# Module 2

### Lab 16 - Using Azure Key Vault for Managed Identities

##### 

**Managed Identity:** Là identity do Microsoft Entra ID cấp cho resource (VM, App Service…). Dùng để lấy access token mà không cần hardcode credentials.



Vấn đề thực tế là không phải service nào cũng support Entra authentication.



Giải pháp chuẩn:

* Lưu credential (password, api key,..) trong Azure Key Vault
* Managed Identity -> Auth -> Key Vault -> lấy secret -> dùng cho service khác.



##### Flow hoạt động

1. VM có **System-assigned Managed Identity**
2. VM gọi endpoint nội bộ: http://169.254.169.254/metadata/identity/oauth2/token
để lấy access
3. Dùng token đó gọi Key Vault API:

Authorization: Bearer <token>

4. Key Vault trả về Secret



##### Có 2 thứ phải cấu hình đúng

1. Enable Managed Identity
2. Grant quyền Key Vault

Dùng Access policy, role: Secret Management, gán cho chính VM

Nếu thiếu bước này sẽ bị 403 Forbidden.

##### 

##### PowerShell quan trọng

* Lấy token từ Managed Identity

$Response = Invoke-RestMethod -Uri 'http://169.254.169.254/metadata/identity/oauth2/token?api-version=2018-02-01\&resource=https%3A%2F%2Fvault.azure.net' -Method GET -Headers @{Metadata="true"}



* Extract token

$KeyVaultToken = $Response.access\_token



* Gọi Key Vault bằng token

Invoke-RestMethod -Uri https://<keyvault>/secrets/<secret>?api-version=2016-10-01 -Method GET -Headers @{Authorization="Bearer $KeyVaultToken"}







