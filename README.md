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

## 2. Review backlink qua hai nguồn

Không dùng riêng một công cụ để ra quyết định. Google Search Console và Semrush
có index, thời điểm crawl và cách lấy mẫu khác nhau, vì vậy một nguồn có thể
không hiển thị cụm spam mà nguồn còn lại phát hiện.

### Bước 1: Review Google Search Console

1. Vào **Links > External links > Top linking sites**.
2. Export danh sách domain, số linking pages và số target pages.
3. Ưu tiên kiểm tra:
   - Domain tên ngẫu nhiên, đặc biệt là `.xyz`.
   - Domain tạo số lượng link lớn bất thường.
   - Link được rải tới nhiều target pages không liên quan.
   - Domain không được nhận diện là khách hàng, đối tác, directory hoặc nền tảng
     hợp pháp.
4. Lưu danh sách ứng viên, chưa đưa trực tiếp vào file Disavow.

### Bước 2: Review Semrush

1. Export báo cáo Backlinks dạng CSV.
2. Nhóm dữ liệu theo root domain và kiểm tra:
   - Authority Score của source page/domain.
   - Source URL, target URL và anchor text.
   - Thuộc tính `nofollow`, `sponsored`, `ugc` và `sitewide`.
   - Ngày `First seen`, `Last seen` và trạng thái `Lost`.
3. Tìm các network có dấu hiệu đồng bộ:
   - Nhiều domain đăng cùng một tiêu đề hoặc cùng một slug.
   - Link xuất hiện trong cùng một khoảng thời gian ngắn.
   - Anchor và target URL giống nhau trên hàng loạt domain.
   - Domain có Authority Score rất thấp, mất DNS, redirect sang nội dung khác,
     domain parking hoặc nội dung không liên quan.
4. Không Disavow chỉ vì Authority Score thấp. Các citation thật, profile thương
   hiệu, backlink nofollow và link từ khách hàng vẫn có thể hợp lệ.

### Đối chiếu và hợp nhất

1. So sánh ứng viên từ GSC với Semrush.
2. Giữ lại domain chỉ xuất hiện ở một nguồn nếu bằng chứng spam vẫn rõ ràng.
3. Loại bỏ domain khách hàng, đối tác, referral traffic và directory hợp pháp.
4. Khử trùng lặp và ghi lại lý do cho từng nhóm domain.
5. Chỉ chuyển danh sách đã review qua cả hai bước sang file Disavow đề xuất.

## 3. Kiểm tra domain

Với từng referring domain:

1. Mở domain bằng HTTPS.
2. Kiểm tra HTTP status và redirect cuối cùng.
3. Kiểm tra domain còn phân giải DNS hay không.
4. Xác định website thật, website hết hạn, link farm hoặc redirect sang nội dung khác.
5. Ưu tiên xử lý các domain spam đã ngừng hoạt động, đặc biệt là `.xyz`.

## 4. Tạo file Disavow

Tạo file văn bản thuần `.txt`, mã hóa UTF-8 hoặc ASCII. Mỗi domain nằm trên một
dòng theo định dạng:

```text
# Reviewed YYYY-MM-DD
domain:example-spam.xyz
domain:another-spam.xyz
```

Dòng bắt đầu bằng `#` là ghi chú. Không thêm `https://`, đường dẫn hoặc ký tự
không cần thiết khi muốn loại bỏ toàn bộ domain.

Trước khi bàn giao, kiểm tra file:

- Mỗi dòng dữ liệu phải có dạng `domain:example.com`.
- Không có domain trùng lặp.
- Không có URL scheme, path hoặc ký tự thừa.
- File được lưu bằng UTF-8 hoặc ASCII và có phần mở rộng `.txt`.

## 5. Kiểm tra file cũ

Google thay thế toàn bộ danh sách hiện tại khi upload file mới. Nếu property đã
có file Disavow, hãy tải file cũ xuống và gộp các domain cần giữ trước khi upload.

## 6. Upload lên Google

1. Mở [Google Search Console Disavow Links](https://search.google.com/search-console/disavow-links).
2. Chọn đúng property dạng URL-prefix.
3. Upload file `.txt` đã kiểm tra.
4. Xác nhận kết quả và lưu lại bản file đã gửi.

Google có thể cần vài tuần để thu thập lại dữ liệu và áp dụng danh sách.

## Nguyên tắc của HiAgency

- Ưu tiên kiểm tra thủ công và Disavow thận trọng.
- Luôn review độc lập qua Google Search Console và Semrush trước khi hợp nhất.
- Giữ lại các domain đang hoạt động hoặc có khả năng mang lại referral traffic.
- Ưu tiên các `.xyz` không hoạt động và cụm backlink spam rõ ràng.
- Không xem Authority Score thấp là lý do duy nhất để Disavow.
- Không công khai dữ liệu backlink hoặc file Disavow của khách hàng.

Tài liệu cập nhật lần cuối: 2026-07-29.
