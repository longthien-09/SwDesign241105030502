## I. Phân tích các ca sử dụng trong hê thống Payment System.

### 1. Add Employee (Thêm Nhân Viên)

* Mô Tả Chi Tiết: Ca sử dụng này cho phép người quản lý hoặc hệ thống thêm một nhân viên mới vào cơ sở dữ liệu của hệ thống. Mỗi nhân viên mới sẽ được thêm vào với các thông tin cơ bản như:
- ID: Mã định danh duy nhất cho mỗi nhân viên.
- Tên: Họ tên nhân viên.
- Mức Lương: Mức lương của nhân viên (có thể cố định, theo giờ hoặc hoa hồng).
- Phương Thức Thanh Toán: Cách thức nhận lương (chuyển khoản hoặc tiền mặt).
- Loại Nhân Viên: Nhân viên có thể thuộc một trong ba loại chính:
- Nhân viên lương cố định.
- Nhân viên tính lương theo giờ làm việc.
Nhân viên nhận hoa hồng dựa trên doanh thu.
Yêu Cầu Kỹ Thuật:

Lớp EmployeeManager: Chịu trách nhiệm thực hiện việc thêm nhân viên mới. Lớp này sẽ tạo một đối tượng Employee với các thông tin cần thiết và lưu thông tin đó vào PayrollDatabase.
Lớp Employee: Đại diện cho một nhân viên, bao gồm các thuộc tính như ID, tên, mức lương, phương thức thanh toán và loại nhân viên.
Lớp PayrollDatabase: Lưu trữ tất cả thông tin nhân viên trong hệ thống.
Lợi Ích:

Tăng cường tính linh hoạt của hệ thống trong việc thêm các nhân viên mới mà không cần can thiệp trực tiếp vào cơ sở dữ liệu.
Cung cấp cơ sở dữ liệu nhân viên đầy đủ, phục vụ cho các ca sử dụng khác như tính lương, quản lý timecard và quản lý doanh thu.- Mô tả: Ca sử dụng này cho phép người quản lý hoặc hệ thống thêm nhân viên mới vào hệ thống payroll. Một nhân viên mới sẽ bao gồm các thông tin như ID, tên, mức lương, phương thức thanh toán và loại nhân viên (lương cố định, tính theo giờ, hoặc tính hoa hồng).
- Yêu cầu: Lớp EmployeeManager có thể chịu trách nhiệm tạo đối tượng Employee và lưu thông tin vào PayrollDatabase.
### 2. Delete Employee (Xóa Nhân Viên)

Mô Tả Chi Tiết: Ca sử dụng này cho phép người quản lý hoặc hệ thống xóa thông tin của một nhân viên khỏi cơ sở dữ liệu. Để xóa một nhân viên, chỉ cần cung cấp ID của nhân viên đó. Việc xóa nhân viên đảm bảo hệ thống được cập nhật và không lưu trữ thông tin của các nhân viên không còn làm việc.

Yêu Cầu Kỹ Thuật:

Phương thức deleteEmployee trong lớp EmployeeManager: Chịu trách nhiệm tìm nhân viên dựa trên ID và xóa khỏi cơ sở dữ liệu.
Lớp PayrollDatabase: Thực hiện việc lưu trữ và xóa thông tin nhân viên, đảm bảo dữ liệu luôn nhất quán.
Lợi Ích:

Giảm bớt khối lượng dữ liệu không cần thiết.
Cải thiện hiệu suất và khả năng quản lý hệ thống.
### 3. Record Sales Receipt (Ghi Nhận Doanh Thu)

Mô Tả Chi Tiết: Ca sử dụng này áp dụng cho các nhân viên hưởng lương theo hoa hồng. Khi nhân viên có một giao dịch bán hàng, hệ thống ghi nhận doanh thu từ giao dịch này để tính toán hoa hồng. Mỗi giao dịch sẽ bao gồm:

Ngày Bán Hàng: Thời điểm giao dịch diễn ra.
Giá Trị Doanh Thu: Số tiền thu được từ giao dịch.
Yêu Cầu Kỹ Thuật:

Lớp SalesReceipt: Đại diện cho một giao dịch bán hàng, lưu trữ thông tin về ngày và số tiền doanh thu.
Lớp SalesManager: Quản lý việc lưu trữ các giao dịch cho từng nhân viên.
Lớp PayrollDatabase: Lưu trữ dữ liệu về doanh thu, liên kết từng giao dịch với nhân viên tương ứng.
Lợi Ích:

Đảm bảo nhân viên nhận đúng khoản hoa hồng.
Tạo cơ sở cho hệ thống tính toán chính xác lương và thưởng cho các nhân viên làm việc theo cơ chế hoa hồng.
### 4. Select Payment Method (Chọn Phương Thức Thanh Toán)

Mô Tả Chi Tiết: Ca sử dụng này cho phép nhân viên tự chọn hoặc thay đổi phương thức nhận lương của mình. Các phương thức thanh toán bao gồm:

Chuyển Khoản Ngân Hàng: Lương được gửi vào tài khoản ngân hàng của nhân viên.
Séc: Nhân viên nhận lương qua séc.
Tiền Mặt: Lương được thanh toán trực tiếp bằng tiền mặt.
Yêu Cầu Kỹ Thuật:

Thuộc tính paymentMethod trong lớp Employee: Lưu trữ phương thức thanh toán đã chọn.
Phương thức selectPaymentMethod trong EmployeeManager: Cập nhật thông tin thanh toán trong PayrollDatabase dựa trên yêu cầu của nhân viên.
Lợi Ích:

Cho phép nhân viên có sự linh hoạt trong cách nhận lương.
Hệ thống có thể quản lý hiệu quả các phương thức thanh toán đa dạng mà không ảnh hưởng đến quy trình tính lương.
### 5. Calculate Payroll (Tính Lương)

Mô Tả Chi Tiết: Đây là ca sử dụng quan trọng trong Payroll System, tính toán lương của từng nhân viên dựa trên thông tin làm việc và loại hình lương. Ca sử dụng này sẽ tính toán và lưu kết quả lương vào cơ sở dữ liệu, đồng thời chuẩn bị dữ liệu cho các phương thức thanh toán đã chọn. Hệ thống sẽ tính lương theo:

Lương Cố Định: Nhân viên nhận lương cố định hàng tháng.
Lương Theo Giờ: Nhân viên được trả lương dựa trên số giờ làm việc thực tế.
Lương Hoa Hồng: Nhân viên nhận lương cơ bản cộng với hoa hồng từ các giao dịch bán hàng.
Yêu Cầu Kỹ Thuật:

Lớp PayrollCalculator: Áp dụng các công thức tính toán lương, phân biệt các loại nhân viên và áp dụng công thức phù hợp.
Lớp PayrollDatabase: Lưu trữ kết quả lương đã tính toán để xử lý thanh toán.
Lớp Employee: Có thể chứa các thuộc tính liên quan đến tính lương, như số giờ làm việc hoặc doanh thu để tính hoa hồng.
Lợi Ích:

Đảm bảo nhân viên nhận đúng lương, khuyến khích sự trung thực trong báo cáo thời gian và doanh thu.
Giảm thiểu lỗi trong quy trình tính toán lương nhờ vào hệ thống tự động.

### 6. 
