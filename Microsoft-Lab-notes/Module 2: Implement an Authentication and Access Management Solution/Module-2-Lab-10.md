# Module 2

### Lab 10 - Microsoft Entra Authentication for Windows and Linux Virtual Machines

Dùng Microsoft Entra để auth vào Azure VM

##### Điều kiện để login VM bằng Entra ID

1. Khi tạo VM, tick '**Login with Microsoft Entra ID**'
* Hệ thống sẽ tự bật '**System Assigned Managed Identit**y'

2\. Dùng RBAC

* admin gán VM Admin Login
* user thường gán VM User Login
* Không có role thì không thể login được
* Role này gán ở VM level, Resource group, Subscription

3\. User phải là Entra identity

##### Cơ chế hoạt động

1. User log in qua Entra ID
2. Azuze VM dùng Managed Identity để trust Entra
3. RBAC quyết định cho login hay deny

###### Windows VM

* Disable NLA: network level authentication (layer bảo mật của RDP)

Trong Windows VM:

System → Remote Desktop → 

✔ Allow connections only from computers running Remote Desktop with NLA

Phải tắt NLA vì Entra ID login qua RDP không tương thích hoàn toàn với NLA mặc định.

* RDP file phải sửa: (nếu không login Entra sẽ fail)

enablecredsspsupport:i:0

authentication level:i:2

###### Linux VM

* Không dùng RDP, dùng SSH
* Khác với Window ở protocol nhưng auth model giống nhau







