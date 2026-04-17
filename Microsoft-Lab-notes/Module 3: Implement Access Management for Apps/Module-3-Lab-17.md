# Module 2

### Lab 17 - Defender for Cloud Apps application discovery and enforcing restrictions

##### Ex 1: Defender for Cloud Apps discovery

###### Task 1 - Discovery apps in Defender for Cloud Apps

1. Truy cập https://security.microsoft.com/
2. Scroll thanh trái mở mục Cloud apps > Cloud app catalog
3. Filter catagory, tick Cloud storage, Apply
4. Trong list apps (có Dropbox trong đây), chú ý Risk score
5. Mở tab khác và truy cập www.dropbox.com
6. Có thể access vào website này, đóng tab

7. Click vào Dropbox trong click app. Xuất hiện details. Click Sanction. Xuất hiện thông báo Sanctioned app. 

Task 2 - Restrict Apps in Defender for Cloud Apps

8. Chỉnh lại unsanction cho Dropbox. Trong tag app còn có Monitored.

Quy trình này cho phép block các ứng dụng không được phê duyệt theo chính sách của công ty, giúp hạn chế Shadow IT trong tổ chức.



**Lưu ý:** Có độ trễ khi thực hiện việc đánh dấu ứng dụng là sanctioned (được cho phép) hoặc unsanctioned (không được phép). Có thể phải chờ tối đa 5 phút để thay đổi có hiệu lực.



Sau khi ứng dụng bị đánh dấu là ***unsanctioned***, ứng dụng đó sẽ không thể truy cập được thông qua:

* Trình duyệt thông thường
* Trình duyệt ẩn danh (InPrivate)
* Tải từ store

trên các máy client đã được onboard vào Microsoft Defender for Endpoint và tích hợp với Microsoft Defender for Cloud Apps.

