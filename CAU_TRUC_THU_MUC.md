# 📁 Cấu Trúc Thư Mục Để Load Ảnh

## Cấu Trúc Khuyến Nghị

```
gesture-Christmas_tree-3d_with_photo/
│
├── christmas_tree_touch&gesture.html    ← File HTML chính
├── README.md
├── HUONG_DAN.md
│
└── images/                              ← Thư mục chứa ảnh (TẠO THƯ MỤC NÀY)
    ├── (1).jpg                          ← Ảnh số 1
    ├── (2).jpg                          ← Ảnh số 2
    ├── (3).png                          ← Ảnh số 3 (PNG cũng được)
    ├── (4).jpg
    ├── (5).jpg
    ├── (10).jpg                         ← Không cần đánh số liên tục
    ├── (20).jpg
    └── (50).jpg
```

## ✅ Tên File Đúng

```
images/
├── (1).jpg      ✅ ĐÚNG
├── (2).jpg      ✅ ĐÚNG
├── (3).png      ✅ ĐÚNG (PNG được)
├── (10).jpg     ✅ ĐÚNG
└── (100).jpg    ✅ ĐÚNG
```

## ❌ Tên File Sai

```
images/
├── 1.jpg           ❌ SAI - Thiếu dấu ngoặc đơn
├── image1.jpg      ❌ SAI - Tên không đúng format
├── (01).jpg        ❌ SAI - Không có số 0 đứng trước
├── ( 1 ).jpg       ❌ SAI - Có khoảng trắng
└── photo(1).jpg    ❌ SAI - Tên file không đúng
```

## 📝 Các Bước Thực Hiện

### Bước 1: Tạo Thư Mục
1. Trong thư mục dự án, tạo thư mục mới tên `images`
2. Đảm bảo thư mục `images` cùng cấp với file HTML

### Bước 2: Đổi Tên Ảnh
1. Copy ảnh vào thư mục `images`
2. Đổi tên theo format: `(số).jpg` hoặc `(số).png`
   - Ví dụ: `my-photo.jpg` → `(1).jpg`
   - Ví dụ: `family.png` → `(2).png`

### Bước 3: Kiểm Tra Code
Mở file HTML và kiểm tra:
```javascript
preload: {
    autoScanLocal: true,    // Phải là true
    scanCount: 200,         // Số lượng ảnh tối đa
    images: []
}
```

### Bước 4: Chạy và Kiểm Tra
1. Chạy local server (xem HUONG_DAN.md)
2. Mở file HTML trong trình duyệt
3. Ảnh sẽ tự động load và hiển thị xung quanh cây thông

## 💡 Tips

1. **Không cần đánh số liên tục:** Có thể có `(1).jpg`, `(5).jpg`, `(10).jpg` mà không cần `(2).jpg`, `(3).jpg`, ...

2. **Hỗ trợ cả JPG và PNG:** Code sẽ tự động tìm `.jpg` trước, nếu không có thì tìm `.png`

3. **Số lượng không giới hạn:** Có thể có 1 ảnh hoặc 200 ảnh, tùy bạn

4. **Tên file phân biệt hoa thường:** `(1).JPG` và `(1).jpg` là khác nhau (nên dùng chữ thường)

## 🔧 Script Đổi Tên Tự Động (Windows PowerShell)

Nếu có nhiều ảnh, có thể dùng script này để đổi tên tự động:

```powershell
# Lưu file này thành rename.ps1 trong thư mục images
$files = Get-ChildItem -Filter *.jpg,*.png,*.jpeg
$counter = 1
foreach ($file in $files) {
    $extension = $file.Extension
    $newName = "($counter)$extension"
    Rename-Item -Path $file.Name -NewName $newName
    $counter++
}
Write-Host "Đã đổi tên $($counter-1) file!"
```

**Cách dùng:**
1. Mở PowerShell trong thư mục `images`
2. Chạy: `.\rename.ps1`
3. Nếu bị lỗi permission, chạy: `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`

## 🔧 Script Đổi Tên Tự Động (Mac/Linux)

```bash
#!/bin/bash
# Lưu file này thành rename.sh trong thư mục images
counter=1
for file in *.jpg *.png *.jpeg; do
    if [ -f "$file" ]; then
        extension="${file##*.}"
        mv "$file" "($counter).$extension"
        ((counter++))
    fi
done
echo "Đã đổi tên $((counter-1)) file!"
```

**Cách dùng:**
```bash
chmod +x rename.sh
./rename.sh
```

