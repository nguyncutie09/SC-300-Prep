# Module 4

### Lab 26 - Configure Privileged Identity Management for Microsoft Entra roles

A Privileged role administrator can customize Privileged Identity Management (PIM) in their Microsoft Entra organization, including changing the experience for a user who is activating an eligible role assignment. You must become familiar with configuring PIM.

##### Ex 1: Configure Microsoft Entra role settings

1. Tìm role  Compliance Administrator. và xem settings của nó.
2. Require approval to activate. Vào role Compliance Administrator, click Edit > Select Require approval to activate checkbox (mặc định nó đã checked) > Select approvers > chọn account Admin của mình đang dùng, Select > Update

##### Ex 2: Use PIM to assign Microsoft Entra roles

Global Admin / PIM → cấp role

Có 2 kiểu:

* Permanent → luôn có quyền
* Eligible (PIM) → chỉ có quyền khi activate, xong thì tự hết

PIM giúp chuyển từ quyền luôn bật (always-on) → sang quyền tạm thời (just-in-time) để tăng bảo mật.

1. PIM > Under Manage, chọn Microsoft Entra roles > Under Manage, chọn Roles > Add assignments > tìm và chọn role Compliance Administrator > Under Manager, trong mục Assignments có thể thấy 2 tab là 2 assignment types: Eligible và Active.

\-Eligible yêu cầu người được gán role phải thực hiện một hành động để sử dụng role đó.

Các hành động có thể bao gồm:

* Xác thực đa yếu tố (MFA)
* Cung cấp lý do sử dụng (business justification)
* Yêu cầu phê duyệt từ người có thẩm quyền

\-Active assignments thì không yêu cầu hành động nào để sử dụng role. Người dùng được gán dạng active sẽ luôn có quyền của role đó.

2. Add assignment > chọn members, select > next > chọn assignment type và có checkbox permanent cho 2 type trên > Assign

3. Activate your Microsoft Entra roles. Vào PIM > Under Task, chọn My roles > tại Microsoft Entra roles, có thể thấy entry cho role Compliance Administrator ở tab Eligible và bao gồm action Active. Click Active > chờ tí để quá trình Verification hoàn tất > chỉnh Duration > nhập Reason > click Active.

**NOTE**: Theo nguyên tắc least privilege, chỉ nên kích hoạt tài khoản trong khoảng thời gian thực sự cần thiết.

4. Assign a role with restricted scope

Đối với một số role nhất định, phạm vi quyền được cấp (scope) có thể được giới hạn trong:

* một administrative unit
* một service principal
* hoặc một application

Quy trình sau là một ví dụ về việc gán role với phạm vi thuộc một administrative unit.

PIM > Microsoft Entra roles > Under Manage, select Roles > Add assignments > chọn role User Administrator > Scope type có 2 kiểu là Administrative unit và Directory. Lab này thì chọn Directory. > Chọn member > Next

As you did when assigning a role without a restricted scope, you would add members and complete the settings options. For now, select Cancel.

**TIP**: Go to https://docs.microsoft.com/en-us/azure/active-directory/roles/admin-units-manage for more information about the administrative unit scope type.

5. Update or remove an existing role assignment. Vào PIM > Under Manage, chọn Assignments > các entry kéo sang phải có nút Remove | Update

