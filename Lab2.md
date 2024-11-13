## I. Phân tích các ca sử dụng trong hê thống Payment System.
  ### 1. Phân tích ca sử dụng Create Administrative Report.

    Các lớp phân tích và nhiệm vụ cho ca sử dụng Create Administrative Report:
     - PayrollAdministrator: Xác định loại báo cáo, cung cấp thông tin cần thiết, yêu cầu lưu báo cáo.
     - Report: Chứa thông tin báo cáo và cung cấp các phương thức để tạo và lưu báo cáo.
     - ReportCriteria: Lưu trữ và kiểm tra các thông tin tiêu chí báo cáo.
     - System: Nhận yêu cầu từ Payroll Administrator, xác thực và tạo báo cáo, yêu cầu lưu trữ hoặc huỷ báo cáo.
     - ErrorHandler: Hiển thị thông báo lỗi nếu có thông tin thiếu hoặc không hợp lệ và yêu cầu nhập lại.
Biểu đồ tuần tự:

![](https://www.planttext.com/api/plantuml/png/b9DDJiD038NtEOMN81MnPu6A2e9bHKzWPKnbQNw2xKIQix7WI5o1YPA8158ekypCUr-UNoOVR-zRDHHhWw-mjYImnop9-piNEBAQODciA1fRXaDMep2jdgb9OilLJjX86AVT1v4aJnYT9wcgDJPStOvSk2cGrvRKe1P28v3X3UDn4Qu2lco3lhY7471XkQ4DkCBI3L1eVCf4436GNlwTPY-fOqVViRCyow6BPJSFVjfHb8yKIMP3ZWU_3Mcjn4b-TfMMGB7xVvTzIL0-7FXKet6A4-dytduWrdeuh8QRtviY6fuWi2h7upN73ZqxuFYI90peXUFqUFUiZSSCrCkXt0F58rLRYgx_1Ju1003__mC0)

Thuộc tính của các lớp:
- PayrollAdministrator:
  + username: Tên đăng nhập của người quản trị.
  + password: Mật khẩu để đăng nhập hệ thống.
- Report:
  + reportType: Loại báo cáo (Tổng giờ làm việc hoặc lương năm đến nay).
  + startDate: Ngày bắt đầu của báo cáo.
  + endDate: Ngày kết thúc của báo cáo.
  + employeeNames: Danh sách tên nhân viên.
- ReportCriteria:
  + reportType: Loại báo cáo.
  + startDate: Ngày bắt đầu.
  + endDate: Ngày kết thúc.
  + employeeNames: Danh sách tên nhân viên.
- System:
  + generateReport(criteria: ReportCriteria): Phương thức tạo báo cáo từ các tiêu chí.
  + saveReport(report: Report, location: String): Phương thức lưu báo cáo.
- ErrorHandler:
  + displayError(message: String): Phương thức hiển thị thông báo lỗi.
  + requestInput(): Phương thức yêu cầu người dùng nhập lại thông tin.

Biểu đồ lớp:

![](https://www.planttext.com/api/plantuml/png/l5BBJiCm4BpdArOvjOXMwjL2g0YGG488KNx0YfTWoR7DhXCK8RwC0v_4B-0uIQ4XNBdaCPcPzKpsy_rZoq5Ig2kJ5KOomvrioHbpfYfjDGUImH6yPW0hg1d9oWe5x09fMoRGHz6B8xK7txB1QTTom2ff0Kgq6Btm7hsZi2X81oGj1VJ0-V2-J6IMpKYaT1jfns1S8ODsTXpN2mYVQ-HmRH_TOYcWSLfzdwEN3XbwluVM7wP89Lp4ymdehWb3gwP8vOrh4MzZ2IpW9lPpqfkSJiUDWVvjx2MHeojfbK4QEbUQlP5j-hA8KfOb_j6RhyFFucQN8D_ai5f1VfHFCmhmv1gjaBFXfu_SpNgzfqVQk0M_UJEUSTtcU0T11Job9mRiOCwsiRvkcRy0003__mC0)

### 2. Phân tích ca sử dụng Create Employee Report

   Các lớp phân tích và nhiệm vụ cho ca sử dụng Create Employee Report:
   - Employee: Cung cấp các thông tin đầu vào cho báo cáo (loại báo cáo, ngày, số dự án) và yêu cầu lưu báo cáo.
   - System: Yêu cầu thông tin từ nhân viên, tạo và lưu báo cáo.
   - ReportCriteria: Lưu trữ các thông tin tiêu chí báo cáo và kiểm tra tính hợp lệ.
   - Report: Tạo nội dung báo cáo và cung cấp báo cáo cho nhân viên.
   - ErrorHandler: Xử lý các lỗi và yêu cầu người dùng nhập lại thông tin nếu cần thiết.

Biểu đồ tuần tự:
![](https://www.planttext.com/api/plantuml/png/Z5IxJiH03Epp5HOLI8VeAT191-8ea127e3Q9xrZOH_0waV9j57mIlu3puf8G7ccowundxHblFjxUbr6GfN0smLG2muNBRQY84l9Yf89D5OLSlxkbFB2is0YnmN6qtrqm1rwZponnalHyS7pMSS6f9hmM50KaGCg4Gi0jHOTGx5VU7jrYDACxVPRwXaDfCfg2uL2gd1RGT0kP7ha0ybctIf-GTmI-S8_4HmbQWOEx86XX7GgEy13uXJBOgZvOd_1CgHn09AjloXBGPr_ve4jXGoMDwIDiERYU1QxHuuwSQWVdAFY8aIPy0oNEJSmjLbD2rLhxRKLgYpB1Doop4cqQo9X4pSi6wezzrfnLQzF4_mbiBl4UhQb5tjjMgtlbopg-3zR5VcSRZjAWVQh3u2X6bQxjSmYSdnxZyq9-5gMV6sTYD7vtCgblJXxDkYHFF9ZVxiEq0YdOzv2_BaJ4yd_NmQEZndeRKgmTR-PJqxNyt-_6jyovrZRpTOmTQLUj8H7CLbchPAbYrJ-KJm000F__0m00)

* Employee
  - Thuộc tính:
    + employeeID: Mã nhân viên 
    + name: Tên nhân viên 
  - Phương thức:
    + requestReport(): Phương thức yêu cầu hệ thống tạo báo cáo.
    + provideCriteria(reportType, startDate, endDate, chargeNumber): Cung cấp thông tin tiêu chí để tạo báo cáo (bao gồm loại báo cáo, ngày bắt đầu, ngày kết thúc và mã số dự án nếu có).
* Lớp System
  - Phương thức:
    + requestReportCriteria(): Yêu cầu nhân viên cung cấp các tiêu chí báo cáo.
    + retrieveChargeNumbers(): Lấy thông tin số dự án (charge numbers) từ cơ sở dữ liệu quản lý dự án nếu báo cáo loại "Total Hours Worked for a Project" được chọn.
    + generateReport(criteria: ReportCriteria): Tạo báo cáo dựa trên các tiêu chí đã cung cấp.
    + saveReport(report: Report, location: String): Lưu báo cáo vào vị trí được chỉ định.
    + displayError(message: String): Hiển thị lỗi khi thiếu thông tin.
* Lớp ReportCriteria
  - Thuộc tính:
    + reportType: Loại báo cáo.
    + startDate: Ngày bắt đầu của báo cáo.
    + endDate: Ngày kết thúc của báo cáo.
    + chargeNumber: Mã số dự án (kiểu String, chỉ có khi chọn báo cáo "Total Hours Worked for a Project").
  - Phương thức:
    + validate(): Kiểm tra tính hợp lệ của các tiêu chí báo cáo (ví dụ, kiểm tra định dạng ngày, đảm bảo rằng thông tin đầy đủ).
* Lớp Report
  - Thuộc tính:
    + reportType: Loại báo cáo.
    + content: Nội dung báo cáo.
    + generatedDate: Ngày tạo báo cáo.
  - Phương thức:
    + generate(): Tạo nội dung báo cáo từ các tiêu chí đã cung cấp.
* Lớp ErrorHandler
  - Phương thức:
    + displayError(message: String): Hiển thị thông báo lỗi nếu có thiếu sót thông tin hoặc lỗi khác.
    + requestInput(): Yêu cầu người dùng nhập lại thông tin bị thiếu.

Biểu đồ lớp:

![](https://www.planttext.com/api/plantuml/png/Z5HHQiCm3FtFAKI_KcWl44Ofj8KLnZxQNS1DH6Tmx4ns0c7iPFlOaNQ5sQwJnMuxzXCIwUdfwKda-_DhhGqZqzOYAmNJ6dPr8rIF2EyPm18mVEwt1HmDSNdsOSbgd0G02DzQrEQ0ZIAJpmle5AzyfY7LyGetn0qIPpbvo4lVZ0GBy1gspDYGUou0PJNzB5yPdV6vhKz8GzNGuoCBoe-zDbXxtOcUiVTK5w6bmGut4sxj44zScuTBZvL7db4YMHrXk3Am5H2ppuU0BzAi6mek4m_P1GXLCiELJ2TnPHNNZM3zZaXHNgFMx8nt9uxxXurT--l3YSMNvKvTzf5RHdjT7HEyiYXdq4afWKocElxkNoffK9eeDXWRg_WrFB-QsFloo6GbaCAc_-FOv2BsicdDb7Wy-ELoDTnG0RFae6VtSEbvMsH8Eboo8Oil2VraDs0kdToQXOMSWuqIBF20fYKPt8x88eyiCZ9e_YSqzYZgVJr9XOqz80rAphArVNF_a1y0003__mC0)

3. Phân tích ca sử dụng Maintain Employee Information:

  Các lớp phân tích và nhiệm vụ cho ca sử dụng Maintain Employee Information:
    - PayrollAdministrator: Người quản trị thực hiện các thao tác thêm, sửa, hoặc xóa nhân viên.
    - System: Hệ thống xử lý yêu cầu từ người quản trị.
    - Employee: Lớp nhân viên lưu trữ thông tin nhân viên trong hệ thống.
    - ErrorHandler: Lớp xử lý lỗi nếu có sự cố xảy ra (ví dụ: ID nhân viên không hợp lệ).

Biểu đồ tuần tự:

![](https://www.planttext.com/api/plantuml/png/t5H1JiCm4Bpx5JwIGp_00RKI8793GZp0YhUH9NiTrfjAUHi7diGNSDmaE2LfLGuSoC6AxPtnpjYxd-yVsy2Ak7LMg8ezoMVLaRTsfvr14vXKN1I0RBYJBrrWSEFimJNMTm3JdCZJaq9jWOHOuf6RpTr08cybmLiBWHzRhDXul2d4iDL7BSANC49PbZkjlzEHyRjyUaF-O3ICg1BtdfnAf32i5OagIseCZl2AGF64NeUiwAW1WJA2KaSfWFeevxNHSUzQHV4QW392c7xF2Qc1Smz-eARGsLdQXCQgReOi_iRvDfcpc7DcuJrO-ByMLXxtXbmIUIo3zUnqSc9wgPb7gM1bgbY3zIyjCdXGrkZh73e1dJUept91OTPjJeCTXA3guHND0Y-tbXARbWUNjd7eE-CN0000__y30000)

* PayrollAdministrator
  - Thuộc tính:
    + username: Tên đăng nhập của người quản trị.
    + password: Mật khẩu của người quản trị.
  - Phương thức:
    + requestFunction(): Yêu cầu hệ thống thực hiện một chức năng (thêm, sửa, xóa nhân viên).
    + provideEmployeeInformation(employee: Employee): Cung cấp thông tin nhân viên khi thêm mới hoặc cập nhật.
    + enterEmployeeId(employeeId: String): Nhập ID nhân viên để thực hiện thao tác sửa hoặc xóa.
    + confirmDeletion(): Xác nhận việc xóa nhân viên khỏi hệ thống.
* System
  - Thuộc tính:
    + Không có thuộc tính cụ thể (hệ thống là đối tượng xử lý các yêu cầu từ người quản trị).
  - Phương thức:
    + requestFunction(): Yêu cầu người quản trị chọn thao tác (thêm, sửa, xóa nhân viên).
    + getEmployeeInfo(employeeId: String): Truy vấn thông tin của nhân viên từ hệ thống theo ID.
    + addEmployee(employee: Employee): Thêm nhân viên mới vào hệ thống.
    + updateEmployee(employee: Employee): Cập nhật thông tin nhân viên trong hệ thống.
    + deleteEmployee(employeeId: String): Xóa nhân viên khỏi hệ thống.
    + displayError(message: String): Hiển thị thông báo lỗi nếu có sự cố xảy ra.
    + confirmDeletion(): Xác nhận việc xóa nhân viên từ hệ thống.
* Employee
  - Thuộc tính:
    + employeeId: ID nhân viên (sẽ được tạo tự động khi thêm nhân viên).
    + name: Tên nhân viên.
    + employeeType: Loại nhân viên (theo giờ, theo lương, hoặc hoa hồng).
    + mailingAddress: Địa chỉ nhân viên.
    + ssn: Số an sinh xã hội.
    + taxDeductions: Các khoản khấu trừ thuế.
    + otherDeductions: Các khoản khấu trừ khác như bảo hiểm y tế, 401k.
    + phoneNumber: Số điện thoại của nhân viên.
    + hourlyRate: Mức lương theo giờ (nếu là nhân viên theo giờ).
    + salary: Mức lương cố định (nếu là nhân viên theo lương).
    + commissionRate: Mức hoa hồng (nếu là nhân viên theo hoa hồng).
    + hourLimit: Giới hạn giờ làm của nhân viên (nếu có).
  - Phương thức:
    + createEmployee(): Tạo một nhân viên mới trong hệ thống với thông tin đã nhập.
    + updateEmployeeInfo(employee: Employee): Cập nhật thông tin nhân viên trong hệ thống.
    + displayEmployeeInfo(): Hiển thị thông tin của nhân viên để người quản trị xem và thay đổi.
    + deleteEmployee(): Xóa thông tin nhân viên khỏi hệ thống (nếu thao tác xóa được xác nhận).
* ErrorHandler
  - Thuộc tính:
    + Không có thuộc tính cụ thể.
  - Phương thức:
    + displayError(message: String): Hiển thị thông báo lỗi nếu có sự cố xảy ra trong quá trình thực hiện ca sử dụng.
    + requestInput(): Yêu cầu người quản trị nhập lại thông tin nếu có lỗi hoặc thiếu thông tin.

Biểu đồ lớp:
![](https://www.planttext.com/api/plantuml/png/Z9J1JiCm38RlVOgeft7O2-o0Dcb3J488CLuWMxmjKX8N9nbKY2VZm2Fn2hIXhP9s7RirzcSdzc_tv-jxRXqdvxNATefRovvuIQZKGcXff7N47HBxo1YRCc-13DSmOnj7qXo2iQY2tf14P6ICuDM3TNVUx9n4CxcPiHDA4Nm5uKaAMEb2OGcmDdiapGC6ZMt6McyS2CO1TM6YezVTtItzcJN5j7HJm30Yc0SrjTnBMQGEpQMglXT245YRkAmroTdnzoK87-glI85-go1uq1s1Hdp54GqyUhq5Ih8TqPCgdxc31BTSSIeJqmwrbjPMcGTqdUH1QkaYAsE-41LOop0Pz6zJMWSwTE-og0TmiQ3djMc94C65QC__wFxtm2jX0GhEmCCP2R2qXUBbYWXfeYj5-G7ESJiqUqbwMUTkAjyYAk0c6hKwoJqtGW4r3RisVTFOjIcyYpKukuhJwMqhoupb0qtoQw8khE1r2VghM4KrpfhhjguY-uCnJiO3CKxrXc4Sx0r23up5gk5OgSjeAbQUTNUc7OgtAi_cO4JzY_q5003__mC0)
