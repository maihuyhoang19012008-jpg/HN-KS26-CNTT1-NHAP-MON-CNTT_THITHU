

# BÀI LÀM  : WEBSITE VĂN PHÒNG PHẨM

**Họ và tên:** [ MAI HUY HOÀNG ]

**Ngày hoàn thành:** 23/10/2026

## 1 (4.2) Thao tác máy tính cơ bản bằng CLI

### Các lệnh đã thực hiện (PowerShell trên Windows)

powershell


**Hiển thị đường dẫn tuyệt đối** 
`Get-Location`
**Liệt kê nội dung gồm cả file ẩn** 
`Get-ChildItem -Force`

### Di chuyển nhap_hang.txt vào docs
`Move-Item nhap_hang.txt docs/`

### Di chuyển logo vào media
`Move-Item logo_van_phong_pham.png media/`

### Sao chép logo từ media vào backup
`Copy-Item media/logo_van_phong_pham.png backup/`

### Xoá file tạm .tmp
`Remove-Item temp_131.tmp`

### Vào thư mục logs bằng đường dẫn tương đối, liệt kê, quay lại gốc
Set-Location logs
`Get-ChildItem
Set-Location ..`



### Kết quả liệt kê toàn bộ dự án sau khi tổ chức


C:\...\van-phong-pham-website
1. .env
2.  bai_lam.md
3.  README.md
4.  docs/
` nhap_hang.txt`
5.  media/
` logo_van_phong_pham.png`
6.  data/
  ` don_ban_thang_10.xlsx`
7.  logs/
   `shop.log`
  ` daily_report.txt`
 ` auto_report.txt`
 ` tong_hop.txt`
8.  backup
 - List item

   `logo_van_phong_pham.png`
 - List item
 - List item
    `auto_report.ps1`



## 2 (4.3) Lọc log thủ công

### Lệnh thực hiện

powershell

Lọc dòng chứa ERROR và ghi vào báo cáo : 
`Get-Content logs/shop.log | Select-String "ERROR" > logs/daily_report.txt`

## Đọc kiểm tra
muốn đọc dữ liệu kiểm tra dùng lệnh
`Get-Content logs/daily_report.txt`



### 2 dòng lỗi đầu tiên

```
ERROR: Kết nối cơ sở dữ liệu thất bại
ERROR: Không tìm thấy ảnh sản phẩm SP017

```


## 3 (4.4 ) Tài liệu README.md



## 4 (4.5) Hoàn thiện script tự động báo cáo

### Nội dung `auto_report.ps1` đã hoàn thiện

powershelll 

```
# Script: auto_report.ps1
# Tác giả: [Điền họ tên]
# Ngày tạo: 23/10/2026

Write-Host "Đang lọc log..."

"=== BÁO CÁO LỖI ===" > logs/auto_report.txt
Get-Content logs/shop.log | Select-String "ERROR" >> logs/auto_report.txt

Write-Host "Hoàn thành!"

```

### Lệnh chạy script

powershell

```
.\auto_report.ps1

```

### Nội dung sau :  `logs/auto_report.txt`


```
=== BÁO CÁO LỖI ===
ERROR: Kết nối cơ sở dữ liệu thất bại — mã lỗi 1045
ERROR: Không tìm thấy hình ảnh sản phẩm SP007
ERROR: Đơn hàng DH129 không có thông tin khách hàng
ERROR: Hệ thống hết thời gian chờ kết nối thanh toán

```

----------

## 5 (4.6) Đếm số dòng lỗi

### Lệnh thực hiện


```
Get-Content logs/shop.log | Select-String "ERROR" | Measure-Object | Select-Object -ExpandProperty Count

```

### Kết quả

`4` dòng chứa `ERROR`

----------

## 6 (4.7) Báo cáo tổng hợp

### Các lệnh thực hiện

powershell

 TỔNG HỢP LOG  
 ` logs/tong_hop.txt`


 Nối các dòng WARNING
`Get-Content logs/shop.log | Select-String "WARNING" >> logs/tong_hop.txt`

 số lỗi 
`$so_loi = 
Get-Content logs/shop.log | Select-String "ERROR" | Measure-Object`
"Tổng số lỗi ERROR: 
`$($so_loi.Count)" >> logs/tong_hop.txt`


 **Nội dung** : `logs/tong_hop.txt`



TỔNG HỢP LOG 
`WARNING: Dung lượng đĩa còn dưới 20%
WARNING: Phiên bản PHP sắp hết hỗ trợ
WARNING: Không nhận được phản hồi từ máy chủ sao lưu
Tổng số lỗi ERROR: 4`




## 7 (4.8) Xử lý dữ liệu Excel

### Công thức đã áp dụng dùng Sheet `DonBan`


|Cột|Công thức|Giải thích|
|-|-|-| 
|**E (ten_sp)**|`=VLOOKUP(C2; SanPham!A:C; 2; FALSE)`|Tên sản phẩm khớp chính xác theo mã|
| **F (gia_ban)**| `=VLOOKUP(C2; SanPham!A:C; |3; FALSE)` | Giá bán khớp chính xác theo mã| 
|**G (tien_ban)**|`=D2*F2`|Thành tiền = Số lượng × Đơn giá|

### Lọc dữ liệu

-   Bật **AutoFilter** cho toàn vùng dữ liệu bảng
-   Lọc cột **G** với điều kiện: `>= 300000`
-   Lưu tệp sau khi lọc

>  Không nhập tay dữ liệu — toàn bộ lấy bằng công thức tự động

----------

----------

## README.md [ Tài liệu ]


### Website Cửa Hàng Văn Phòng Phẩm

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


