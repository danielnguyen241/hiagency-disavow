# Hướng dẫn xử lý và Disavow backlink

Tài liệu này hướng dẫn cách kiểm tra backlink đáng ngờ và gửi file Disavow
cho website bằng Google Search Console.

> Không lưu danh sách backlink hoặc file Disavow của khách hàng trong repository
> công khai. File thực tế cần được gửi riêng cho người phụ trách website.

## 1. Khi nào nên Disavow?

Chỉ cân nhắc Disavow khi backlink có dấu hiệu spam hoặc thao túng rõ ràng, ví dụ:

- Domain không còn hoạt động hoặc không phân giải được DNS.
- Domain `.xyz` có tên ngẫu nhiên và tạo hàng trăm hoặc hàng nghìn backlink.
- Website link farm, PBN hoặc website bị hack.
- Backlink không liên quan và xuất hiện hàng loạt trên nhiều trang.
- Website nhận cảnh báo về unnatural links trong Google Search Console.

Không nên Disavow các nền tảng hoặc directory hợp pháp chỉ vì số lượng backlink
lớn. Luôn kiểm tra URL nguồn và anchor text trước.

## 2. Kiểm tra domain

Với từng referring domain:

1. Mở domain bằng HTTPS.
2. Kiểm tra HTTP status và redirect cuối cùng.
3. Kiểm tra domain còn phân giải DNS hay không.
4. Xác định website thật, website hết hạn, link farm hoặc redirect sang nội dung khác.
5. Ưu tiên xử lý các domain spam đã ngừng hoạt động, đặc biệt là `.xyz`.

## 3. Tạo file Disavow

Tạo file văn bản thuần `.txt`, mã hóa UTF-8 hoặc ASCII. Mỗi domain nằm trên một
dòng theo định dạng:

```text
# Reviewed YYYY-MM-DD
domain:example-spam.xyz
domain:another-spam.xyz
```

Dòng bắt đầu bằng `#` là ghi chú. Không thêm `https://`, đường dẫn hoặc ký tự
không cần thiết khi muốn loại bỏ toàn bộ domain.

## 4. Kiểm tra file cũ

Google thay thế toàn bộ danh sách hiện tại khi upload file mới. Nếu property đã
có file Disavow, hãy tải file cũ xuống và gộp các domain cần giữ trước khi upload.

## 5. Upload lên Google

1. Mở [Google Search Console Disavow Links](https://search.google.com/search-console/disavow-links).
2. Chọn đúng property dạng URL-prefix.
3. Upload file `.txt` đã kiểm tra.
4. Xác nhận kết quả và lưu lại bản file đã gửi.

Google có thể cần vài tuần để thu thập lại dữ liệu và áp dụng danh sách.

## Nguyên tắc của HiAgency

- Ưu tiên kiểm tra thủ công và Disavow thận trọng.
- Giữ lại các domain đang hoạt động hoặc có khả năng mang lại referral traffic.
- Ưu tiên các `.xyz` không hoạt động và cụm backlink spam rõ ràng.
- Không công khai dữ liệu backlink hoặc file Disavow của khách hàng.

Tài liệu cập nhật lần cuối: 2026-07-29.
