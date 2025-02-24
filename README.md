# 📚 **Hướng Dẫn Quy Tắc Viết Mã Dự Án - Toàn Diện, Cụ Thể & Chuyên Nghiệp**

---

## ⚙️ **Yêu cầu môi trường & Hướng dẫn cài đặt**

### 🔧 **Phiên bản yêu cầu:**
- **Node.js:** v20.17.0
- **pnpm:** v9.9.0
- **Trình duyệt hỗ trợ:** Chrome, Firefox, Edge (phiên bản mới nhất)

### 💻 **Cách cài đặt Node.js**

#### 🔵 **Trên Windows:**
```bash
choco install nodejs-lts
```

#### 🍏 **Trên macOS:**
```bash
brew install node@20
```

#### 🐧 **Trên Linux (Ubuntu/Debian):**
```bash
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt-get install -y nodejs
```

### 📦 **Cách cài đặt pnpm**
```bash
npm install -g pnpm@9.9.0
```

### 🚀 **Khởi chạy dự án**
```bash
pnpm install
pnpm dev
```

---

## 📂 **Cấu trúc thư mục & Quy tắc đặt tên (Cập nhật theo hình cung cấp)**

### 🔠 **Quy tắc chung:**
- **Tên thư mục:** `kebab-case`, số nhiều.
- **Tên file:** `kebab-case` (ví dụ: `user-profile.ts`).
- **Component:** PascalCase (ví dụ: `UserProfile`).
- **Interface & Type:** PascalCase (ví dụ: `UserProfileResponse`).
- **Sub-component:** `_components` chứa các thành phần con.
- **Hook:** `useXyz` (ví dụ: `useUserProfile`).
- **Trang:** `page-name-page.tsx` (ví dụ: `welcome-page.tsx`).
- **Layout:** `layout-name-layout.tsx` (ví dụ: `main-layout.tsx`).
- **Utils:** `[functionality].util.ts` (ví dụ: `format.util.ts`).
- **Libs:** `[functionality].lib.ts` (ví dụ: `format-string.lib.ts`).

### 📁 **Cấu trúc thư mục chi tiết (theo hình đã cung cấp):**
```
├── src/
│   └── app/
│       ├── apis/
│       │   └── users/
│       │       ├── command/
│       │       │   ├── protos/
│       │       │   └── user.command.api.ts
│       │       └── query/
│       │           ├── protos/
│       │           └── user.query.api.ts
│       │
│       ├── assets/
│       │   ├── images/
│       │   └── svgs/
│       │
│       ├── components/
│       │   └── my-button/
│       │       ├── my-button-component.module.scss
│       │       ├── my-button-component.tsx
│       │       └── index.ts
│       │
│       ├── configs/
│       │   ├── http-status-code.config.ts
│       │   ├── message.config.ts
│       │   ├── routes.config.ts
│       │   └── tanstack-key.config.ts
│       │
│       ├── constants/
│       │   └── file.constant.ts
│       │
│       ├── errors/
│       │   └── error-boundary-handlers/
│       │       └── error-boundary-handlers.tsx
│       │
│       ├── hooks/
│       │   └── use-responsive.tsx
│       │
│       ├── layouts/
│       │   └── main-layout/
│       │       ├── main-layout.module.scss
│       │       ├── main-layout.tsx
│       │       └── index.ts
│       │
│       ├── pages/
│       │   ├── errors/
│       │   │   └── error-404-page/
│       │   │       ├── error-404-page.module.scss
│       │   │       ├── error-404-page.tsx
│       │   │       └── index.ts
│       │   ├── welcome-page/
│       │   │   ├── welcome-page.module.scss
│       │   │   ├── welcome-page.tsx
│       │   │   └── index.ts
│       │
│       ├── routes/
│       │   └── app-route.tsx
│       │
│       ├── shared/
│       │   └── user-example.shared.ts
│       │
│       ├── types/
│       │   ├── commons/
│       │   │   ├── config-lang/
│       │   │   └── helpdesk/
│       │   ├── icons/
│       │   │   ├── requests/icon.type.ts
│       │   │   └── responses/icon.type.ts
│       │   └── menu/
│       │
│       ├── utils/
│       │   ├── api.util.ts
│       │   ├── format.util.ts
│       │   └── string.util.ts
│       │
│       └── query-client.ts
│
└── App.tsx
```

### 📝 **Phân tích cấu trúc thư mục:**
- ✅ **apis/**: Tổ chức đúng theo tiêu chuẩn với thư mục `command` và `query`, mỗi phần đều chứa `protos` và file API tương ứng.
- ✅ **assets/**: Chia rõ ràng giữa `images/` và `svgs/`.
- ✅ **components/**: Mỗi component nằm trong thư mục riêng, có file SCSS và `index.ts` để export.
- ✅ **configs/**: Tên file theo chuẩn `kebab-case`, kết thúc bằng `.config.ts`.
- ✅ **constants/**: Lưu trữ hằng số với tên file rõ ràng (`file.constant.ts`).
- ✅ **errors/**: Xử lý lỗi với cấu trúc rõ ràng, hỗ trợ `error-boundary-handlers`.
- ✅ **hooks/**: Tên hook tuân theo quy tắc `use-xyz`.
- ✅ **layouts/**: Bố cục rõ ràng với file SCSS và `index.ts`.
- ✅ **pages/**: Mỗi trang có thư mục riêng, file chính `page-name.tsx` và SCSS tương ứng.
- ✅ **routes/**: Cấu hình định tuyến tập trung trong `app-route.tsx`.
- ✅ **shared/**: Chứa mã nguồn dùng chung (`user-example.shared.ts`).
- ✅ **types/**: Tổ chức rõ ràng, phân tách `requests`, `responses`.
- ✅ **utils/**: Các hàm tiện ích được đặt tên theo chuẩn `[functionality].util.ts`.

---

📌 **Tài liệu đã được điều chỉnh với cấu trúc thư mục cụ thể theo hình ảnh đã cung cấp, giữ nguyên nội dung cũ và loại bỏ phần khuyến nghị theo yêu cầu.** 🚀✨
