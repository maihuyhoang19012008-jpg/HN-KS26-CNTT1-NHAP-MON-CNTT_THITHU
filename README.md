


# Website Cửa Hàng Văn Phòng Phẩm

 Xây dựng hệ thống giao diện hiện đại, tích hợp quản lý tồn kho, xử lý đơn hàng và báo cáo theo thời gian thực

 Cấu trúc

| Thư mục/Tệp | Nội dung chính |
|:--|-|
| `docs/` | Tài liệu dự án, phiếu nhập hàng |
| `media/` | Logo, hình ảnh sản phẩm|
| `data/` | Tệp dữ liệu đơn bán, danh mục sản phẩm |
| `logs/` | Nhật ký hệ thống, báo cáo lỗi có cảnh báo |
| `backup/` | Bản sao lưu tài nguyên quan trọng |
| `auto_report.ps1` | Tự động trích xuất lỗi từ log |

## Lệnh xem toàn bộ  cấu trúc dự án
powershell
 *Liệt kê toàn bộ tệp bao gồm ẩn*
`Get-ChildItem -Recurse -Force`

## Tiến độ thực hiện

- [x]   Tổ chức chuẩn hoá cấu trúc thư mục dự án
- [x]  Phát triển giao diện trang chủ
- [x]  Xây dựng trang chi tiết sản phẩm
- [x] Tích hợp cổng thanh toán trực tuyến
- [ ] AI chăm sóc khách hàng nhận giải quyết khiếu nại của khách hàng 
> **note:**  Tệp `.env` không đẩy lên hệ thống quản lý mã nguồn công khai.


