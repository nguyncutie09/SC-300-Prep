# Module 3

### Lab 19 - Register an application

##### Ex 1: Register an application

1. App registration > (Single tenant, URL là Web: myapp.com/auth) > Register > Tự động được chuyển tới Demo app
2. Under Manage, chọn Auth > Under Redirect URI configuration, Add: gồm các Platform sau:
* Web: nhập redirect uri (nơi nhận token sau khi user log in), dùng cho web app chạy server-side
* Single-page app (SPA): nhập redirect uri, dùng cho web app frontend (client-side): Angular, React, Vue, Blazor WASM
* iOS/macOS: nhập Bundle Ì (trong Xcode), hệ thống tự tạo redirect uri 
* Android: nhập Package name (AndroidManifest.xml) + Signature hash, hệ thống tự tạo redirect uri
* Mobile \& Desktop applications: chọn redirect uri có sẵn hoặc tự nhập

. Desktop khuyến nghị: https://login.microsoftonline.com/common/oauth2/nativeclient

. Dùng cho: App mobile **không dùng MSAL / không dùng broker**, Ứng dụng desktop

Tóm tắt:

Web → server-side

SPA → frontend JS

Mobile native (iOS/Android) → Bundle ID / Package name

Desktop / legacy mobile → nativeclient URI
3. Chọn Web, nhập: https://localhost > Configure

4. Add credentials, cert and client secret. Chọn Certificate \& secrets, có 2 tab Certificates và Client secrets

**NOTE:**

* certificate còn gọi là public key, loại credential được khuyến nghị vì bảo mật cao hơn client secret. hỗ trợ định dạng .cer, .pem, .crt
* client secret (app password) là chuỗi dùng để app tự xác thực thay cho cert, dễ dùng hơn, thường dùng trong development, kém an toàn hơn cert, không khuyến nghị cho production.

Trong lab này thì add New client secret. Nhập: Description = SC300 lab secret, Duration = 90 days (3 months)

Lưu value và secret ID lại trong notepad: 

* value:e1Y8Q\~aHvAxxZxCitkbdz96hpckiGaxJlRk\_DaNO (chỉ hiển thị 1 lần)
* secret id: f7bbe4c5-2b68-4c8a-ad76-5ec5e6d2eeac

**NOTE:** Sau khi register web app có thể thêm scopes (quyền) cho API. Scopes giúp cấp quyền chi tiết (granular) cho app/client sử dụng API.

5. Add a scope. Tạo 1 scope tên Employees.Read.All

Code trong client app sẽ yêu cầu quyền thực hiện các thao tác của web API bằng cách gửi kèm access token trong request đến resource được bảo vệ

Web API chỉ thực hiện hành động nếu access token chứa scopes (hay application permissions) phù hợp với yêu cầu.

Client → gửi access token

API → check scopes trong token

Under Manage > chọn Expose an API > Add a scope > mở ra Application ID URI > nhập giá trị api://.. (giá trị này được generate sẵn, muốn cái khác thì nhập)

**NOTE:** App ID URI là prefix của scopes dùng trong code API, Phải unique toàn cục (globally unique)

* Có thể dùng mặc định: api://<application-client-id>
* Hoặc đặt URI dễ đọc hơn, ví dụ: https://contoso.com/api

Mở ra Add a scope panel: 

* Scope name: Employees.Read.All

quy ước đặt tên phổ biến: resource.operation.constraint (tài nguyên.hành động.ràng buộc)

* Who can consent?: chọn Admins and users (lựa chọn còn lại là Admins only)
* Admin consent display name: Read-only access to employee records
* Admin consent des: Allow the application to have read-only access to all employee data.
* User consent display name: Read-only access to your employee records
* User consent des: Allow the application to have read-only access to your employee data.
* State: Enable

6. (optional) Pre-authorize client

Có thể pre-authorize client app để không cần user consent khi truy cập scopes. Chỉ nên áp dụng với client app đáng tin cậy (trusted app) vì user sẽ không có quyền từ chối consent.

Done mục Scopes thì quay lại Expose an API, kéo xuống 'Authorized client apps' > Add a client app > nhập Client ID (Application ID) của app 'Demo app' nãy tạo (vào overview copy). Nó cũng là phần được default generated sau api:// ở trên. > Tick chọn Authorized scopes (nãy tạo ở trên thì giờ nó hiển thị ở đây: api://d42ff2a1-e1af-4c37-a510-e472721dbc2d/Employees.Read.All) > Add app

Client ID: d42ff2a1-e1af-4c37-a510-e472721dbc2d

Nếu đã làm step này thì client app giờ là PCA, user kh bị prompted để consent khi log in vào app này.

7. Add scope yêu cầu admin consent.
(chỉ admin mới có thể cấp quyền consent)
**NOTE:** Các scope yêu cầu admin consent thường được sd để cung cấp quyền truy cập tới những thao tác có đặc quyền cao hơn, thường dành cho các ứng dụng client chạy dưới dạng dịch vụ backend or daemon - những ứng dụng kh có quá trình log in user 1 cách tương tác.
Scope name: Employees.Write.All
Who can consent: Admins only
...
NOTE: nếu URI dùng https://contoso.com/api thì full scope sẽ hiển thị là https://contoso.com/api/Employees.Read.All tại Expose an API pane.

-Cấu hình client app để được gọi web API với các scope đã tạo.
-Khi được cấp quyền, client sẽ nhận access token (OAuth 2.0).
-Khi gọi API, token này chứa scp (scope) = các quyền đã cấp.
-API sẽ đọc scp để quyết định cho phép hay từ chối request.

##### Ex 2: Manage app registration with a custom role
1. Vào Roles and admins > New custom role > Đặt tên > Next > Chọn 2 permissions sau:
> microsoft.directory/servicePrincipals/managePasswordSingleSignOnCredentials  -   Manage password single sign-on credentials or service principals.
> microsoft.directory/servicePrincipals/synchronizationCredentials/manage    -   Manage application provisioning secrets and credentials.

Next > Create
Chọn 2 quyền này vì đối với việc provisioning app thì đây là những quyền tối thiểu cần thiết để:
- bật và thực thi SSO cho app hoặc service principal được tạo
- và có thể gán enterprise app đó cho 1 tập user or group
Ngoài ra cũng có thể cấp thêm các quyền khác nếu cần.
Xem ds đầy đủ các quyền tại: https://docs.microsoft.com/azure/active-directory/roles/custom-enterprise-app-permissions




