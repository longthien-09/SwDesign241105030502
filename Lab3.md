# Lab 3

## Subsystem context diagrams

### Biểu đồ ngữ cảnh của các hệ thống con

#### BankSystem
- Biểu đồ ngữ cảnh của hệ thống con BankSystem:
![alt text] 
![](https://www.planttext.com/api/plantuml/png/l59BJiCm4Dtx52El0FK3swYAgbAGs22adi1nfX3LiIFFM10XJiQ28t459arQsW9Rl1ZRC-_DUnhxy_rZJcmYfzefsbGUOY1KrXaYU31j3CvT1y_TZX5cCxk_vFch0bdJQHE3HIA1r-XPlQc1VxSmVhDgYR4MPkKPuzfOt161e_6qndYRV4bdnjgGFD-dki2OmOfZvHz7OEekcy4ofCBXg2SPorNmIyCe1Odd6In2S6Zyj_gHEAM2-hEOVMdp7Fx5mqtTkD0Y3gCH8n8hxlK5zNF2ut5-DBSCT28ahGwJ7UWOinskE29uhlX9_z7ur4xNl2d5k_G_hNNueSk13C7ms5X2qUvr1eI-qbkUlfnCBlHlSZks2CxHbzsl-m800F__0m00)
- Giải thích biểu đồ:

   - PayrollController (control): Là lớp điều khiển xử lý các thao tác liên quan đến việc tính toán và thực hiện trả lương. Lớp này có phương thức runPayroll().
   - IBankSystem (interface): Giao diện mà các hệ thống ngân hàng cần triển khai để thực hiện các thao tác liên quan đến việc gửi tiền (direct deposit). Phương thức deposit() trong giao diện này sẽ thực hiện việc chuyển tiền vào tài khoản ngân hàng.
   - BankSystem (subsystem proxy): Là hệ thống ngân hàng, thực hiện các thao tác gửi tiền trực tiếp vào tài khoản ngân hàng. Nó có phương thức deposit() để gửi tiền từ Paycheck vào tài khoản được mô tả bởi BankInformation.
   - Paycheck (entity): Là đối tượng đại diện cho phiếu lương hoặc số tiền được trả cho nhân viên.
   - BankInformation: Lưu trữ thông tin ngân hàng cần thiết để thực hiện các giao dịch, chẳng hạn như thông tin tài khoản.

- Mô tả:
Interface (IBankSystem):

          interface IBankSystem {
          // Thực hiện chuyển tiền lương vào tài khoản ngân hàng
          void deposit(Paycheck aPaycheck, BankInformation intoBank);
          }

  Hệ thống con (BankSystem):

    - Chức năng chính:

     Xử lý giao dịch chuyển lương
  
    - Thành phần:
      
    Transaction Processing: Xử lý giao dịch chuyển tiền
  
    Account Verification: Xác thực thông tin tài khoản
  
    Transaction Logging: Ghi log giao dịch
  
    - Đặc điểm:
      
    Đảm bảo tính bảo mật trong giao dịch
  
    Xác thực thông tin tài khoản trước khi chuyển
  
    Ghi nhận log đầy đủ cho mỗi giao dịch
  
    Hỗ trợ nhiều loại tài khoản ngân hàng khác nhau

- Các thành phần chính trong biểu đồ:

  - PayrollController: Điều khiển quá trình tính và chuyển lương
  - IBankSystem: Interface định nghĩa phương thức giao tiếp với ngân hàng
  - BankSystem: Triển khai thực tế việc tương tác với hệ thống ngân hàng
  - Paycheck: Thông tin chi tiết về séc lương
  - BankInformation: Thông tin tài khoản ngân hàng
- Thuộc tính:
  - PayrollController (control):/-strong/-heart:>:o:-((:-h - payrollData: Lưu trữ dữ liệu trả lương cần thiết cho việc tính toán và thực hiện trả lương. Thuộc tính này có thể chứa thông tin về các phiếu lương hoặc dữ liệu trả lương cho từng nhân viên.
  - IBankSystem (interface):
    - IBankSystem là một giao diện, do đó nó chỉ có phương thức mà không có thuộc tính. Giao diện này quy định các hành động mà hệ thống ngân hàng cần thực hiện.
  - BankSystem (subsystem proxy):
    - bankAPIKey: Chứa một khóa API để tương tác với các dịch vụ ngân hàng bên ngoài (nếu có), có thể được sử dụng để xác thực khi gửi yêu cầu đến ngân hàng.
  - Paycheck (entity):
    - amount: Số tiền của phiếu lương.
    - employeeId: ID của nhân viên mà phiếu lương này được phát cho.
    - payDate: Ngày trả lương cho nhân viên.
  - BankInformation:
    - accountNumber: Số tài khoản ngân hàng của nhân viên nhận lương.
    - routingNumber: Số mã định tuyến ngân hàng (dùng để xác định ngân hàng).
    - bankName: Tên ngân hàng nơi nhân viên có tài khoản.
      
- Mối quan hệ của các thuộc tính:
  - PayrollController có thể tương tác với IBankSystem (dạng quan hệ tùy chọn "0..1" có nghĩa là một đối tượng PayrollController có thể hoặc không có liên kết với một đối tượng IBankSystem).
  - IBankSystem là giao diện mà BankSystem triển khai, và thông qua đó, BankSystem thực hiện việc gửi tiền vào tài khoản của người lao động (liên kết với Paycheck và BankInformation).
  - Các mối quan hệ giữa các lớp cho thấy cách BankSystem và IBankSystem phối hợp để xử lý các giao dịch gửi tiền từ Paycheck vào tài khoản BankInformation.

 #### PrintService
- Biểu đồ ngữ cảnh của hệ thống con PrintService:
![alt text]()


- Giải thích biểu đồ:
  - PrintService (control): Là lớp điều khiển xử lý các thao tác liên quan đến việc gửi yêu cầu in tài liệu. Lớp này có các phương thức để thực hiện các thao tác như in tài liệu, kiểm tra trạng thái máy in và quản lý hàng đợi công việc in./-strong/-heart:>:o:-((:-h - Phương thức chính: printPaycheck(), getPrinterStatus(), getPrinterQueue()
  - IPrintService (interface): Giao diện mà các hệ thống in cần triển khai để thực hiện các thao tác liên quan đến việc in tài liệu. Các phương thức trong giao diện này sẽ cho phép gửi tài liệu đến máy in, kiểm tra trạng thái máy in và xem hàng đợi in hiện tại.
    - Phương thức:
      - print(document: Document): In một tài liệu.
      - getPrinterStatus(): Kiểm tra trạng thái của máy in (sẵn sàng hay có lỗi).
      - getPrinterQueue(): Kiểm tra và trả về hàng đợi in.
  - PrintService (subsystem proxy): Là hệ thống con thực hiện các thao tác in tài liệu thực tế. Nó triển khai giao diện IPrintService và thực hiện việc in tài liệu qua các máy in thực tế, đồng thời theo dõi trạng thái máy in và hàng đợi in.
    - Phương thức:
      - print(document: Document): Thực hiện việc in tài liệu qua máy in.
      - getPrinterStatus(): Kiểm tra và trả về trạng thái của máy in.
      - getPrinterQueue(): Kiểm tra và trả về hàng đợi in.
  - Document (entity): Là đối tượng đại diện cho tài liệu cần in. Mỗi tài liệu có thể chứa thông tin về nội dung, định dạng và kích thước.
    - Thuộc tính:
      - documentId: Mã định danh của tài liệu.
      - content: Nội dung của tài liệu cần in.
      - format: Định dạng của tài liệu (ví dụ: PDF, DOCX).
      - createdDate: Ngày tạo tài liệu.
      - size: Kích thước của tài liệu.
  - Status: Lưu trữ trạng thái của máy in, có thể bao gồm các thông tin về tình trạng sẵn sàng của máy in, mức giấy, mức mực, và các lỗi có thể xảy ra.
    - Thuộc tính:
      - isReady: Trạng thái của máy in, xác định xem máy có sẵn sàng để in không.
      - errorMessage: Thông điệp lỗi nếu máy in gặp vấn đề.
      - paperLevel: Mức độ giấy còn lại trong máy in.
      - tonerLevel: Mức độ mực còn lại trong máy in.
  - Queue: Quản lý hàng đợi các công việc in. Các tài liệu được thêm vào hàng đợi và sẽ được in theo thứ tự trong hàng đợi.
    - Thuộc tính:
      - pendingJobs: Danh sách các tài liệu đang chờ được in.
    - Phương thức:
      - addJob(document: Document): Thêm tài liệu vào hàng đợi.
      - removeJob(documentId: int): Loại bỏ tài liệu khỏi hàng đợi.
      - getQueueLength(): Trả về số lượng tài liệu còn lại trong hàng đợi.
      - clearQueue(): Xóa tất cả các công việc trong hàng đợi.
2. Analysis class to design element map
Hệ thống con BankSystem
Các lớp phân tích:

PayrollController (Lớp điều khiển)
IBankSystem (Giao diện)
BankSystem (Proxy hệ thống con)
Tiền lương (Thực thể)
BankInformation (Thực thể)
Các yếu tố thiết kế:

Người kiểm soát tiền lương:

Yếu tố thiết kế: Lớp điều khiển
Sẽ được triển khai như một lớp điều khiển trong giai đoạn thiết kế. Nó sẽ quản lý các tương tác giữa giao diện người dùng và BankSystem.
Mẫu thiết kế mẫu: Mẫu Facade để đơn giản hóa tương tác với BankSystem.
Phương pháp thực hiện: runPayroll()quản lý quy trình tính lương.
Hệ thống IBank:

Yếu tố thiết kế: Giao diện
Điều này sẽ được chuyển thành giao diện trong thiết kế, xác định hợp đồng để tương tác với các triển khai BankSystem khác nhau.
Phương pháp thực hiện:deposit(Paycheck, BankInformation)
Hệ thống ngân hàng:

Phần tử thiết kế: Lớp hệ thống con (Proxy)
Lớp này hoạt động như một proxy cho BankSystem thực tế, xử lý tương tác cấp thấp với các API hoặc dịch vụ ngân hàng bên ngoài.
Phương pháp thực hiện: deposit(), verifyAccount(),logTransaction()
Mẫu thiết kế mẫu: Mẫu proxy để cung cấp cổng truy cập vào BankSystem.
Tiền lương:

Yếu tố thiết kế: Lớp thực thể
Nó sẽ được biểu diễn như một đối tượng đơn giản lưu trữ thông tin về tiền lương, bao gồm các thuộc tính như số tiền, ID nhân viên và ngày trả lương.
Mẫu thiết kế mẫu: Đối tượng truyền dữ liệu (DTO) để truyền dữ liệu tiền lương giữa các lớp.
Thông tin ngân hàng:

Yếu tố thiết kế: Lớp thực thể
Sẽ được triển khai như một lớp lưu trữ thông tin tài khoản ngân hàng cần thiết để xử lý giao dịch.
Mẫu thiết kế mẫu: Đối tượng giá trị để biểu diễn dữ liệu không thay đổi.
Hệ thống con PrintService
Các lớp phân tích:

PrintService (Lớp điều khiển)
IPrintService (Giao diện)
PrintService (Proxy hệ thống con)
Tài liệu (Thực thể)
Trạng thái (Thực thể)
Hàng đợi (Thực thể)
