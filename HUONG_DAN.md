# 🎄 Hướng Dẫn Chạy và Tùy Chỉnh Cây Thông Noel 3D

## 📋 Mục Lục
1. [Cách Chạy Dự Án](#cách-chạy-dự-án)
2. [Cách Tùy Chỉnh](#cách-tùy-chỉnh)
3. [Các File HTML Khác Nhau](#các-file-html-khác-nhau)
4. [Troubleshooting](#troubleshooting)
5. [🚀 Deploy để Người Khác Xem](#deploy-để-người-khác-xem)

---

## 🚀 Deploy để Người Khác Xem

Bạn muốn chia sẻ cây thông cho bạn bè xem? Xem hướng dẫn chi tiết tại: **[HUONG_DAN_DEPLOY.md](./HUONG_DAN_DEPLOY.md)**

**Tóm tắt nhanh:**
- **GitHub Pages** (khuyến nghị): Miễn phí, tích hợp GitHub
- **Netlify**: Kéo thả là xong, cực dễ
- **Vercel**: Nhanh, tự động deploy
- **Firebase Hosting**: Của Google, miễn phí
- **Surge.sh**: Đơn giản nhất, 1 lệnh

Tất cả đều **miễn phí** và hỗ trợ **HTTPS** (cần cho camera)!

---

---

## 🚀 Cách Chạy Dự Án

### ⚠️ Lưu Ý Quan Trọng
**KHÔNG được mở trực tiếp file HTML bằng cách double-click!** Dự án sử dụng ES Modules và cần quyền truy cập camera, nên phải chạy qua local server.

### Phương Pháp 1: VS Code (Khuyến nghị) ⭐

1. Mở VS Code
2. Cài đặt extension **"Live Server"** (Ritwick Dey)
3. Click chuột phải vào file HTML (ví dụ: `christmas_tree_touch&gesture.html`)
4. Chọn **"Open with Live Server"**
5. Trình duyệt sẽ tự động mở

### Phương Pháp 2: Python

Mở terminal/PowerShell trong thư mục dự án và chạy:

```bash
# Python 3
python -m http.server 8000

# Hoặc Python 2
python -m SimpleHTTPServer 8000
```

Sau đó mở trình duyệt và truy cập: `http://localhost:8000/christmas_tree_touch&gesture.html`

### Phương Pháp 3: Node.js

```bash
npx http-server .
```

Sau đó truy cập: `http://localhost:8080/christmas_tree_touch&gesture.html`

### Phương Pháp 4: PHP (nếu có cài PHP)

```bash
php -S localhost:8000
```

---

## 🎨 Cách Tùy Chỉnh

### 1. Tùy Chỉnh Màu Sắc

Mở file HTML và tìm object `CONFIG` (thường ở dòng 220-250). Tìm phần `colors`:

```javascript
const CONFIG = {
    colors: {
        bg: 0x050d1a,              // Màu nền (hex)
        fog: 0x050d1a,              // Màu sương mù
        champagneGold: 0xffd966,    // Màu vàng champagne
        deepGreen: 0x03180a,         // Màu xanh lá cây
        accentRed: 0x990000,         // Màu đỏ nhấn
    },
    // ...
};
```

**Cách đổi màu:**
- Sử dụng công cụ chuyển đổi màu online: https://www.color-hex.com/
- Hoặc dùng format hex: `0xRRGGBB` (ví dụ: `0xff0000` = đỏ, `0x00ff00` = xanh lá)

**Ví dụ tùy chỉnh:**
```javascript
colors: {
    bg: 0x000000,              // Nền đen
    fog: 0x1a1a2e,              // Sương mù xanh đậm
    champagneGold: 0xffd700,    // Vàng kim loại
    deepGreen: 0x228b22,        // Xanh lá sáng hơn
    accentRed: 0xff1744,        // Đỏ tươi
}
```

### 2. Tùy Chỉnh Số Lượng Particles

Trong object `CONFIG`, tìm phần `particles`:

```javascript
particles: {
    count: 1500,        // Số lượng hạt chính (cây thông)
    dustCount: 2000,    // Số lượng hạt bụi vàng
    snowCount: 1000,    // Số lượng bông tuyết
    treeHeight: 24,     // Chiều cao cây
    treeRadius: 8       // Bán kính cây
}
```

**Lưu ý:** Tăng số lượng particles sẽ làm giảm hiệu suất. Khuyến nghị:
- Máy yếu: `count: 800`, `dustCount: 1000`, `snowCount: 500`
- Máy trung bình: `count: 1500`, `dustCount: 2000`, `snowCount: 1000`
- Máy mạnh: `count: 2500`, `dustCount: 3000`, `snowCount: 2000`

### 3. Tùy Chỉnh Camera

```javascript
camera: { 
    z: 50  // Khoảng cách camera (số càng lớn = càng xa)
}
```

### 4. Cách Load Ảnh vào Cây Thông

Có **3 cách** để load ảnh vào cây thông:

#### 📁 Cách 1: Tự Động Load từ Thư Mục `images/` (Khuyến nghị)

**Bước 1:** Tạo thư mục `images` trong cùng thư mục với file HTML:
```
gesture-Christmas_tree-3d_with_photo/
├── christmas_tree_touch&gesture.html
├── images/                    ← Tạo thư mục này
│   ├── (1).jpg
│   ├── (2).jpg
│   ├── (3).png
│   ├── (4).jpg
│   └── ...
```

**Bước 2:** Đặt tên ảnh theo format: `(số).jpg` hoặc `(số).png`
- ✅ Đúng: `(1).jpg`, `(2).jpg`, `(3).png`
- ❌ Sai: `1.jpg`, `image1.jpg`, `(01).jpg`

**Bước 3:** Trong code, cấu hình:
```javascript
preload: {
    autoScanLocal: true,    // Bật tự động quét
    scanCount: 200,         // Quét từ (1) đến (200)
    images: []
}
```

**Lưu ý:**
- Code sẽ tự động tìm `(1).jpg`, nếu không có thì tìm `(1).png`
- Nếu cả 2 đều không có, sẽ bỏ qua và tiếp tục với `(2).jpg`
- Không cần đánh số liên tục, ví dụ: có `(1).jpg`, `(5).jpg`, `(10).jpg` là được

#### 🌐 Cách 2: Load Ảnh từ URL (Internet)

Thêm URL ảnh vào mảng `images` trong CONFIG:

```javascript
preload: {
    autoScanLocal: true,
    scanCount: 200,
    images: [
        'https://images.unsplash.com/photo-1543589077-47d81606c1bf?w=600',
        'https://images.unsplash.com/photo-1576919228236-a097c32a5cd4?w=600',
        'https://example.com/my-photo.jpg'
    ]
}
```

**Lưu ý:**
- Ảnh phải cho phép CORS (Cross-Origin Resource Sharing)
- Nếu ảnh từ domain khác không cho phép CORS, sẽ bị lỗi
- Khuyến nghị dùng Unsplash, Imgur, hoặc host ảnh trên server của bạn

#### 📤 Cách 3: Upload Ảnh Trực Tiếp (Dễ nhất)

**Trên giao diện web:**
1. Click nút **"Select Folder"** → Chọn thư mục chứa ảnh (load tất cả ảnh trong thư mục)
2. Hoặc click **"Select Files"** → Chọn nhiều file ảnh cùng lúc

**Lưu ý:**
- Ảnh sẽ được load ngay lập tức
- Không cần đổi tên file
- Hỗ trợ: `.jpg`, `.jpeg`, `.png`, `.gif`, `.webp`

#### ⚙️ Tùy Chỉnh Cấu Hình Load Ảnh

```javascript
preload: {
    autoScanLocal: true,    // true = tự động quét, false = tắt
    scanCount: 200,         // Số lượng ảnh tối đa (1-200)
    images: []              // Danh sách URL
}
```

**Ví dụ:**
- Chỉ load từ URL, không quét local:
  ```javascript
  preload: {
      autoScanLocal: false,
      scanCount: 0,
      images: ['https://example.com/photo1.jpg']
  }
  ```
- Tăng số lượng ảnh quét:
  ```javascript
  preload: {
      autoScanLocal: true,
      scanCount: 500,  // Quét từ (1) đến (500)
      images: []
  }
  ```

#### 🔍 Kiểm Tra Ảnh Đã Load

- Mở **Developer Tools** (F12) → Tab **Console**
- Nếu ảnh load thành công: không có lỗi
- Nếu ảnh lỗi: sẽ thấy thông báo "404" hoặc "Failed to load"
- Ảnh sẽ xuất hiện xung quanh cây thông dưới dạng khung vàng

### 5. Tùy Chỉnh Hiệu Ứng Bloom (Ánh sáng)

Tìm function `setupPostProcessing()`:

```javascript
const bloomPass = new UnrealBloomPass(/*...*/, 1.5, 0.4, 0.85);
bloomPass.threshold = 0.65;  // Ngưỡng phát sáng (0-1)
bloomPass.strength = 0.5;    // Cường độ phát sáng (0-3)
bloomPass.radius = 0.4;      // Bán kính phát sáng (0-1)
```

**Tùy chỉnh:**
- `threshold` thấp hơn = nhiều vật phát sáng hơn
- `strength` cao hơn = sáng hơn
- `radius` cao hơn = ánh sáng lan tỏa rộng hơn

### 6. Tùy Chỉnh Tốc Độ Xoay

Tìm function `animate()` và tìm dòng:

```javascript
STATE.rotation.y += 0.3 * dt;  // Tốc độ xoay tự động
```

Thay đổi `0.3` thành giá trị khác:
- `0.1` = chậm
- `0.5` = nhanh
- `1.0` = rất nhanh

### 7. Tùy Chỉnh Background CSS

Tìm thẻ `<style>` và tìm phần `body`:

```css
body { 
    background: radial-gradient(circle at center, #0f2027 0%, #203a43 50%, #2c5364 100%); 
    background-color: #050d1a; 
}
```

**Ví dụ tùy chỉnh:**
```css
/* Nền đen đơn giản */
background: #000000;
background-color: #000000;

/* Nền gradient tím */
background: radial-gradient(circle at center, #1a0033 0%, #4a0080 50%, #8b00ff 100%);

/* Nền gradient đỏ Noel */
background: radial-gradient(circle at center, #1a0000 0%, #660000 50%, #cc0000 100%);
```

### 8. Tùy Chỉnh Text "Merry Christmas"

Tìm thẻ `<h1>` trong HTML:

```html
<h1>Merry Christmas</h1>
```

Đổi thành:
```html
<h1>Chúc Mừng Giáng Sinh</h1>
<!-- hoặc -->
<h1>Feliz Navidad</h1>
```

### 9. Tùy Chỉnh Kích Thước Text

Trong CSS, tìm:

```css
h1 { 
    font-size: 56px;  /* Đổi số này */
}
```

Hoặc cho responsive:
```css
h1 { 
    font-size: 8vw;  /* 8% chiều rộng màn hình */
    max-size: 56px;
}
```

---

## 📁 Các File HTML Khác Nhau

Dự án có nhiều phiên bản:

1. **`christmas_tree_touch&gesture.html`** ⭐ (Khuyến nghị)
   - Hỗ trợ đầy đủ: Touch, Gesture, Stats
   - UI ẩn mặc định, bấm 'S' để hiện stats

2. **`christmas_tree_pro.html`**
   - Phiên bản Pro với MediaPipe tự động bật

3. **`christmas_tree.html`**
   - Phiên bản cơ bản

4. **`christmas_tree2.html`**, **`christmas_tree3.html`**
   - Các phiên bản thử nghiệm

5. **`christmas_tree_helicalphoto.html`**
   - Ảnh xếp theo hình xoắn ốc

6. **`christmas_tree_touch&gesture_Cloudimages.html`**
   - Sử dụng Cloud Images

---

## 🎮 Điều Khiển

### Bàn Phím:
- **H**: Ẩn/hiện UI
- **S**: Ẩn/hiện Stats (chỉ trong `touch&gesture.html`)

### Chuột:
- **Kéo thả**: Xoay cây
- **Click vào ảnh**: Phóng to ảnh
- **Scroll**: Zoom (nếu có OrbitControls)

### Cử Chỉ Tay (cần bật camera):
- **🖐️ Bàn tay mở**: Chế độ SCATTER (phân tán)
- **✊ Nắm tay**: Chế độ TREE (cây thông)
- **🤏 Pinch (ngón cái + ngón trỏ)**: Chế độ FOCUS (phóng to ảnh ngẫu nhiên)

### Màn Hình Cảm Ứng:
- **Kéo**: Xoay
- **Tap đúp**: Chuyển SCATTER/TREE
- **Tap ảnh**: Phóng to ảnh

---

## 🔧 Troubleshooting

### Lỗi: "Failed to load module"
**Nguyên nhân:** Mở file trực tiếp thay vì qua server
**Giải pháp:** Chạy qua local server (xem phần "Cách Chạy")

### Lỗi: Camera không hoạt động
**Nguyên nhân:** 
- Chưa cho phép quyền camera
- Không phải HTTPS (trừ localhost)
**Giải pháp:**
- Cho phép quyền camera trong trình duyệt
- Chạy trên localhost hoặc HTTPS

### Lỗi: Ảnh không load
**Nguyên nhân:** 
- Đường dẫn sai
- File không tồn tại
**Giải pháp:**
- Kiểm tra thư mục `./images/` có tồn tại không
- Đảm bảo tên file đúng format: `(1).jpg`, `(2).jpg`, ...

### Cây thông chạy chậm/lag
**Giải pháp:**
- Giảm số lượng particles (xem phần 2)
- Tắt bloom effect (comment dòng `composer.addPass(bloomPass)`)
- Giảm `snowCount`

### Không thấy gì trên màn hình
**Giải pháp:**
- Kiểm tra console (F12) xem có lỗi không
- Đảm bảo đã chạy qua server
- Thử file HTML khác

---

## 💡 Tips & Tricks

1. **Tạo thư mục images:** Tạo thư mục `images` trong cùng thư mục với file HTML
2. **Tối ưu ảnh:** Nén ảnh trước khi upload để tăng tốc độ
3. **Fullscreen:** Nhấn F11 để fullscreen
4. **Screenshot:** Ẩn UI (nhấn H) rồi chụp màn hình
5. **Mobile:** Dự án hỗ trợ mobile, nhưng hiệu suất có thể kém hơn

---

## 📝 Ví Dụ Tùy Chỉnh Hoàn Chỉnh

Tạo một theme "Đỏ Noel":

```javascript
const CONFIG = {
    colors: {
        bg: 0x1a0000,
        fog: 0x330000,
        champagneGold: 0xff4444,  // Đỏ thay vì vàng
        deepGreen: 0x004400,
        accentRed: 0xff0000,
    },
    particles: {
        count: 1200,
        dustCount: 1500,
        snowCount: 800,
        treeHeight: 20,
        treeRadius: 7
    },
    camera: { z: 45 }
};
```

Và CSS:
```css
body { 
    background: radial-gradient(circle at center, #1a0000 0%, #660000 50%, #cc0000 100%); 
}
```

---

**Chúc bạn có một Giáng Sinh vui vẻ! 🎄🎅**

