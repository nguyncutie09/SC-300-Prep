# Module 4

### Lab 24 - Manage the lifecycle of external users in Microsoft Entra Identity Governance settings



User ngoài (guest) được cấp quyền qua access package

Khi không còn access package nào nữa (hết hạn hoặc tự bỏ):

→ Bị chặn đăng nhập ngay

→ Sau 30 ngày bị xóa tài khoản



##### **Ex 1: Microsoft Entra Identity Governance settings**

1. Vào ID Gov > Entitlement management > Settings:

Dưới mục **Delegate who can create and manage access reviews** (Updating the settings allows for more users to create and manage reviews.):

(Preview) Group owners can create and manage access reviews for groups they own: Yes/No

Yes → Chủ group (owner) có thể:

* Tự tạo access review
* Tự quản lý review cho group của họ

No → Chỉ admin (Global Admin / Identity Governance Admin) mới làm được

2. Phần life cycle bây giờ khác với hướng dẫn cũ. Truy cập ID Gov > Entitlement management > Control configurations > Sẽ thấy Lifecycle of external user > click View settings, cấu hình:

* Block external user from signing in: Yes tức là khóa đăng nhập đến khi hết access package. Nếu user cần request lại access, không nên bật.

* Remove external user: Yes là xóa tài khoản guest khỏi tenant.

Lưu ý cái này chỉ xóa user được invite qua access package. Dù user có quyền ở resource khác (SharePoint, OneDrive) thì vẫn bị xóa.

* Number of days before removing: default là 30 days. Nếu đặt là 0 thì xóa ngay lập tức.





