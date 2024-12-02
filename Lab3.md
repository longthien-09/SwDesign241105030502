# Lab 3

## 1. Subsystem context diagrams

### Biểu đồ ngữ cảnh của các hệ thống con

### BankSystem 
![](https://www.planttext.com/api/plantuml/png/p5B1Ri8m3BtdAtnRaGRSgsb280wzeV459ZKY8asgsA1LsxviXttIVc5fscw52Uswd5xiz-nd9v_l7miM37AghBg3bNSIl5NQ8ZDii8aNsmSj1NXH4Czy3dNmcYAbxYZPHBsfg2-SKDYZ9cK61CKItN7Ri53LwqkgFHl9ebWVI1_pjbD2zx2BvCBjVGxB7eKAnNWtIT8pMbEYq93CRlDZn7jBw3fhszEEEnERu9-RViJ_uMtjn4W3gzOIyS_sKz-Hqr69LlP4Dc4-c9hLxzUQJXyljfyFqp6aoWndWshCU7YTpKOxkSYrrRuzNIUktTtI_I5Ra2lRd_W5003__mC0)

Giải thích

- PayrollController: Điều khiển quá trình trả lương, yêu cầu chuyển tiền qua IBankSystem.

- IBankSystem: Giao diện với phương thức deposit và validateBankInfo.

- BankSystem: Hệ thống thực hiện chuyển tiền và kiểm tra thông tin tài khoản.

- Paycheck và BankInformation: Chứa thông tin lương và tài khoản ngân hàng.

### PrintService

Giải thích

- PayrollController: Điều khiển việc in phiếu lương và gửi yêu cầu in đến IPrintService.

- IPrintService: Giao diện với phương thức print để in phiếu lương.

- PrintService: Hệ thống thực hiện việc in phiếu lương từ PayrollController.

- Paycheck: Đối tượng chứa thông tin phiếu lương cần in.

![](https://www.planttext.com/api/plantuml/png/b5513e8m4Bpt5NjJ3y3T66D2F7WZyeAAQsWiXNGBiL5Vvi4d-GLR0GqO3_QqipipEvi-RlSL6QvDNKWsWRXKHfUIPP8JGSAj0x9hIjHmPk1U586k5LJjU3fZL-Qq6sLG7tY6JFGLR1BjG8gw4GwrwigtfjoPPpbcnpdqLUUJrZkoPB20H9SdssVvtsYjZ30MOgz7-jpqudZ25YKtebIKYuhOzxL1i1nTC6-N4hmy21h1sP2nk8JX8EnexZtV6NvFLgZs_akU0000__y30000)

### ProjectManagementDatabase subsystems
![](https://www.planttext.com/api/plantuml/png/f591JiCm4Bpx5NkZFRIzHmXLQdleeL85BzWcss3asC6xgHG1B-F0a_W2DhM5Kb8k-BIsTsPsnlvy_rYoe9UkCUe6LiwATqQL1fbXZttOc7HeoCEBWh0M2sYzAocqjEUMoLIzgO3VMY5_n9AKpXLizzuzKIaxj5XJGrOIJKsIhjOag0rFg6cDwuaAsAHgMi2mvwppq1suPw4cJtefiKR10pBzNsfZHKiFgwX3dFGoPYYVSG5rJmP5EykFkcNrEyZPx6uic08yYTTq8euHnrlGzkZWf56DzD--pkT_c2-W8aCrIg3pzDmH2uWR8uhpP5C1XcLytO3ACNrFSGquj7ysqNdxOw5AmLoVT9I6nVcB8DIIR1N_wXS0003__mC0)

Giải thích

- PayrollController: Điều khiển việc truy xuất thông tin dự án cần thiết cho việc tính lương.

- IProjectManagement: Giao diện cung cấp phương thức getProjectDetails để lấy thông tin chi tiết dự án của nhân viên.

- ProjectManagementDatabase: Hệ thống con thực tế lưu trữ thông tin chi tiết về các dự án.

- Employee: Đối tượng đại diện cho nhân viên cần truy xuất thông tin dự án.

- ProjectDetails: Đối tượng chứa các chi tiết về dự án mà nhân viên tham gia.

# 2. Analysis class to design element map

| Analysis Class             | Design Element                  |
|----------------------------|----------------------------------|
| LoginForm                  | LoginForm                       |
| MaintainEmployeeForm       | MainEmployeeForm                |
| TimecardForm               | TimecardForm                    |
| MainApplicationForm        | MainApplicationForm             |
| TimecardController         | TimecardController              |
| SystemClockInterface       | SystemClockInterface            |
| PayrollController          | PayrollController               |
| Paycheck                   | Paycheck                        |
| Employee                   | Employee                        |
| BankSystemInterface        | IBankSystem, BankSystem         |
| PrintServiceInterface      | IPrintService, PrintService     |
| ProjectManagementSystem    | IProjectManagement, ProjectManagementDatabase |
| PayrollReportGenerator     | PayrollReportGenerator          |
| EmployeeDatabase           | EmployeeDatabase                |

# 3. Design element to owning package map

| Design Element        | "Owning" Package                            | 
|-----------------------|---------------------------------------------|
| LoginForm             | Middleware::Security::GUI Framework         |
| MainEmployeeForm      | Applications::Employee Activities           |
| TimecardForm          | Applications::Employee Activities           |
| MainApplicationForm   | Middleware::Security::GUI Framework         |
| TimecardController    | Applications::Employee Activities           |
| SystemClockInterface  | Applications::Payroll                       |
| PayrollController     | Applications::Payroll                       |
| Paycheck              | Business Services::Payroll Artifacts        |
| Employee              | Business Services::Employee Management      |
| IBankSystem           | External Interfaces::Banking                |
| BankSystem            | External Interfaces::Banking                |
| IPrintService         | External Interfaces::Printing               |
| PrintService          | External Interfaces::Printing               |
| IProjectManagement    | External Interfaces::Project Management     |
| ProjectManagementDatabase | External Interfaces::Project Management |

# 4.	Architectural layers and their dependencies

![](https://www.planttext.com/api/plantuml/png/V99DRiCW48NtFWNoFbUealHdbKgHt0jC9wEK6WOqu4fMrPDrqIFr2iLABPm8p0PfveFtvi7lzyysH90uMDDum1xEfDgZK22E4BLZTO2Hf5MVZKeBdVMEKq-r1tVM_EJ4jhUT8upYZEa6Qq768l9elN4ZqJDmKhIfTi6-iecTzqRZkeT_fNl7STeJSqkyQ4i8Sbf1PYzBPE5ZFmJD54BLn7o-b0E-4VPLKrSw3n11xH3NfFR0VJU6I8NGHNFiI3uq5fo8UoUCEUr9x1K2JGwQnLEgpUQk66kXTc7pz5Kavr15beFLxxaQCIlFtUgCM-BJzC7_0000__y30000)
