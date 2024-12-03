## Phân tích và thiết kế ca sử dụng
### 1. Login:

Mô tả ca sử dụng:
- Actor: Employee, PayrollAdministrator

- Mục đích: Xác thực người dùng để truy cập hệ thống.

Luồng chính

- Người dùng mở giao diện đăng nhập.

- Người dùng nhập tên đăng nhập và mật khẩu.

- Hệ thống gửi thông tin đăng nhập đến SecuritySubsystem để xác thực.

- Nếu thông tin hợp lệ:

    + Hệ thống cấp quyền truy cập và chuyển đến giao diện chính.

- Nếu thông tin không hợp lệ:
    
    + Hệ thống hiển thị thông báo lỗi.

Các lớp tham gia

- Boundary Class: LoginForm

- Control Class: LoginController

- Entity Class: User, SecuritySubsystem
  
Biểu đồ tuần tự
![](https://www.planttext.com/api/plantuml/png/Z98xJiGm48Pxds8km0LIe4Kh0HAFPg6WJ1mhjfJOu8T4wYqegBQYX0WX9AGKI5HEiOLp4P-0A-1aWTsm4U32ch7-__FCsE_DSg9qBBKfSXHZBIISAo8XLh3NPIWHXgUnBE5OP8pl2raWBBYM8b-TJ5T9JYGYN3DTzlwlU4QmaI6OcKILIfC2eHuBExjhO0Gdlhc7ZCK2KkQR6mxjeftp33Zrjhv4tyhErliZE0p2EGTDVNExQHtbd_QS87PlWQhPhnVyQ2k20z_Kx0_pMjyXjjgEuCAz6C3UFXkuTXNk2t_5Q4ivMi6HjqiDLyRRnu4xpZMSKVV0AU2kEWHXZTIpCOefDMK_kNOHe7mmTKnTpIaYkI81w-sJXiJRYlq3EtYEpr4bhXAG--QEXU-GeadOkb_s0G00__y30000)

### 2. Maintain Timecard

Mô tả ca sử dụng

- Actor: Employee

- Mục đích: Nhân viên nhập và lưu giờ làm việc vào hệ thống.

Luồng chính

- Nhân viên mở giao diện nhập thẻ chấm công (TimecardForm).

- Nhân viên điền số giờ làm việc và mã dự án (nếu có).

- Giao diện gửi thông tin đến TimecardController.

- TimecardController lưu thông tin vào Timecard.

- Nếu cần, TimecardController lấy dữ liệu dự án từ ProjectManagementDatabase.

- Hiển thị thông báo thành công.

Các lớp tham gia

- Boundary Class: TimecardForm

- Control Class: TimecardController

- Entity Class: Timecard, ProjectManagementDatabase

Biểu đồ tuần tự
![](https://www.planttext.com/api/plantuml/png/X59DIiGm5Dxd5Ey2Ng0B6V0NTCI56vTf6zf8cenf8dJjmeKh3o3EC8WW32guQXQpA7YFTmAlOCfOsrAhMIMFx-Tzx-NJhIUveThOJ10Q6QLXBvi9LJ16GcLbJ7K1PpnZ4TNnlj8PYPGqMecVuixcBPWcJ1fkMdZpFjNgWaLcIYLDMEQBkzJGaEQCaCOBjhPxBW5CqJr0mgc2cAExaQrg5rVp6eq03ZtoMe99qTrskN_OdAHOhcQGexlp37JtS5ND8QkM4ADxWseX1tx3u04Se5lncl82ehQqP8ZgSWCu_dYrFG8L1iwhPmiHba_MXwZUPGA6oxOJyETttT4HUoCi7ujHkL7YMD8ZBDS6BYsMIx_V-9-Sco7tzlBTILWjL7sVonIYka8cNgx-XLy0003__mC0)

### 3. Run Payroll

Mô tả ca sử dụng

- Actor: PayrollAdministrator

- Mục đích: Xử lý lương cho nhân viên.

Luồng chính

- Quản trị viên khởi chạy chức năng tính lương.

- Hệ thống lấy dữ liệu từ Timecard và EmployeeDatabase.

- PayrollController thực hiện tính toán thông qua Payroll.

- Hệ thống chuyển kết quả tới:

    + BankSystem để thanh toán.

    + PrintService để in phiếu lương.

Các lớp tham gia

- Boundary Class: PayrollUI

- Control Class: PayrollController

- Entity Class: Employee, Timecard, Payroll, BankSystem, PrintService

Biểu đồ tuần tự
![](https://www.planttext.com/api/plantuml/png/V5B1IWCn4BtdA-O7_84zI5Ky53q8NK6FQJOqmUoaPhE5V85dZvwqWWZ5eWTFNQI7IFyZNz1VC8lTReMjEGoPcRmtRsQohfQzmb9ZormHogmsS46TqKeTPRb4MLX3Ov0CTOaPDQx9NlO9qsZZjOcS_BgA6yBHIklWD1yhxJXl_5Jcd56JDVu6sBZ756y6hh0ytpum4ks0cubad90kNN1ms2fAu4o4wb72ztse7d04jwK3Q_mR2h1-7grQVQocE29Ro0w-rP_0jP-LmCBYjUm6jczhWgRF1Cx3uiL15gftK39KToMWyCy84-bds0rkXj85PYA6Sc3-Sr_fJJ21z8zCgYoaWjPzQp_5E0WAEAgL2FyKyn1F9r-xWmIkGZK7vR_0jao4gu937s4iP5Wiost5lOoxEqowa1opVtkhzvgAUWGmz5CDGiSMegPe1Ub5TFrpVm000F__0m00)

## Lý do thiết kế

### 1. Tách biệt trách nhiệm (SRP):
Các lớp được thiết kế theo nguyên lý SRP (Single Responsibility Principle), với các chức năng cụ thể như quản lý giao diện, xử lý điều khiển, và lưu trữ dữ liệu.

### 2. Khả năng mở rộng:
Các lớp Controller có thể được mở rộng thêm các tính năng khác (ví dụ: thêm xác thực hai bước cho LoginController).

### 3. Tính nhất quán:
Hệ thống tuân thủ quy trình chuẩn trong thiết kế, giúp đảm bảo tính nhất quán và dễ dàng bảo trì.
