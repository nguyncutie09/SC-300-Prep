# Module 1

### Lab 06: Add a federated identity provider

Scenario là công ty cần làm việc với nhiều vendors và cần add các tài khoản của vendor vào directory với type guest và cho phép họ dùng gg account để log in. (Thực chất là cấu hình federation giữa Google (IdP) và Microsoft Entra ID.)

GG Accounts đóng vài trò là IdP, còn Entra ID là Service Provider hoặc Resource Provider, chỉ tin tưởng Gg để cho user log in.

Flow:

1. Mời 1 user với gmail của họ
2. user log in bằng google
3. entra match với guest account, cấp access

##### Ex 1: Configure identity providers

###### Task 1 - Cấu hình gg được sd như 1 identity provider

1. Truy cập https://console.developers.google.com và log in gg account
2. Tạo 1 project mới. Chọn ký tự 3 chấm tròn kế thanh search hoặc Ctrl + O. Chọn New project. Nhập tên project 'MyB2BApp2'. Nhấn create
3. Ctrl O, chọn vào tên project mới tạo. Thanh bên trái tên APIs \& Services. chọn mục OAuth consent screen. Nhấn Get started.
4. Phần **App info**, nhập tên app 'Microsoft Entra ID' và chọn email từ dropdown. Phần **Audience**, chọn External. Phần C**ontact info**, nhập cùng email với phần App info. Phần finish tick I agree. Create.

Tiếp tục

1. Click Create OAuth client. App type chọn Web app. Để Name theo default.
2. Phần Authorized JavaScript origins, Add và nhập:

https://microsoftonline.com

3\. Phần Authorized redirect URIs, click Add và nhập:

* 1st url: https://login.microsoftonline.com
* 2nd url: https://login.microsoftonline.com/te/***tenant*** ***ID***/oauth2/authresp
* 3rd url: https://login.microsoftonline.com/te/***tenant name***.onmicrosoft.com/oauth2/authresp

4\. Click create. Sau đó copy client id và client secret.

644183526689-1m9m6i31h2rvbj5fh4aeitmppa25v7kh.apps.googleusercontent.com

GOCSPX-g6jbpShc\_IgoBtKWFTHgqAr6Yg45

Task 2 - Add a test user

1. Thanh trái, chọn Audience. Kéo xuống Test users, chọn Add users. Thêm gmail vào để test lab. Save.

(Vì app chưa publish, chỉ user trong danh sách này login được)

2\. Test log in (user đó đã accept guest invitation)

###### Task 3 - Add authorized domain to Branding

1. Thanh trái, chọn Branding. Tại Authorized domains, add domain 'microsoftonline.com.'. cần paste app domain vào nữa.
2. Tại Developer contact information, add email dev. email dùng tạo app á.

##### Ex 2: Configure Azure to work with an External identity provider

###### Task 1 - Configure Microsoft Entra ID for Google federation

1. Vào External identities > All. Tại lựa chọn Google, nhấn configured. Nhập client id và client secret. Save.

###### Task 2 - Invite you Test User account

Tạo guest user và gửi lời mời với email ex 1 đã nhập trong Test users.

###### Task 3 - Accept the invitation and login

1. Log in and accept invitation qua email.



NOTE: nếu federation work thì user nhập email sẽ redirect sang Gg Account, sau đó quay lại Microsoft entra id mà kh cần verify email thêm. vì entra tin gg đã xác thực user. Nếu kh work đúng cách thì không redirect sang gg, entra kh biết tin ai. nó sẽ gửi mail Account verification và yêu cầu confirm qua email.



##### Task 4 - Login to Microsoft 365 using your Google account

1. Nếu done task 3 được thì task này oke. Mở Inprivate browser. Enter: login.microsoftonline.com
2. Chọn sign in options > sig in to an organization
3. Enter tenant domain name > Next
4. Nhập tiếp gmail > Next. Nó sẽ tự chuyển hướng sang Gg, ấn next. Nhập pass > Next.

