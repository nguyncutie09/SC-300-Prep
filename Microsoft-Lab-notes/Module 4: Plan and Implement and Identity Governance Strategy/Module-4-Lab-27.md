# Module 4

### (optional) Lab 27 - Microsoft Sentinel Kusto Queries for Microsoft Entra data sources

Kết nối dữ liệu từ entra ID với các hệ thống bảo mật khác. sau đó dùng KQL (kusto query language) để phân tích log, hunting.

##### Ex 1: Configure Microsoft Sentinel for Kusto Queries

1\. Tạo workspace Sentinel.

Vào portal.azure.com với quyền Global Admin. Search Microsoft Sentinel. Click Create để tạo workspace > Create a new workspace:

* Tab Basics

\-Chọn subscription

\-Chọn resource group

\-Đặt name

\-Chọn region

Review + create. sau khi create, chọn vào entry của workspace vừa tạo.

2. Select Add, this will add the workspace to Microsoft Sentinel and open Microsoft Sentinel.

3. Add Microsoft Entra ID as a Data source

Trong Microsoft Sentinel, Content management > Select Content hub > Cài connector Microsoft Entra ID > Bật log: Sign-in logs và Audit logs > Apply > Sau đó Sentinel sẽ bắt đầu ingest log từ Entra

4. Chạy KQL

Vào Logs > Chạy query mẫu (Audit → User IDs) >Xem activity của user

Nếu mới tạo thì có thể chưa có dữ liệu





