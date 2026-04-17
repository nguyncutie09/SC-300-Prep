# Module 2

### Lab 13 - Implement and test a conditional access policy

Your organization needs to be able to limit user access to its internal applications. You must deploy an Microsoft Entra conditional access policy.



**Note** - For Conditional Access Policies, you can turn off Security Defaults, the key points to remember are from the training. Additional information on Security defaults can be found at this link: https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/concept-fundamentals-security-defaults

##### 

##### Ex 1: Set a conditional access policy to block DebraB from accessing Sway

1. Xác thực user có quyền vào Sway

2. Tạo policy block user access vào Sway

Lưu ý exclude acc admin

3. Test policy xem thực thi đúng không

Kết quả là user kh còn access được vào Sway



##### Ex 2: Test conditional access policies with “What if”

What If = Conditional Access policy simulation engine, dùng để kiểm tra policy sẽ áp dụng như thế nào trước khi bật thật. Hệ thống sẽ trả về Policy nào sẽ được áp dụng và Policy nào không áp dụng

1. Vào Conditional Access > Policies > Click nút What if trên thanh ngang
2. Xem các mục sau:
* (bắt buộc) Mục Identity:

Identity type gồm các lựa chọn: Users, Guest or External users, Workload identities, Agent identities (preview)

. Với **User**, click Edit user và chọn user

. Với **Guest or External users**, có các lựa chọn:

\-B2B collaboration guest users

\-B2B collaboration member users

\-B2B direct connect users

\-Service provider users

\-Other external users

\-Local guest users

và chọn Tenant, nhập tenant id hoặc domain name sau đó click Select

. Với **Workload identities**, click Edit service principal, chọn Enterprise app cần thiết sau đó Select.

. Với **Agent identities**, click Edit agent identities, chọn agent và Select.

* (bắt buộc) Mục Target resource:

Target type gồm các lựa chọn: Cloud apps, User actions và Auth context.

. Với Cloud apps click Select cloud app, chọn App và click Select

. Với User actions, có các lựa chọn:

\-Register security information

\-Register or join device

\-Recover account

. Với Auth context (mục này lúc làm lab chưa có, kh note)

* Mục Sign-in conditions, sẽ dựa trên:

. (bắt buộc) Device platform: Android, iOS, Windows Phone, Windows, macOS, Linux.

. (bắt buộc) Client app:

\-Mobile apps and desktop client - Modern auth clients

\-Mobile apps and desktop client - Exchange ActiveSync clients (supported platform)

\-Mobile apps and desktop client - Exchange ActiveSync clients (unsupported platform)

\-Mobile apps and desktop client - Other client

. Auth flow: None, Device code flow, Auth transfer

. Insider threat: No risk, Minor, Moderate, Elevated.

. Sign-in risk: No risk, Low, Medium, High.

. User risk: No risk, Low, Medium, High.

. IP address

. Country

* Mục Filter for devices

Property | Value | Delete



##### Ex 3: Configure sign in frequency controls using a conditional access policy

Phần session chọn Sign-in frequency nhập 30. Enable Report-only.



NOTE: Report-only mode là một trạng thái mới của chính sách Conditional Access, cho phép quản trị viên đánh giá tác động của chính sách trước khi kích hoạt trong môi trường thật.



Với chế độ report-only:

* Chính sách Conditional Access có thể được bật ở trạng thái report-only.
* Trong quá trình đăng nhập, các chính sách ở trạng thái report-only vẫn được đánh giá nhưng không được thực thi.
* Kết quả được ghi lại trong tab Conditional Access và Report-only trong chi tiết **Sign-in logs.**
* Khách hàng có đăng ký Azure Monitor có thể theo dõi tác động của các chính sách Conditional Access thông qua **Conditional Access insights workbook.**





