# 🚀 Hướng Dẫn Deploy Cây Thông Noel 3D

## 📋 Mục Lục
1. [GitHub Pages (Khuyến nghị - Miễn phí)](#github-pages)
2. [Netlify (Dễ nhất - Miễn phí)](#netlify)
3. [Vercel (Nhanh - Miễn phí)](#vercel)
4. [Firebase Hosting (Google - Miễn phí)](#firebase-hosting)
5. [Surge.sh (Đơn giản - Miễn phí)](#surgesh)
6. [Lưu Ý Quan Trọng](#lưu-ý-quan-trọng)

---

## 🌟 GitHub Pages (Khuyến nghị)

### Ưu điểm:
- ✅ **Hoàn toàn miễn phí**
- ✅ **Không giới hạn băng thông**
- ✅ **HTTPS tự động** (cần cho camera)
- ✅ **Tích hợp với GitHub**
- ✅ **Tên miền tùy chỉnh** (nếu có)

### Cách Deploy:

#### Bước 1: Tạo Repository trên GitHub

1. Đăng nhập vào [GitHub.com](https://github.com)
2. Click nút **"New"** (hoặc **"+"** → **"New repository"**)
3. Đặt tên repository (ví dụ: `christmas-tree-3d`)
4. Chọn **Public** (Private cũng được nhưng phải trả phí cho GitHub Pages)
5. **KHÔNG** tích "Initialize with README"
6. Click **"Create repository"**

#### Bước 2: Upload Code lên GitHub

**Cách 1: Dùng GitHub Desktop (Dễ nhất)**

1. Tải [GitHub Desktop](https://desktop.github.com/)
2. Cài đặt và đăng nhập
3. Click **"File"** → **"Add Local Repository"**
4. Chọn thư mục dự án của bạn
5. Nhập commit message: `Initial commit`
6. Click **"Commit to main"**
7. Click **"Publish repository"**
8. Chọn repository vừa tạo → **"Publish"**

**Cách 2: Dùng Git Command Line**

Mở terminal/PowerShell trong thư mục dự án:

```bash
# Khởi tạo git (nếu chưa có)
git init

# Thêm tất cả files
git add .

# Commit
git commit -m "Initial commit"

# Thêm remote (thay YOUR_USERNAME và REPO_NAME)
git remote add origin https://github.com/YOUR_USERNAME/REPO_NAME.git

# Push lên GitHub
git branch -M main
git push -u origin main
```

**Cách 3: Upload trực tiếp trên GitHub**

1. Vào repository vừa tạo
2. Click **"uploading an existing file"**
3. Kéo thả tất cả files vào
4. Click **"Commit changes"**

#### Bước 3: Bật GitHub Pages

1. Vào repository trên GitHub
2. Click tab **"Settings"** (ở trên cùng)
3. Scroll xuống phần **"Pages"** (bên trái)
4. Ở **"Source"**, chọn **"Deploy from a branch"**
5. Chọn branch **"main"** và folder **"/ (root)"**
6. Click **"Save"**
7. Đợi 1-2 phút, GitHub sẽ tạo URL cho bạn

#### Bước 4: Truy Cập Website

URL sẽ có dạng:
```
https://YOUR_USERNAME.github.io/REPO_NAME/christmas_tree_touch&gesture.html
```

**Ví dụ:**
```
https://john.github.io/christmas-tree-3d/christmas_tree_touch&gesture.html
```

#### Bước 5: Tạo File index.html (Tùy chọn)

Để URL ngắn gọn hơn, tạo file `index.html` trỏ đến file chính:

```html
<!DOCTYPE html>
<html>
<head>
    <meta http-equiv="refresh" content="0; url=christmas_tree_touch&gesture.html">
</head>
<body>
    <p>Redirecting... <a href="christmas_tree_touch&gesture.html">Click here</a></p>
</body>
</html>
```

Hoặc copy nội dung từ `christmas_tree_touch&gesture.html` vào `index.html`.

Sau đó URL sẽ là:
```
https://YOUR_USERNAME.github.io/REPO_NAME/
```

---

## 🎯 Netlify (Dễ nhất - Khuyến nghị cho người mới)

### Ưu điểm:
- ✅ **Cực kỳ dễ sử dụng** (kéo thả)
- ✅ **Miễn phí**
- ✅ **HTTPS tự động**
- ✅ **Deploy tự động** khi push code
- ✅ **Tên miền tùy chỉnh**

### Cách Deploy:

#### Bước 1: Đăng ký Netlify

1. Vào [netlify.com](https://www.netlify.com)
2. Click **"Sign up"** → Chọn **"GitHub"** (khuyến nghị)
3. Cho phép Netlify truy cập GitHub

#### Bước 2: Deploy

**Cách 1: Kéo thả (Drag & Drop) - Nhanh nhất**

1. Vào [app.netlify.com/drop](https://app.netlify.com/drop)
2. Kéo thả **toàn bộ thư mục dự án** vào
3. Đợi upload xong
4. Netlify sẽ tự động tạo URL cho bạn!

**Cách 2: Kết nối với GitHub**

1. Vào [app.netlify.com](https://app.netlify.com)
2. Click **"Add new site"** → **"Import an existing project"**
3. Chọn **"GitHub"**
4. Chọn repository của bạn
5. Click **"Deploy site"**
6. Netlify sẽ tự động deploy và cập nhật khi bạn push code mới

#### Bước 3: Cấu hình (Tùy chọn)

1. Vào **"Site settings"** → **"Change site name"**
2. Đổi tên site (ví dụ: `my-christmas-tree`)
3. URL sẽ thành: `https://my-christmas-tree.netlify.app`

---

## ⚡ Vercel (Nhanh - Tốt cho Performance)

### Ưu điểm:
- ✅ **Miễn phí**
- ✅ **Rất nhanh** (CDN toàn cầu)
- ✅ **HTTPS tự động**
- ✅ **Deploy tự động**

### Cách Deploy:

1. Vào [vercel.com](https://vercel.com)
2. Đăng nhập bằng GitHub
3. Click **"Add New"** → **"Project"**
4. Chọn repository của bạn
5. Click **"Deploy"**
6. Xong! URL sẽ có dạng: `https://your-project.vercel.app`

---

## 🔥 Firebase Hosting (Google)

### Ưu điểm:
- ✅ **Miễn phí** (10GB storage, 360MB/day bandwidth)
- ✅ **HTTPS tự động**
- ✅ **CDN của Google**
- ✅ **Tích hợp với Firebase services**

### Cách Deploy:

#### Bước 1: Cài Firebase CLI

```bash
npm install -g firebase-tools
```

#### Bước 2: Đăng nhập

```bash
firebase login
```

#### Bước 3: Khởi tạo Project

```bash
# Trong thư mục dự án
firebase init hosting
```

Chọn:
- **"Use an existing project"** hoặc tạo mới
- **Public directory:** `.` (dấu chấm)
- **Single-page app:** `No`
- **Overwrite index.html:** `No`

#### Bước 4: Deploy

```bash
firebase deploy --only hosting
```

URL sẽ có dạng: `https://YOUR-PROJECT-ID.web.app`

---

## 🌊 Surge.sh (Đơn giản nhất)

### Ưu điểm:
- ✅ **Miễn phí**
- ✅ **Cực kỳ đơn giản** (1 lệnh)
- ✅ **HTTPS tự động**

### Cách Deploy:

#### Bước 1: Cài Surge

```bash
npm install -g surge
```

#### Bước 2: Deploy

```bash
# Trong thư mục dự án
surge
```

Lần đầu sẽ yêu cầu:
- Email: nhập email của bạn
- Password: tạo password
- Project: nhấn Enter (dùng tên mặc định)
- Domain: nhấn Enter (sẽ tạo domain ngẫu nhiên)

URL sẽ có dạng: `https://random-name.surge.sh`

#### Đổi tên domain:

```bash
surge . your-custom-name.surge.sh
```

---

## ⚠️ Lưu Ý Quan Trọng

### 1. Camera chỉ hoạt động trên HTTPS

- ✅ GitHub Pages: **HTTPS tự động**
- ✅ Netlify: **HTTPS tự động**
- ✅ Vercel: **HTTPS tự động**
- ✅ Firebase: **HTTPS tự động**
- ✅ Surge: **HTTPS tự động**

**Lưu ý:** Nếu deploy lên server HTTP thông thường, camera sẽ **KHÔNG hoạt động**.

### 2. CORS và Ảnh

- Ảnh từ thư mục `images/` sẽ hoạt động bình thường
- Ảnh từ URL khác phải cho phép CORS
- Nếu ảnh không load, kiểm tra Console (F12)

### 3. Tối ưu Performance

**Trước khi deploy:**
- Nén ảnh trong thư mục `images/` (dùng [TinyPNG](https://tinypng.com/))
- Xóa các file không cần thiết
- Giảm số lượng particles nếu site chạy chậm

### 4. Cập nhật Code

**GitHub Pages:**
- Push code mới lên GitHub
- Đợi 1-2 phút để cập nhật

**Netlify/Vercel:**
- Tự động cập nhật khi push code
- Hoặc kéo thả lại folder mới

**Surge:**
- Chạy lại lệnh `surge` trong thư mục mới

### 5. Tên Miền Tùy Chỉnh (Custom Domain)

Tất cả các dịch vụ trên đều hỗ trợ custom domain miễn phí:

**GitHub Pages:**
1. Settings → Pages → Custom domain
2. Nhập domain của bạn
3. Cấu hình DNS theo hướng dẫn

**Netlify:**
1. Site settings → Domain management
2. Add custom domain
3. Làm theo hướng dẫn

---

## 📊 So Sánh Các Dịch Vụ

| Dịch vụ | Độ khó | Tốc độ | Tự động deploy | Custom domain |
|---------|--------|--------|----------------|---------------|
| GitHub Pages | ⭐⭐ | ⭐⭐⭐ | ❌ | ✅ |
| Netlify | ⭐ | ⭐⭐⭐ | ✅ | ✅ |
| Vercel | ⭐ | ⭐⭐⭐⭐ | ✅ | ✅ |
| Firebase | ⭐⭐ | ⭐⭐⭐ | ⚠️ | ✅ |
| Surge | ⭐ | ⭐⭐ | ❌ | ❌ |

---

## 🎯 Khuyến Nghị

- **Người mới:** Dùng **Netlify** (kéo thả là xong)
- **Đã có GitHub:** Dùng **GitHub Pages** (tích hợp tốt)
- **Cần tốc độ:** Dùng **Vercel**
- **Cần đơn giản:** Dùng **Surge.sh**

---

## 🔗 Ví Dụ URL Sau Khi Deploy

Sau khi deploy, bạn sẽ có URL dạng:

```
GitHub Pages:
https://yourname.github.io/christmas-tree/christmas_tree_touch&gesture.html

Netlify:
https://your-project.netlify.app/christmas_tree_touch&gesture.html

Vercel:
https://your-project.vercel.app/christmas_tree_touch&gesture.html

Firebase:
https://your-project.web.app/christmas_tree_touch&gesture.html

Surge:
https://your-project.surge.sh/christmas_tree_touch&gesture.html
```

---

## 💡 Tips

1. **Test trước khi share:** Đảm bảo mọi thứ hoạt động trên mobile
2. **Chia sẻ URL:** Copy URL và gửi cho bạn bè
3. **QR Code:** Tạo QR code từ URL để dễ truy cập trên mobile
4. **Social Media:** Có thể embed vào Facebook, Twitter

---

**Chúc bạn deploy thành công! 🎄🚀**

