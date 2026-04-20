# Module 3

### Lab 21 - Grant tenant-wide admin consent to an application

##### Ex 1: Admin Consent

###### Task 1 - Grant admin consent in App registrations

1. Cấp admin consent cho app regist

WARNING: Cấp admin consent trên toàn tenant cho 1 app cho phép app và nhà phát hành của nó truy cập vào dữ liệu của tổ chức của bạn. Xem xét kỹ các quyền mà app yêu cầu trước khi cấp consent.

Để cấp admin consent cho app permissions đối với Microsoft Graph API, cần có Global Admin.

2. Chọn cái Demo app đã tạo ở lab 19. Copy lại App ID và Directory ID.

d42ff2a1-e1af-4c37-a510-e472721dbc2d

0ab428ed-9611-4ffa-afb3-915bb61d5c2d

3. Under Manage, chọn API permissions. Under Configured permissions > click Grant admin consent information > Yes

\-Việc cấp admin consent trên toàn tenant thông qua App registrations sẽ thu hồi (revoke) bất kỳ quyền nào đã được cấp trước đó ở mức toàn tenant. (kiểu áp lại permissions mới th)

\-Tuy nhiên, các quyền mà người dùng tự cấp cho chính họ (user consent) sẽ không bị ảnh hưởng.

###### Task 2 - Grant admin consent in Enterprise apps

1. Vào Enterprise apps > chọn Demo app
2. Under Security, chọn Permissions
3. Chọn Grant admin consent. Nó sẽ được prompted mở 1 browser, log in bằng Global Admin, sau đó xuất hiện Permissions requested > Accept.



