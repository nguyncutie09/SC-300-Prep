# Module 2

### Lab 08 - Enable multi-factor authentication

##### Ex 1: Review and enable Multi-factor Authentication in Azure

1. Vào multifactor authentication, dưới mục Configure, click 'Additional cloud-based multifactor authentication settings'
2. Sang tab Service settings:
* **App passwords**: có thể enable hoặc disable, cho phép users tạo unique pass cho 1 app mà không support MFA. Tính năng này giúp user log in bằng danh tính Entra nhưng sd 1 pass khác được tạo riêng cho app đó.
* **Trusted IPs**: bỏ qua MFA đến từ 1 dải IP cụ thể hoặc có thể bỏ qua MFA đến từ users đã federated
* **Remember multifactor authentication on trusted device**: cho phép user được nhớ MFA trên những device mà đã được trust. Có thể chỉnh số ngày.

3. Cấu hình conditional access policies.

##### Ex 2:  Configure MFA to be required for login

1. Users > All users > Chọn Per-user MFA
2. Chọn user muốn enable MFA sau đó click Enable MFA > Enable
3. Status chuyển sang Enforced
4. Log in lại để test MFA

