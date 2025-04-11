
# 🔐 Hướng Dẫn Cấu Hình Lại Git để Dùng Personal Access Token (PAT) với HTTPS

## ✅ Bước 1: Kiểm Tra Remote URL

```bash
git remote -v
```

Ví dụ kết quả:

```
origin  https://github.com/your-username/your-repo.git (fetch)
origin  https://github.com/your-username/your-repo.git (push)
```

Nếu là SSH (dạng `git@github.com:...`), chuyển sang HTTPS:

```bash
git remote set-url origin https://github.com/your-username/your-repo.git
```

---

## ✅ Bước 2: Xoá Cache Thông Tin Đăng Nhập Cũ

```bash
git credential-cache exit
```

Hoặc:

```bash
git credential reject
```

---

## ✅ Bước 3: Thử Kết Nối Lại để Git Yêu Cầu Nhập PAT

```bash
git pull
```

Khi được hỏi:

- **Username**: nhập GitHub username
- **Password**: dán **PAT** vào

> ⚠️ PAT là chuỗi thay thế mật khẩu GitHub, bạn có thể tạo ở: [https://github.com/settings/tokens](https://github.com/settings/tokens)

---

## ✅ Bước 4 (Tuỳ Chọn): Ghi Nhớ PAT Để Không Cần Nhập Lại

### Trên Windows:

```bash
git config --global credential.helper manager
```

### Trên macOS:

```bash
git config --global credential.helper osxkeychain
```

### Trên Linux hoặc cache tạm thời:

```bash
git config --global credential.helper cache
```

---

## ✅ Bước 5: Kiểm Tra Bằng Lệnh Push

```bash
git push
```

Nếu không có lỗi và đẩy code thành công thì bạn đã cấu hình đúng.
