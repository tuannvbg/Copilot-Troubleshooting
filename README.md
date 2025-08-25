# 🛠️ Copilot-Troubleshooting  
Fixing Microsoft Copilot timeout and launch errors on Windows 11 — includes rare registry workaround and PowerShell cleanup. *(Việt - Anh)*

---

## 🔍 Kiểm tra Registry trước khi sửa | Check Registry Before Fixing

Trước khi áp dụng bất kỳ giải pháp nào, hãy kiểm tra đường dẫn registry sau:  
Before applying any fix, check this registry path:

```
HKEY_CURRENT_USER\Software\Policies\Microsoft\Windows
```

👉 Nếu **không thấy thư mục `WindowsCopilot`**, thì rất có thể đây là nguyên nhân khiến Copilot bị treo hoặc báo lỗi:  
👉 If the `WindowsCopilot` folder is missing, this may be the reason Copilot fails to launch or times out:

> `"Copilot error: The request took longer than expected. Please ensure you're online and try again."`

✅ Trong trường hợp đó, bạn có thể áp dụng giải pháp sau để khôi phục Copilot.  
✅ In that case, you can apply the following fix to restore Copilot.

---

## ✅ Giải pháp từng bước | Step-by-step Fix

### 🔧 1. Tạo key registry | Create Registry Key

Tạo thủ công đường dẫn sau:  
Manually create this registry path:

```
HKEY_CURRENT_USER\Software\Policies\Microsoft\Windows\WindowsCopilot
```

Thêm giá trị DWORD:  
Add a DWORD value:

```
TurnOffWindowsCopilot = 0
```

📸 *Ảnh minh họa: Registry thiếu key Copilot*  
📸 *Screenshot: Registry missing Copilot key*

![Registry missing Copilot key](https://github.com/tuannvbg/Copilot-Troubleshooting/blob/main/screenshots/missing-copilot-key.png?raw=true)

---

### 🔧 2. Gỡ sạch Copilot bằng PowerShell | Remove Copilot via PowerShell

Mở PowerShell dưới quyền admin và chạy:  
Open PowerShell as admin and run:

```powershell
Get-AppxPackage *WindowsCopilot* | Remove-AppxPackage
```

💡 Cách này gỡ sạch hơn so với xóa qua Settings  
💡 This removes the app more thoroughly than uninstalling via Settings

---

### 🔧 3. Cài lại Copilot từ Microsoft Store | Reinstall from Microsoft Store  
🔧 4. Khởi động lại máy sau mỗi bước | Restart PC after each step

📸 *Ảnh minh họa lỗi Copilot*  
📸 *Screenshot: Copilot timeout error*

![Copilot timeout error](https://github.com/tuannvbg/Copilot-Troubleshooting/blob/main/screenshots/copilot-timeout-error.png?raw=true)

---

## 🔧 Trước và Sau khi Fix | Before and After Fix

| Trước khi fix | Sau khi fix |
|---------------|-------------|
| ![Copilot timeout error](https://github.com/tuannvbg/Copilot-Troubleshooting/blob/main/screenshots/copilot-timeout-error.png?raw=true) | ![Post-Fix Copilot Welcome Screen](https://github.com/tuannvbg/Copilot-Troubleshooting/blob/main/screenshots/copilot-welcome.png?raw=true) |

---

## 👋 Giao diện sau khi fix lỗi | Post-Fix Copilot Welcome Screen

> Sau khi áp dụng bản sửa lỗi, Copilot đã hoạt động bình thường và chào đón người dùng như thế này.  
> After applying the fix, Copilot greeted the user with this welcome screen.

![Copilot đã hoạt động trở lại](https://github.com/tuannvbg/Copilot-Troubleshooting/blob/main/screenshots/copilot-welcome.png?raw=true)

---

## 🙌 Credits | Ghi nhận đóng góp

Special thanks to **Tuấn from Bắc Ninh, Vietnam** — the first to discover and share this rare fix.  
Cảm ơn đặc biệt tới **Tuấn từ Bắc Ninh** — người đầu tiên phát hiện và chia sẻ cách khắc phục hiếm này.  
Your contribution helps the entire Copilot community!

---

## 📄 License | Giấy phép sử dụng

This project is licensed under the MIT License.
