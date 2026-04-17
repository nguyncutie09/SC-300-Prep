# Module 1

### Lab 04 - Configure external collaboration settings

##### Ex 1: Allowing guest users to be invited into your organization

1. Cho phép guest user self-service sign up

Users > User settings.

Chọn vào Manage external user collaboration settings.

Chọn Yes cho Enable guest self-service sign up via user flows.

Khi doanh nghiệp có 1 web/app:

* Yes: ai cũng có thể tự đăng ký vào hệ thống, guest có thể tự bấm sign up, tạo tài khoản và dùng luôn.
* No: người ngoài (guest) không tự đăng ký được. Bắt buộc admin phải tạo user hoặc invite (qua email)

2. Cấu hình external collaboration settings

External identities > All identity providers

Chọn vào Configured kế Email one-time passcode và bật Yes

Note - A OTP code is a very secure way to invite a user to join your organization.

External identities > **External collaboration settings**

***Guest user access***<i>,</i> chọn *Guest user access is restricted to properties and memberships of their own directory objects (most restrictive)*.

###### NOTE

* **Guest users have the same access as members (most inclusive)**: guest gần như kh khác gì user nội bộ, có quyền truy cập tương đương
* **Guest users have limited access to properties and memberships of directory objects: (Default)** guest bị chặn 1 số thao tác như liệt kê user, xem ds group, duyệt tài nguyên trong directory. có thể xem membership của các group kh bị ẩn
* **Guest user access is restricted to properties and memberships of their own directory objects (most restrictive)**: guest chỉ truy cập được thông tin của chính họ



***Guest invite settings***<i>, chọn Member users and users assigned to specific admin roles can invite guest users including guests with member permissions!</i>

###### NOTE

* **Anyone in the organization can invite guest users including guests and non-admins (most inclusive)**: ai cũng mời guest được
* **Member users and users assigned to specific admin roles can invite guest users including guests with member permissions**: member (user nội bộ) và user có role admin nhất định có thể mời
* **Only users assigned to specific admin roles can invite guest users**: chỉ user có role admin cụ thế mới được mời
* **No one in the organization can invite guest users including admins (most restrictive)**: không ai được mời, khóa hoàn toàn việc mời guest

Nếu Member có thể mời đặt là No, còn **admin và người dùng có role Guest Inviter** có thể mời đặt là Yes. Thì người dùng có role Guest Inviter vẫn có thể mời guest như bình thường.



***Collaboration restrictions,*** <i>có 3 option sau</i>

* Allow invitations to be sent to any domain (most inclusive)
* Deny invitations to the specified domains
* Allow invitations only to the specified domains (most restrictive)

Sau đó có phần nhập Target domains

###### IMPORTANT

* Có thể tạo allow list or deny list chứ kh thể dùng cả 2 cùng lúc. Mặc định domain không nằm trong allow list sẽ bị coi là deny và ngược lại.
* Chỉ có thể tạo 1 policy duy nhất cho mỗi tổ chức trong Entra ID. có thế cập nhật policy để thêm domain hoặc xóa policy để tạo lại.
* Số lượng domain khi thêm vào allow/deny list không giới hạn theo số lượng, mà bị giới hạn bởi kích thước policy. Kích thước tối đa 25kB (25000 ký tự), gồm ds domain và các cấu hình khác trong policy.
* Ds này hoạt động độc lập với allow/block list của OneDrive for Business và SharePoint Online. Nếu muốn hạn chế chia sẻ file trong sharepoint sẽ phải cấu hình riêng ở dịch vụ đó.
* Ds này không áp dụng cho user bên ngoài đã accept lời mời trước đó. Policy chỉ có hiệu lực sau khi được tạo. Nếu user đang trạng thái pending (chưa accept) và mình block domain của họ. Khi họ bấm accept -> sẽ bị fail





