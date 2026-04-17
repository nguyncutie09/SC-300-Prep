# Module 1

### Lab 05 - Add guest users to the directory

##### Ex 1: Add guest users to the directory

1. Users > All users. Chọn + New user, chọn Invite external user.

NOTE: Nhập địa chỉ email của 1 cá nhân, group email không được hỗ trợ. Microsoft hiện kh hỗ trợ dấu + trong email.

2. Nhập email, display name và message

3. Qua tab Properties, có thể thấy User type là Guest

4. Rv + invite > Invite

##### Ex 2: Invite guest users in bulk

1. Users > All users > Bulk operations > Bulk Invite

Tải file csv về và điển vào

row 1: version

row 2: field names

row 3: example

row 4-: data

2. Save file and upload. Submit.

3. Để xem status, chọn **Select here to view the status of each operation** hoặc **Bulk operation results**. Để xem chi tiết thì chọn vào value dưới # Success, #Failure hoặc Total Requests columns.

###### **MỜI GUEST VỚI POWERSHELL**

* Log in to Azure:

&#x20;Connect-MgGraph -Scopes "User.ReadWrite.All"

* Set giá trị cho email và redirect cho External user:

&#x20;Import-Module Microsoft.Graph.Identity.SignIns

&#x20;   

&#x20;$params = @{

&#x20;    invitedUserEmailAddress = "admin@fabrikam.com"

&#x20;    inviteRedirectUrl = "https://myapp.contoso.com"

&#x20;}

* Gửi invitation:

&#x20;New-MgInvitation -BodyParameter $params





