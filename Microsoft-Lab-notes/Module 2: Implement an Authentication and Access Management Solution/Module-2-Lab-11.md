# Module 2

### Lab 11 - Assign Azure resource roles in Privileged Identity Management

Dùng Microsoft Entra PIM để gán quyền trên Azure resources. Tạo trạng thái Eligible role assignment cho user (chưa active ngay, kích hoạt khi cần, có thể yêu cầu MFA/lý do)

##### Ex 1: PIM with Azure resources

1. Vào ID Gov > PIM > Quick start > Manage access
2. Click Overview, mục này có thể xem
* Role activations in last 7 days (gồm All roles, Global Administrator, Privileged Role Administrator, User Administrator)
* Role assignment distribution (gồm Eligible, Permanent active assignments và Time based assignments)
* PIM Activities in last 30 days (Members with new eligible assignments và Members assigned as active)
* Roles by assignment (descending) (Role|Eligible|Active)
* Alert

3. Dưới mục Manage:

* **Roles** > (Resource type có sẵn là Directory) > Add assignment > chọn role > chọn member > Next > Assignment type: Eligible > Assign

Có mục tick cho chọn permanent, dựa trên assignment type nó sẽ là permanently eligible hoặc permanently assigned. Nếu không tick permanent thì có thể chọn ngày start và ngày end của assignment đấy.

4. Muốn remove thì dưới Manage vào mục Assignments

Hiển thị assignment và người dùng được assign, kéo thanh ngang sang phải có thể thấy nút Remove | Update

###### Vai trò liên quan

PIM có thể quản lý các role Azure như:

* Owner
* User Access Administrator
* Contributor
* Security Admin
* Security Manager



