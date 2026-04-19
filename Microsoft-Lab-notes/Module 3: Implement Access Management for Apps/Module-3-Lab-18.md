# Module 3

### 18 - Defender for Cloud Apps Access and Session Policies

##### Ex 1: Create and test the Conditional Access App Contol policy

1. Make sure là user ChrisG không bị hạn chế gì khi truy cập forms.microsoft.com
2. Cấu hình Conditional Access. Mục Session chọn 'Use Conditional Access App Control'. Có box Use custom policy.. xuất hiện, click mũi tên chọn 'Monitor only'. Enable policy 'On'.
3. Truy cập lại Forms, confirm Chris haCd access và nhận được thông báo: 'Your company is monitoring the usage of this application.

##### Ex 2: Setup alerts in Microsoft Defender for Cloud Apps

1. Log in vào security.microsoft.com bằng Global Admin.
2. Cloud apps > Policies > Policy management > Create policy > Access policy. Activities matching all of the following -> Intune compliant -> Microsoft Entra Hybrid joined  -> unselect Microsoft Entra Hybrid joined
3. Select apps > chọn Forms (giờ là Apps matching all of the following, Apps and domains | equals | (nhập domain app, chọn Both apps and domains))
4. Actions > chọn Test. (giờ là Governance actions, chọn Tag app as monitored)
5. Alerts > chọn Send alert as email. Create.
6. Log in Chris vào Forms to trigger activity. Chris nhận được message Your company is monitoring the usage of this application.
7. Trở về Defender for cloud apps, Investigate > Activity log > App: filter chọn Microsoft Forms. Có sign-in records.

