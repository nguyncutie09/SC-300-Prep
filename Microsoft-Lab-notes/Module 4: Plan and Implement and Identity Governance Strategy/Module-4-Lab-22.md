# Module 4

### Lab 22 - Create and manage a catalog of resources in Microsoft Entra entitlement management

A catalog is a container of resources and access packages. You create a catalog when you want to group related resources and access packages. Whoever creates the catalog becomes the first catalog owner. A catalog owner can add additional catalog owners. You must create and configure a catalog in your organization.

##### Ex 1: Building out resources in Entitlement Management

Để dùng Entra ID terms of use, cần Microsoft Entra ID Premium P1, P2, EMS E3, or EMS E5 subscription.

1. Vào ID Governance > Entitlement management > Catalogs > New catalog

Có Name, Des, Enabled for users to request: **Yes**/No, Enabled for external users to request: Yes/**No** (This setting allows users in selected external directories to be able to request access packages in this catalog. Default is No).

2\. Add resources vào catalog. Chọn catalog vừa tạo > Under Manage. chọn Resources > Add resources, các lựa chọn có thể Add:

* Groups and Teams
* Applications
* SharePoint sites
* Microsoft Entra role (preview)
* Custom data provided resource (preview)

Add group Retail, app Box, Salesforce, SharePoint sites: Brand - pick this SharePoint from your list of available sites > Add

3\. Add additional catalog owners. Chọn catalog vừa tạo > under Manage, chọn Role and admin > có 3 lựa chọn Add là:

* Add catalog owner (có thể là user, group, app)
* Add catalog reader
* Add access package manager
* Add access package assignment manager

Chọn add catalog owner > chọn user muốn làm owner và Add

4\. Edit catalog

ID Gov > Entitlement Management > Catalog > chọn group catalog muốn edit > Overview > Edit > Mục Enabled switch to Yes.

5\. Tạo Access Review cho Guest users. Vào ID Gov > Access Reviews > New access review, có 2 loại template:

* Resource review: Review access to a resource type. Chỉ tập trung vào 1 loại Resource cụ thể, như 1 nhóm, 1 app hoặc 1 role. phù hợp khi muốn kiểm tra xem ai đang có quyền vào 1 nhóm cụ thể.
* Catalog review: Review users access across multiple resource types within a catalog. Quét qua tất cả resources được gom nhóm trong 1 Catalog. phù hợp khi muốn kiểm tra trong Catalog (dự án) cụ thể, user đó đang có những quyền gì trên toàn bộ App, Group và Role của dự án đó.

**Trong lab này thì select template Resource.** 

Tab  Review Type, gồm 2 lựa chọn: Teams + groups, và Apps. Lab chọn Teams + groups.

\-Khi chọn Teams + groups thì xuất hiện thêm mục chọn Review scope, gồm có All Microsoft 365 groups with guest users và Select Teams and groups.

\-Chọn All Microsoft 365 groups with guest users, xuất hiện mục Group để chọn những groups to exclude (mục này không bắt buộc), và mục Scope (bắt buộc), lựa chọn là Guest users only và All users. Lab này chọn Guest users only.

\-Nếu chọn Select Teams and groups thì chỉ hiện group để chọn include.

\-Kéo xuống còn mục Inactive users only và ô tick. Khi được kích hoạt, chỉ những người dùng không hoạt động kể từ một ngày nhất định mới được đưa vào danh sách soát xét. Một người dùng được coi là 'không hoạt động' nếu họ không thực hiện đăng nhập vào tenant (hệ thống khách hàng). Lab này thì kh tick gì.

* Tab Reviews

\-Đầu tiên là ô Multi-stage review, nếu tick sẽ Thêm tối đa 3 giai đoạn (cấp) phê duyệt để hoàn tất việc soát xét.

\-Mục Specify reviewers, có các lựa chọn Group owners, Select users or groups cụ thể, Users review their own access, Managers of users. Nếu là users or groups thì mở ra mục chọn users or groups muốn để làm reviewers. Nếu chọn group owners và managers thì sẽ mở ra mục chọn Fallback reviewers. (kh bắt buộc)

**NOTE**: Fallback reviewers cho phép chọn users or groups thực hiện review khi mà primary reviewers không exist.

\-Mục Specify recurrence of review:

+Duration (in days): default là 3

+Review recurrence: kiểu chọn tần suất review mỗi tuần, tháng, quý, nửa năm và năm.

+Start date

+End: có Never, End on specific day và End after number of occurrences.

* Tab Settings

\-Upon completion settings: best practice nên tick Auto apply results to resource.

+If reviewers don't respond có 4 lựa chọn, No change, Remove access, Approve access và Take recommendations. Lab chọn Remove access.

+At end of review, send notification to: cái này có thể chọn users or groups

\-Enable reviewer decision helpers: tính năng hỗ trợ reviewers đưa ra quyết định

+No sign-in within 30 days: Nếu một người không hề đăng nhập vào hệ thống trong suốt 30 ngày qua, Entra ID sẽ hiện gợi ý là Deny.

+User-to-Group Affiliation (Sự liên kết giữa người dùng và nhóm): Đây là tính năng sử dụng Machine Learning. Hệ thống sẽ nhìn vào sơ đồ tổ chức (Reporting structure) hoặc thói quen làm việc để xem: "Những người khác trong cùng team với ông A đều vào Group này, tại sao ông A lại không?" hoặc ngược lại. Nếu ông A có vị trí, phòng ban hoặc người quản lý hoàn toàn khác biệt so với số đông còn lại trong nhóm, hệ thống sẽ cảnh báo hoặc gợi ý Deny. Nếu ông A "thuộc về" nhóm đó một cách logic (cùng phòng ban với mọi người), hệ thống sẽ gợi ý Approve.

\-Advanced settings: gồm Justification required, Email notifications, Reminders, Additional content for reviewer email

* Tab review + create > Create



**Select thử template Catalog xem có gì**

* Tab Basics:

\-Name new access review: nhập name và des

\-Review Target: Users in Scope có 3 lựa chọn, All users, All users excluding guests và Guest users.

Lab này chọn Guest users

* Tab Resources:

\-Microsoft Entra resources: Lúc nãy chọn template Catalog nên mục này sẽ yêu cầu Select Catalog (có thể create new catalog tại đây).

* Tab Reviewers and schedule: 

\-Multi-stage review

\-Reviewers, có 2 lựa chọn là Managers of users và Resource owners. chọn Resource owners. 

\-Schedule of review series:

+Recurrence tương tự với template Resource nhưng có thêm One time.

+Days open for each review: default là 3 (giống duration của template Resource)

+Start date

+End (tương tự Resource)

* Tab Reviewer experience:

\-Reviewer instructions:
+Require justifications with decisions: yêu cầu reviewer cung cấp lý do cho approval

\-Reviewer decision helpers (tương tụ Resource)

\-Notifications:

+Email notifications for reviewers and review admins

+Reviewer reminder notifications

+Additional completion notification recipients: Select User(s) or Group(s)

+Custom message in reviewer notification emails

* Tab Upon completion settings:

\-Automatic decisions if reviewers don't respond

+No change in decision

+Deny all unreviewed decisions

+Approve all unreviewed decisions

+Take recommendations on all unreviewed decisions

* Review > create

6\. Delete a catalog. chọn vào Catalog muốn xóa xong ở mục Overview có nút Delete next to Edit button.

