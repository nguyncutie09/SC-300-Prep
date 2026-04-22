# Module 4

### Lab 23 - Add terms of use and acceptance reporting

Microsoft Entra terms of use policies provide a simple method that organizations can use to present information to end users. This presentation ensures users see relevant disclaimers for legal or compliance requirements. This article describes how to get started with terms of use (ToU) policies.

You must create and enforce a ToU policy for your organization.

##### Ex 1: Set up a Term of Use and test them

1. ID Gov > Entitlement management > Kéo xuống chọn Terms of use > New terms:

Nhập Name, Terms of use document chọn file PDF, nhập Display Name. Select default language.

**Note**: The language option allows you to upload multiple terms of use, each with a different language. The version of the terms of use that an end user will see will be based on their browser preferences.

\-Require users to expand the terms of use: on/off (buộc người dùng mở hết terms of user trước khi bấm Accept, tránh việc họ click đồng ý mà chưa đọc)

\-Require users to consent on every device: on/off (vd log in trên máy mới phải accept lại)

\-Expire consents: on/off (nếu bật là có thời hạn, hết hạn phải accept lại). Nếu set on thì bên dưới xuất hiện thêm Expire starting on (mm/dd/yyyy) và frequency (annually | bi-annually | quarterly | monthly)

\-Duration before re-acceptance required (days): vd set 90 days thì mỗi 90 ngày user phải xác nhận lại Terms of Use.

2. Dưới mục Conditional access > Enforce with conditional access policy templates, chọn Policy templates, có thể là Custom policy hoặc Create conditional access policy later.

**IMPORTANT**: Conditional Access policy controls (including terms of use) do not support enforcement on service accounts. We recommend excluding all service accounts from the Conditional Access policy.

3. Sau khi click Custom policy, chuyển tới trang để tạo policy mới. Tạo CA để enforced ToU, Grant access cho terms of use > Select. Enable policy và Create.

4. Log in với user đã gán CA và sẽ được yêu cầu accept terms of use. Nếu decline thì log in lại vẫn sẽ được yêu cầu accept.

5. Xem report ai decline or accept ToU. Vào ID Gov > Entitlement management > ToU, có thể xem các ToU đã tạo và Current accepted/current declined. Select number hiển thị dưới sẽ biết là user nào đã thực hiện accepted/declined, tại thời điểm nào. Có nút download để download ToU report.

6. User có thể review ToU mà họ đã accepted. Vào https://myapps.microsoft.com, Overview  > VIEW SETTINGS AND PRIVACY > Settings \& Privacy > Tab Privacy > kéo xuống Organization's notice > thấy ToU, You can edit some details of terms of use, but you can’t modify an existing document.

7. Edit ToU details. Vào entitle management > ToU > Click vào 1 entry term cần edit > Edit terms > Update an existing terms of use document. sau khi update có thể yêu cầu người dùng re-accept.
