# Bộ cấu hình Shadowrocket — Kiên
Ngày kiểm tra: 26/10/2026 (Việt Nam).

## Kết quả và giới hạn
Đã kiểm tra trực tiếp các trang raw bằng trình duyệt, không chỉ dựa vào kết quả tìm kiếm.
Một số kết quả tìm kiếm vẫn có nội dung đã lưu của kho duyvinh09 dù khi mở trực tiếp trả về 404.
“Tải được script” chỉ chứng minh mã còn được phục vụ. Chưa chạy trên iPhone/Shadowrocket hoặc xác nhận Premium thực tế.
Không có cơ sở để gọi đây là bản “tất cả app đều hoạt động”. Đây là bản dựng để thử từ các nguồn còn truy cập được.

## Các tệp
- Kien_Core4.sgmodule: YouTube/YouTube Music, Locket, Spotify, SoundCloud; 8 rule, 7 URL script duy nhất.
- Kien_Optional.sgmodule: 7 app phụ, dùng thử riêng; không bắt buộc cài.
- AUDIT.json: toàn bộ URL script gốc và kết quả kiểm tra.
- README.md: hướng dẫn và nguồn.

## Bốn app ưu tiên
| App | Nguồn | Xác minh |
|---|---|---|
| YouTube/YouTube Music | Maasea/sgmodule | Đọc trực tiếp cả request (44.024 ký tự) và response (132.973 ký tự); chưa chạy trên thiết bị. |
| Locket | vuong2023/shad, Ohoang7 | Đọc được cả hai script; người dùng đã báo module gốc hoạt động. Bản ghép vẫn cần thử. |
| Spotify | app2smile/rules | Đọc được JSON và protobuf; giữ rule của module tác giả. |
| SoundCloud | Marol62926/MarScrpt | Đọc được script 1.097 ký tự; mã sửa plan/features của ứng dụng, không chứng minh quyền nội dung phía máy chủ. |

YouTube: dùng đúng request/response khác nhau từ module tác giả, không dùng response script cho request như cấu hình cũ.
Thay tham số mẫu bằng giá trị cụ thể; tắt dịch phụ đề trong lần thử đầu, giữ các nút giao diện.
Không giữ các rewrite/map-local video cũ khi thay sang bộ mới.
Locket: giữ nguyên cặp script bạn đã dùng tốt; bỏ hai Header Rewrite RevenueCat trùng chức năng.
Lưu ý: script Locket này có nhánh sửa cả phản hồi RevenueCat không khớp Locket; tránh bật thêm các module RevenueCat khác. Chưa sửa mã upstream.
Spotify: nguồn chỉ mô tả một phần tính năng; không bảo đảm âm thanh rất cao, tải ngoại tuyến hay tài khoản Premium thật.
SoundCloud: nguồn Loon của tác giả ghi phiên bản cũ 5.174.0. Không hứa Go+ catalog, offline hoặc HQ sẽ chạy trên bản hiện tại.

## Module phụ
| App | Quyết định |
|---|---|
| PicsArt | Nguồn NobyDa còn mở được. Chuyển sang http-response và API /shop/subscription đúng theo tài liệu bên trong script; không tự suy đoán API gw-v2. |
| CamScanner | Nguồn NobyDa còn mở được. Tác giả mô tả mở một phần tính năng. |
| Wink | Nguồn ekaznyra còn mở được, mã đọc được. Giới hạn ở vip_info/vip_info_by_group của api-sub.meitu.com. |
| Truecaller | Nguồn ekaznyra còn mở được. Chỉ dùng subscriptions/status và products/apple mà script xử lý. Không bảo đảm các dịch vụ máy chủ. |
| KineMaster | Nguồn NobyDa/Scripting còn mở được. Dùng API assetstore cũ; độ tương thích bản app mới chưa rõ. |
| BeautyPlus | Nguồn ekaznyra còn mở được. Chỉ ghép manual_unlock; không ghép nhánh sửa points/balance. |
| Lightroom | Nguồn litieyin còn mở được. Không tạo quyền lưu trữ cloud thật. |
| Alight Motion | Không ghép: duyvinh09 và quocchienn/Make trả 404; kho Win98Plus cũng không tồn tại công khai khi kiểm tra. Nguồn N9dev chưa xác minh được. |
| Sub-Store | Không ghép: không phục vụ bốn chức năng ưu tiên; ba URL release không xác minh được trong môi trường này. Không kết luận chúng bị xóa. |

## Cách dùng
1. Giải nén ZIP. Giữ bản cấu hình cũ để dự phòng.
2. Trong Shadowrocket, nhập Kien_Core4.sgmodule dưới dạng module vào cấu hình đang dùng.
3. Tắt All_In_One_Locket_Updated và các module khác cùng xử lý YouTube/Locket/Spotify/SoundCloud để tránh trùng.
4. Giữ thiết lập MITM/chứng chỉ riêng đang dùng trên máy. Tệp không chứa CA hoặc thông tin proxy.
5. Tải script và kiểm tra lỗi URL. Đóng hẳn rồi mở lại từng app.
6. Chỉ cài Kien_Optional.sgmodule nếu cần app phụ, sau khi core đã ổn; không nhập lại bản All In One cũ cùng lúc.
7. Nếu app lỗi, tắt module mới để đối chiếu. Không xóa cache/script cũ trước khi thử bản mới.

## Nguồn chính
- https://raw.githubusercontent.com/Maasea/sgmodule/master/YouTube.Enhance.sgmodule
- https://raw.githubusercontent.com/vuong2023/shad/main/modules/Locket_ohb.sgmodule
- https://raw.githubusercontent.com/app2smile/rules/master/module/spotify.module
- https://github.com/Marol62926/Loon/blob/main/soundcloud.plugin
- https://github.com/Maasea/sgmodule/issues/108 (báo cáo giật phát video; không khẳng định mọi phiên bản đều lỗi)
- https://github.com/app2smile/rules/issues/268 (báo cáo tự đăng xuất)
- https://github.com/app2smile/rules/issues/264 (báo cáo giới hạn chọn bài)

Giữ tên tác giả trong nguồn. Không nhận mã của tác giả khác là mã tự viết.
