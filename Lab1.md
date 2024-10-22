# Lab1
## 1. Phân tích kiến trúc
### 1.1 Đề xuất kiến trúc
- Lớp Data Access: Giao tiếp với CSDL, kết nối với SQL Server (dữ liệu về nhân viên, lương, timecard) và DB2 cho dữ liệu dự án.
- Lớp Presentation (UI): Ứng dụng desktop dựa trên nền tảng Windows, sử dụng WPF hoặc WinForms.
### 1.2. Giải thích lý do lựa chọn kiến trúc
- Đa lớp giúp phân tách rõ ràng giữa giao diện, logic nghiệp vụ, và dữ liệu.
- Windows desktop phù hợp với yêu cầu là hệ thống chạy trên máy tính cá nhân của nhân viên.
### 1.3. Biểu đồ kiến trúc (Package Diagram)
## 2. Cơ chế phân tích
### 2.1. Cơ chế tính toán lương tự động
- Cơ chế xử lý hàng tuần và hàng tháng dựa trên hệ thống clock nội bộ.
- Cơ chế xử lý lương theo loại nhân viên: tính lương theo giờ, lương cố định, và hoa hồng.
### 2.2. Cơ chế bảo mật và phân quyền
- Role-based access control (RBAC): phân quyền giữa nhân viên và quản trị viên.
- Authentication với JWT: đảm bảo an toàn trong quá trình truy cập và thao tác dữ liệu.
### 2.3. Cơ chế xử lý thông tin thanh toán
- Tích hợp với hệ thống ngân hàng cho việc direct deposit.
- Quản lý các phương thức thanh toán: mail, pick-up, direct deposit.
## 3. Phân tích ca sử dụng Payment
### 3.1. Lớp phân tích cho Payment
- PaymentController: quản lý yêu cầu từ UI.
- PaymentService: xử lý logic về phương thức thanh toán.
- EmployeeRepository: truy vấn thông tin nhân viên từ CSDL.
