# Module 1

### Lab 02: Working with tenant properties

##### Ex 1: Create a custom subdomains

1. Tạo custom domain

Vào Domain names > Add custom domain > nhập

Sau khi add xong phải verify bằng TXT record (hoặc MX)

2\. Add record TXT vào nơi quản lý domain

* Nếu dùng domain gốc thì host là @
* Nếu dùng subdomain thì host là phần sub

Còn lại các trường khác thì copy bên Entra sang (Value, TTL)

Chờ sau đó 2-3 phút rồi verify



##### Ex 2: Changing the tenant display name

1. Đổi tên display

Overview > Properties > Nhập tên và Save

* Có thể xem Tenant ID ở đây
* Helpful khi lưu tenant id để sử dụng: 13f5a5f4-e2dd-423f-b034-931223812596

**Access management for Azure resources**

Khi bật bằng user nào thì user đó “có thể cấp quyền cho bất kỳ resource nào trong Azure



##### Ex 3: Setting your privacy information

1. Add privacy info, gồm  Global privacy contact and Privacy statement URL

Technical contact thì thường nên là người trong team kỹ thuật, vận hành hệ thống, devops,

Global privacy contact nên là legal team, compliance officer, IT Admin

2\. Privacy statement URL

Viết privacy xong ném link vào

Important: a guest user sẽ thấy thông báo này khi được mời qua B2B collaboration.

3\. Check Privacy Statement

Log in vào azure > click vào avt góc phải chọn View account > thanh bên trái chọn Setting \& Privacy > Privacy > trong mục **Organization's notice** đã hiện **CyForge VN organizational privacy statement. Đây cũng là nơi sẽ hiển thị terms of use.**

