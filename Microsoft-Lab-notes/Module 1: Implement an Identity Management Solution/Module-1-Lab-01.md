# Module 1

### Lab 01: Manage user roles

##### Ex 1: Create a new user and test their application admin rights

1. Tạo user

ChrisG@cyforgeglobal.onmicrosoft.com

ChrI34@s

2. Khi đăng nhập bằng user sẽ yêu cầu set pass mới, sau đó MFA (do security default)

3. Check quyền

Tạo app trên tài khoản user ChrisG

Enterprise app > New app > Create (bị khóa)

Nhiều chức năng khác tài khoản này cũng không có quyền



##### Ex 2: Assign quyền cho user và check

Sau khi cấp quyền thì chris đã có thể create app



##### Ex 3: Remove role

Tick chọn user và chọn Delete



##### Ex 4: Bulk import of users

Với file CVS:

row 1: version

row 2: Name, Username, Initial Password,..

row 3: Example

row 4-: data



###### Có thể bulk sử dụng Powershell

* Lệnh cài đặt:

Install-Module Microsoft.Graph -Scope CurrentUser -Verbose

* Lệnh để xác nhận

Get-InstalledModule Microsoft.Graph

* Lệnh để log in

Connect-MgGraph -Scopes "User.ReadWrite.All"

Nên sử dụng MOD account (Moderator - người kiểm duyệt, quản trị viên tầm trung) để connect. Chấp thuận permissions request và đóng browser.

* Để xác thực đã connect, chạy lệnh để xem những user đang tồn tại

Get-MgUser

* Để assign 1 temporary pass cho tất cả các user mới, chạy cmd:

&#x20;$PWProfile = @{

&#x20;    Password = "<Enter a complex password you will>";

&#x20;    ForceChangePasswordNextSignIn = $false

&#x20;}

* Muốn tạo new user thì dùng cmd sau:

&#x20;New-MgUser `

&#x20;    -DisplayName "New PW User" `

&#x20;    -GivenName "New" -Surname "User" `

&#x20;    -MailNickname "newuser" `

&#x20;    -UsageLocation "US" `

&#x20;    -UserPrincipalName "newuser@<labtenantname.com>" `

&#x20;    -PasswordProfile $PWProfile -AccountEnabled `

&#x20;    -Department "Research" -JobTitle "Trainer"



##### Ex 5: Remove a user from Microsoft Entra ID

Chọn user và xóa, có thể restore user đó (trong vòng 30 ngày sau khi xóa) tại mục Restore User.



##### Ex 6:  Add a Windows 10 license to a user account

Tìm user, chọn user đó và click vào license xem thì không có.

Assign license cho user thông qua admin.microsoft.com (365 admin) tại Billing > License

(user phải có Usage Location mới có thể assigned license)

