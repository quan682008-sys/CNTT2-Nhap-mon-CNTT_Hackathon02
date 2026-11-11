# BÀI LÀM – HACKATHON 02

- **Mã đề:** 07
- **Họ tên:Nguyễn Minh Quân**
- **Lớp:CNTT2**
- **Link repository:**
- **Hệ điều hành (Windows/macOS):Windows**

## 4.2. Thao tác máy tính cơ bản bằng CLI

### Các lệnh đã chạy

```shell
PS C:\Users\Quan Nguyen> cd E:\starter-kit\spa-website
PS E:\starter-kit\spa-website> ls -force
PS E:\starter-kit\spa-website> mv .\Lich_Lam_Viec.txt docs
PS E:\starter-kit\spa-website> mkdir backup
PS E:\starter-kit\spa-website> copy '.\data\Hoa_Don_Spa_Thang 7.xlsx' backup
PS E:\starter-kit\spa-website> rm *.tmp
PS E:\starter-kit\spa-website> cd .\logs\
PS E:\starter-kit\spa-website\logs> ls
PS E:\starter-kit\spa-website\logs> cd ..
PS E:\starter-kit\spa-website> Get-ChildItem -Recurse -Force

```

### Kết quả liệt kê toàn bộ dự án (Windows: Get-ChildItem -Recurse -Force; macOS: ls -aR)

```text
PS E:\starter-kit\spa-website> Get-ChildItem -Recurse -Force


    Directory: E:\starter-kit\spa-website


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        11/11/2026   1:40 PM                backup
d-----        11/11/2026   1:37 PM                data
d-----        11/11/2026   1:39 PM                docs
d-----        11/11/2026   1:35 PM                evidence
d-----        11/11/2026   1:37 PM                logs
d-----        11/11/2026   1:31 PM                web
------         11/3/2026   7:07 AM             75 .env
-a----         11/3/2026   7:07 AM           2412 bai_lam.md


    Directory: E:\starter-kit\spa-website\backup


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:07 AM           6149 Hoa_Don_Spa_Thang 7.xlsx


    Directory: E:\starter-kit\spa-website\data


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:07 AM           6149 Hoa_Don_Spa_Thang 7.xlsx


    Directory: E:\starter-kit\spa-website\docs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:07 AM            149 Lich_Lam_Viec.txt


    Directory: E:\starter-kit\spa-website\logs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:07 AM            939 Service.log


    Directory: E:\starter-kit\spa-website\web


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        11/11/2026   1:31 PM                images
------         11/3/2026   7:07 AM            597 app.js
------         11/3/2026   7:07 AM            523 index.html
------         11/3/2026   7:07 AM            460 style.css


    Directory: E:\starter-kit\spa-website\web\images


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
------         11/3/2026   7:07 AM           3091 logo-lotuscare.png


```

## 4.3. Lọc log truy cập website

### a) Lệnh lọc các dòng status=500

```shell

PS E:\starter-kit\spa-website> Select-String "status=500" .\logs\Service.log > .\logs\loi_500.txt
PS E:\starter-kit\spa-website> Get-Content .\logs\loi_500.txt

```

### 2 dòng đầu tiên trong logs/loi_500.txt

```text
logs\Service.log:4:2026-07-28 08:12:50 POST /api/dat-lich status=500
logs\Service.log:7:2026-07-28 08:19:23 POST /api/dat-lich status=500

```

### b) Lệnh đếm số dòng status=404 và kết quả

```shell
PS E:\starter-kit\spa-website> (Get-Content .\logs\Service.log |Select-String "status=404").count
```

```text
4
```

## 4.4. Chạy script tong_hop (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
PS E:\starter-kit\spa-website> @'
>> #Script: tong_hop.ps1
>> #Tac gia: Nguyen Minh Quan
>> #Ngay tao: 11/11/2026
>> Write-Host "Dang tao bao cao..."
>> "=== BAO CAO SU CO WEBSITE ===" >logs/tong_hop.txt
>> Get-Content logs/service.log| Select-String "status=404" >>logs/tong_hop.txt
>> >> Get-Content logs/service.log| Select-String "status=500" | Measure-Object >> logs/tong_hop.txt
>> Write-Host "Hoan Thanh!"
>> '@ | set-content tong_hop.ps1

```

### Nội dung file logs/tong_hop.txt

```text
PS E:\starter-kit\spa-website> gc .\logs\tong_hop.txt
=== BAO CAO SU CO WEBSITE ===

2026-07-28 08:16:12 GET /images/phong-spa-3.jpg status=404
2026-07-28 08:39:18 GET /uu-dai-cu status=404
2026-07-28 08:46:40 GET /tin-tuc status=404
2026-07-28 08:48:51 GET /tin-tuc status=404


```

## 4.5. README.md và bảo vệ thông tin bí mật

> README.md, .gitignore và .env.example được chấm trực tiếp trên file ở gốc dự án. Đánh dấu `[x]` vào các mục đã làm để tự kiểm tra.

- [X ] README.md: Heading 1, mô tả có **in đậm** và *in nghiêng*, bảng, code block, task list, blockquote
- [X ] .gitignore có dòng `.env` (tên file đúng, không có đuôi .txt)
- [X ] .env.example có đủ tên biến, giá trị để trống (tên file đúng, không có đuôi .txt)

## 4.6. Kiểm tra trang web bằng DevTools (F12) và báo cáo lỗi

### Bảng lỗi

| STT | Tab DevTools phát hiện lỗi | Tên file hoặc thông báo lỗi | Cách khắc phục |
| --- | --- | --- | --- |
| 1 |Network  |(failed)net::ERR_FILE_NOT_FOUND  |  <img src="images/logo-lotuscare.png" alt="Logo" class="logo">  |
| 2 | Console | app.js:18 Uncaught ReferenceError: hienThiGoiDichVu is not defined | sửa từ hienThiGoiDichVu thành hienThiGoiSpa|

> Ảnh chụp màn hình lưu trong thư mục `evidence/` (network.png, console.png).

### Báo cáo lỗi gửi trưởng nhóm

- **Context:** tôi đang vào web và thấy mất logo và bảng giá trị
- **Expected:** tôi muốn hiện logo và bảng số liệu trên web để dễ dàng làm việc
- **Actual:** hiện tại tôi đang không thể sửa được nó vẫn đang không thấy gì
- **Log:** 
- (failed)net::ERR_FILE_NOT_FOUND
- app.js:18 Uncaught ReferenceError: hienThiGoiDichVu is not defined


### Câu tìm kiếm Google

```text
site:stackoverflow.com "app.js:18 Uncaught ReferenceError: hienThiGoiDichVu is not defined" -quangcao -crack

```

## 4.7. Excel

> Phần Excel được chấm trực tiếp trên file `data/hoa_don_spa_thang_7.xlsx`, không cần ghi vào đây.
