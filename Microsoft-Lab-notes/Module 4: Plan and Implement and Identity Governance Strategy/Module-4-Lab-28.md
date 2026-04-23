# Module 4

### Lab 28 - Monitor and managed security posture with Identity Secure Score



##### Ex 1: Using Identity Secure Score to monitor and manage identity security posture

1. Vào identity score > tìm hiểu. kéo xuống cuối, có 1 bảng:

Priority | Recommendation | Required licenses | Release type | Secure Score points 
 Impacted resource type | Status | Last updated

2\. Execute an improvement action. Click vào recommendation 'Protect all users with a sign-in risk policy.' Review the risk, nó bảo có 7 users đang kh được protected. có thể xem Action plan và cách resolve the threat.

3\. Select link 'Follow these steps to create a Conditional Access policy from scratch or by using a template'. 

4\. Cấu hình Sign-in risk protection policy. Tạo 1 CA, include all users, exclude  MOD Administrator. áp dụng cho all resources.

* Conditions

Chọn 0 conditions selected > dưới mục Sign-in risk, chọn Not configured > Enable Configure sang Yes > Select the sign-in risk level this policy will apply to: High and Medium. > Done

* Grants

Tick Require risk remediation > Under Require authentication strength > chọn Phishing-resistant MFA. > Select

Lưu ý muốn grant cái Require risk remediation thì Conditions cũng cần cấu hình User risk, kh chỉ mỗi Sign-in risk.



Flow:

Người dùng đăng nhập: Nhập Username/Password như bình thường.

Hệ thống đánh giá rủi ro (Risk Check): AI của Microsoft sẽ soi xem lần đăng nhập này có gì "sai sai" không (vị trí lạ, thiết bị lạ, IP lạ...).

Đối chiếu Chính sách:

Nếu rủi ro Thấp (Low/No Risk): Cho vào thẳng.

Nếu rủi ro Trung bình/Cao (Medium/High): Kích hoạt "chế độ khó".

Thử thách xác thực: Hệ thống bắt người dùng phải dùng MFA chống lừa đảo (như khóa vật lý FIDO2 hoặc Windows Hello).

Kết quả: \* Vượt qua được -> Được vào và rủi ro được xóa (Remediated).

Không vượt qua được -> Cấm cửa hoàn toàn.

