# Bài tập 2 – Khởi tạo User thường và thiết lập Sudoers


### 1. Đăng nhập vào Droplet bằng root

```bash
ssh -i ~/.ssh/id_ed25519 root@<IP_DROPLET>
```

### 2. Tạo user `devops`

```bash
adduser devops
```

Điền mật khẩu và các thông tin yêu cầu (có thể Enter bỏ qua phần không bắt buộc).

### 3. Thêm `devops` vào nhóm sudo

```bash
usermod -aG sudo devops
```

### 4. Sao chép SSH Key từ root sang devops

```bash
sudo rsync --archive --chown=devops:devops ~/.ssh /home/devops/
```

### 5. Phân quyền thư mục `.ssh`

```bash
chmod 700 /home/devops/.ssh
chmod 600 /home/devops/.ssh/authorized_keys
```

---

## Kiểm tra

**Từ máy cá nhân**, đăng nhập bằng user `devops`:

```bash
ssh -i ~/.ssh/id_ed25519 devops@<IP_DROPLET>
```

Sau khi vào, kiểm tra quyền sudo:

```bash
sudo whoami
```

Kết quả mong đợi:

```
root
```

---

## Kết quả

| | |
|--|--|
| **User tạo** | `devops` |
| **Nhóm** | `sudo` |
| **Lệnh kết nối** | `ssh -i ~/.ssh/id_ed25519 devops@<IP>` |

> 📸 Chụp màn hình Terminal hiển thị kết quả `sudo whoami` → `root`, lưu vào `screenshots/`.
