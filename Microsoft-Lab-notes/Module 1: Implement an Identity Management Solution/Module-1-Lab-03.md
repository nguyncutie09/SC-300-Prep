# Module 1

### Lab 03 - Assigning licenses using group membership

##### Ex 1: Create a security group and add a user

1. Tạo Security Group
* Member type gồm: assigned, dynamic user, dynamic device
* Microsoft Entra roles can be assigned to the group: Yes (Group đó trở thành role-assignable group) tức là khi gán 1 vai trò cho group thì tất cả user trong group tự động nhận quyền

2. Gán owner và member vào

3. Add license cho group

4. Check license

##### Ex 2: Create a Microsoft 365 group in Microsoft Entra ID

1. Tạo microsoft 365 group
2. Gán owner và user

##### Ex 3: Creating a dynamic group with all users as members

1. Tạo security group và chọn member type là dynamic user
2. Dynamic user members > add dynamic query. Click edit phần Rule syntax, paste vào: *user.objectId -ne null*
* user.objectId: ID duy nhất của user trong Entra ID
* \-ne = not equal
* null: giá trị rỗng, không tổn tại

\-> Tức là lấy user hợp lệ (user không có id = null)

3. Save > Create

4. Chờ để verify, tất cả user đã tạo (hợp lệ) included trong dynamic group này.

##### Thử với các rules khác:

* Tạo group với chỉ Guest users:

(user.objectId -ne null) and (user.userType -eq “Guest”)

* Tạo group với chỉ Member users:

(user.objectId -ne null) and (user.userType -eq “Member”)








