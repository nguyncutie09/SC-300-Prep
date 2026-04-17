# Module 2

### Lab 15 - Configure an Multifactor authentication registration policy

Ex 1: Set up MFA registration policy

1. Vào ID Protection > MFA registration policy
* Phần Assignments, có thể chọn users
* Phần Controls, có thể tick Require Microsoft Entra ID mfa registration. 

Khi tick thì nó sẽ yêu cầu user thực hiện đăng ký mfa the next time user đó log in. Bắt user đăng ký MFA method (chuẩn bị), chứ không yêu cầu phải log in MFA.

**Lưu ý**: policy này chỉ ảnh hưởng lên cloud-based azure mfa. nếu có mfa server thì nó sẽ không bị ảnh hưởng.

* Policy enforcement, enable or disable



