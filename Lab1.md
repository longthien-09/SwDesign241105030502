
## 1. Phân tích kiến trúc
### 1.1 Đề xuất kiến trúc : Chọn kiến trúc tầng.

- Lớp giao diện(Presentation Layer):Lớp này sẽ chịu trách nhiệm hiển thị dữ liệu và giao tiếp với người dùng.
- Lớp ứng dụng(Application Layer): Lớp này là trung tâm xử lý logic nghiệp vụ của hệ thống, gồm các tác vụ như xử lý bảng lương, duy trì thẻ thời gian và thực hiện tính toán thanh toán.
- Lớp dữ liệu(Data Layer): Lớp này chịu trách nhiệm quản lý lưu trữ và truy xuất dữ liệu từ cơ sở dữ liệu.
  
  1.2 Giải thích lý do lựa chọn:
  
  - Mỗi lớp có một trách nhiệm cụ thể, dễ duy trì và phát triển theo từng chức năng riêng biệt.
  - Lớp Dữ Liệu được cách ly, giảm nguy cơ truy cập trực tiếp từ lớp giao diện, giúp bảo vệ thông tin nhạy cảm như bảng lương và thông tin thanh toán.
  - Mỗi lớp có thể được mở rộng hoặc thay đổi mà không ảnh hưởng nhiều đến các lớp khác, phù hợp cho hệ thống cần phát triển dài hạn.
    
  1.3 Ý nghĩa:
  
    - Lớp giao diện : Cung cấp giao diện để người dùng tương tác với hệ thống.
    - Lớp ứng dụng: Thực hiện các logic nghiệp vụ cốt lõi của hệ thống như xử lý thanh toán, tính toán bảng lương, và duy trì thông tin thẻ thời gian.Tương tác với         lớp dữ liệu để lưu trữ hoặc truy xuất thông tin cần thiết.
    - Lớp dữ liệu: Quản lý các thao tác lưu trữ và truy vấn từ cơ sở dữ liệu, chẳng hạn như thông tin nhân viên, thời gian làm việc, và thông tin thanh toán.
      Đảm bảo dữ liệu được lưu trữ một cách an toàn và tối ưu hóa truy cập dữ liệu khi cần thiết.
      
  1.4 Package:
      ![](https://www.planttext.com/api/plantuml/png/T9112i9034NtEKNelbUG5dGXk2XuWZYDCdGwCoHZeOWdS-6Hl8BEncgjMUQ___F9utQlD96aS-z0E-jHWZ929DFHYR5eX9LzecI3nnsDB0LU05zZ7AdYfeykZCnRdrYEPFX3gzlU-acumXHRn-Yi-PlQq2Z1kJtBO6VEDILQikJzWJJ3FvsmB5UpJ8JlTWi8p1oPU5-1YdsRd_O4003__mC0)
  
## 2. Cơ chế phân tích :
  - Cơ chế xác thực người dùng :Đảm bảo rằng chỉ có những người dùng hợp lệ mới có thể truy cập vào hệ thống. Điều này là cần thiết để bảo vệ thông tin nhạy cảm như bảng lương và dữ liệu cá nhân của nhân viên.
  - Cơ chế phân quyền : Đảm bảo rằng người dùng chỉ có thể thực hiện các thao tác mà họ được phép. Ví dụ, nhân viên chỉ có quyền xem thông tin cá nhân của mình, trong khi quản lý có quyền sửa đổi thông tin nhân viên và duyệt bảng lương.
  - Cơ chế tính toán bảng lương : Tính toán các khoản thanh toán cho nhân viên dựa trên thời gian làm việc, thuế, và các khoản khấu trừ khác. Cơ chế này cần phải chính xác để tránh sai sót có thể gây ra tranh chấp hoặc vấn đề tài chính.
  - Cơ chế lưu trữ và truy xuất dữ liệu:  Quản lý việc lưu trữ và truy xuất thông tin về nhân viên, thời gian làm việc và bảng lương. Điều này rất quan trọng để đảm bảo dữ liệu luôn có sẵn và dễ dàng truy cập khi cần.
  - Cơ chế tạo báo cáo : Cung cấp báo cáo tổng hợp về bảng lương, thời gian làm việc và hiệu suất làm việc của nhân viên. Các báo cáo này giúp quản lý đưa ra quyết định dựa trên dữ liệu.
    
##3.Phân tích ca sử dụng Payment
  - PaymentProcessor: Chịu trách nhiệm xử lý các giao dịch thanh toán.
  - Employee: Đại diện cho nhân viên nhận thanh toán.
  - PayrollDatabase: Lớp chịu trách nhiệm truy cập cơ sở dữ liệu để lưu trữ và truy xuất thông tin thanh toán.
    
  - Biểu Đồ Sequence:

    ![](https://www.planttext.com/api/plantuml/png/Z9513e9034NtFSLSW0kmC2JemXtn1XLACd5cYfrYmjbSU2Il82H0pA3HTVzx_oTztXz5L1JjlODuiS48HpA0jRAOW-yS3qJGZGbRsmw3cWe7Jq4huPfYP4cFmixjKV6CaG0MXSbs6p8t9xhs55Sdf8cPUbTEa8gb6wtpp36q34dEP5yQjPUmHN_NbaAej2X7KStI_DbQScYj-0zmqZlIoxHyJSyqgkK01OLcUjOB003__mC0)
    
  -  Biểu Đồ Lớp :
    
![](https://www.planttext.com/api/plantuml/png/R94zRiCm38LtdKAZ0pGNy11aI8TiGNi2HcO3enBfadG0e-Z9ClH8lKATI7QR7srwfDxtIFsSljTg8DQdwFIz9I-iw5s8eEftC2Gasma7L6NndywVJvVrRLFxLvEM3baUZQpNQwtBRujJ1ObxijflCBG9ufF7r4KU4F-y5kxB5VvpAKxS--Qi4oIyYG8HP9WvMHJyw55jol8FD4h2CMx0O0ywym8JOR2MANjVCmJ72nvnIhcbDwuUp5FFSnHNGJ0iALumi3HLsMWzhVoIxMxzo-NgDkhZfXcuHchEN_iB003__mC0)

- Giải thích:
  - PaymentProcessor: Lớp chính thực hiện việc tính toán số tiền thanh toán cho nhân viên dựa trên các thuộc tính của Employee. Phương thức calculatePayment() lấy thông tin từ Employee, tính toán tổng số tiền thanh toán và sau đó cập nhật vào PayrollDatabase.
  - Employee: Lưu trữ thông tin của nhân viên cần thiết cho tính toán, như mã nhân viên, tên, và mức lương theo giờ.
  -  PayrollDatabase: Quản lý việc truy xuất và lưu trữ thông tin liên quan đến thanh toán. PayrollDatabase cung cấp phương thức để lấy dữ liệu nhân viên và lưu lại kết quả thanh toán.
 
##4. Phân Tích Ca Sử Dụng "Maintain Timecard

###4.1: Xác Định Các Lớp Phân Tích Cho Ca Sử Dụng "Maintain Timecard"
    - TimecardManager: Chịu trách nhiệm quản lý các thao tác liên quan đến ghi và duy trì thời gian làm việc.
    - Timecard: Lớp lưu trữ thông tin về thời gian làm việc, bao gồm ngày làm việc và số giờ làm.
    - PayrollDatabase: Lớp chịu trách nhiệm truy cập cơ sở dữ liệu để lưu trữ và truy xuất thông tin thời gian làm việc.
    
###4.2 Biểu đổ Sequence:

![](https://www.planttext.com/api/plantuml/png/R51B2i903DtFANA1uhuBAUXM4DG3n4wKmVcHIGNFvi8ZUGMdCjQskah8-vBd_T4aGPREMPKknWE7HA1YFfdMHFG2U-EeHTORz7Wc_ejDZbkySR1sZO97JAJKp06gvI2iOSM4Gej3r7by3JzBJvuPrh33wuWwWw4Q-PV871FyoR1xItyBJHeDqQLJaQAOu5L3NlVFUW400F__0m00)

###4.3 Biểu đồ lớp:

![](https://www.planttext.com/api/plantuml/png/N95D2i8m48NtEKMM2lO2NOWBDou4GS7rc0mQcfyoIOKYdio5H_8AferDRGC9cPUPDr-Ip-kzyG4eD4OpNodBoNbaGeFt_AGC2Y2v1mjN9FvWl1icXJjPycCWPQ-3h6o8SwXQt5n3lkHR5Cg0Nd490MCOroLxibcFmHnDhLsBE7SVYrFScvyTLIXpYtGY26DMfbWcjQdblpfb--CvG4jEwzW8Bk1nm1BEMXH1EPkWfd0UxgDr-6tAVBVUVlwOHR7E2VcmLsS8R8DMTj_p1G00__y30000)

###4.4 Giải Thích:
  - TimecardManager: Quản lý việc tạo và cập nhật timecard, với các thuộc tính và phương thức liên quan đến việc duy trì thông tin thời gian làm việc.
  - Timecard: Lưu trữ các thuộc tính liên quan đến thời gian làm việc của nhân viên.
  - PayrollDatabase: Quản lý truy cập đến cơ sở dữ liệu, cung cấp phương thức để lưu trữ timecard.

##5.Hợp nhất kết quả phân tích:

- Kiến trúc hệ thống

Hệ thống "Payroll System" được thiết kế với cấu trúc kiến trúc theo mô hình 3 lớp (Three-tier Architecture), bao gồm:
Presentation Layer (Lớp giao diện): Chịu trách nhiệm tương tác với người dùng qua các lớp như PaymentUI và TimecardUI.
Business Logic Layer (Lớp logic nghiệp vụ): Chứa các lớp điều khiển như PaymentController và TimecardController để xử lý các nghiệp vụ thanh toán và quản lý bảng chấm công.
Data Layer (Lớp dữ liệu): Lưu trữ và quản lý dữ liệu trong các lớp thực thể như Payment, Order, và Timecard.
