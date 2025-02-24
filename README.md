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

## 📂 **Cấu trúc thư mục & Quy tắc đặt tên**

### 🔠 **Quy tắc chung:**
- **Tên thư mục:** `kebab-case`, số nhiều.
- **Tên file:** `kebab-case` (ví dụ: `user-profile.ts`).
- **Component:** PascalCase (ví dụ: `UserProfile`).
- **Interface & Type:** PascalCase (ví dụ: `UserProfileResponse`).
- **Sub-component:** `_components` chứa các thành phần con.
- **Hook:** `useXyz` (ví dụ: `useUserProfile`).
- **Trang:** `page-name-page.tsx` (ví dụ: `home-page.tsx`).
- **Layout:** `layout-name-layout.tsx` (ví dụ: `main-layout.tsx`).
- **Utils:** `[functionality].util.ts` (ví dụ: `date.util.ts`).
- **Libs:** `[functionality].lib.ts` (ví dụ: `format-string.lib.ts`).

### 📁 **Cấu trúc thư mục chi tiết:**
```
├── apis/                # Xử lý API
│   ├── users/           # API module 'users'
│   │   ├── query/       # Xử lý đọc dữ liệu
│   │   │   └── user.query.api.ts
│   │   ├── command/     # Xử lý ghi dữ liệu
│   │   │   └── user-role.command.api.ts
│   │   └── protos/      # File gRPC
│
├── assets/              # Tài nguyên dự án
│   ├── images/          # Hình ảnh
│   │   ├── bgs/         # Backgrounds
│   │   └── icons/       # Icons
│   └── svgs/            # File SVG
│
├── components/          # Thành phần UI
│   └── user-profile-component/
│       ├── user-profile-component.tsx
│       ├── user-profile-component.module.scss
│       └── index.ts
│
├── config/              # Cấu hình chung
│   └── api.config.ts
│
├── constants/           # Hằng số dùng chung
│   └── app.constants.ts
│
├── errors/              # Trang lỗi
│   └── not-found.tsx
│
├── hooks/               # Custom hooks
│   └── use-user-profile.ts
│
├── layouts/             # Bố cục giao diện
│   └── main-layout/
│       ├── main-layout.tsx
│       ├── main-layout.module.scss
│       └── index.ts
│
├── libs/                # Thư viện hỗ trợ
│   └── format-string.lib.ts
│
├── pages/               # Các trang chính
│   └── home-page/
│       ├── home-page.tsx
│       ├── home-page.module.scss
│       └── index.ts
│
├── routers/             # Cấu hình định tuyến
│   └── app-router.tsx
│
├── shared/              # Mã dùng chung
│   └── helpers.ts
│
├── types/               # Định nghĩa kiểu dữ liệu
│   └── users/
│       ├── responses/user.type.ts
│       └── requests/user-request.type.ts
│
├── utils/               # Hàm tiện ích
│   └── date.util.ts
│
└── query-client.ts      # Cấu hình TanStack Query
```

---

## 🛡️ **Cấu Hình ESLint & Cách Tránh Lỗi**

### ⚡ **Cấu hình ESLint**
```javascript
module.exports = {
  root: true,
  parser: '@typescript-eslint/parser',
  parserOptions: {
    ecmaVersion: 2020,
    sourceType: 'module',
    ecmaFeatures: { jsx: true }
  },
  settings: {
    react: { version: 'detect' },
    'import/resolver': { typescript: {} }
  },
  extends: [
    'eslint:recommended',
    'plugin:react/recommended',
    'plugin:@typescript-eslint/recommended',
    'prettier',
    'plugin:prettier/recommended'
  ],
  plugins: ['react', 'react-hooks', '@typescript-eslint', 'import', 'jsx-a11y', 'prettier'],
  rules: {
    'no-undef': 'error',
    '@typescript-eslint/no-require-imports': 'error',
    'prettier/prettier': 'warn',
    'react/prop-types': 'off',
    'react/react-in-jsx-scope': 'off',
    '@typescript-eslint/explicit-module-boundary-types': 'off',
    '@typescript-eslint/no-explicit-any': 'error',
    '@typescript-eslint/no-unused-vars': ['warn', { argsIgnorePattern: '^_' }],
    'react-hooks/rules-of-hooks': 'error',
    'jsx-a11y/anchor-is-valid': 'warn'
  }
};
```

### 🚫 **Giải thích & Cách tránh lỗi:**
- ❌ **Biến không sử dụng:** Thêm `_` trước tên biến.
- ❌ **Tránh `any`:** Dùng kiểu cụ thể (`string`, `number`).
- ❌ **Hook sai vị trí:** Gọi ở cấp cao nhất của component.
- ❌ **JSX không có React:** Không cần import React từ v17.
- ❌ **Thẻ `<a>` không hợp lệ:** Luôn thêm `href` hoặc dùng `button`.

---

## ✍️ **Quy tắc import/export & Tối ưu mã**

### 💡 **Import:**
```typescript
import { UserProfile } from '@/components/user-profile-component';
```
- ✅ **Dùng alias `@`** cho thư mục gốc.
- ✅ **Import từ `index.ts`** khi có.

### 💡 **Export:**
```typescript
export default function UserProfile() {}
export const USER_ROLE = 'admin';
```
- ✅ **Component:** Dùng export mặc định.
- ✅ **Hằng số & hàm tiện ích:** Dùng named export.

---

## 📝 **Quy tắc commit message**

### 📜 **Cấu trúc commit:**
```
type(scope): subject
```
- **type:** feat, fix, chore, refactor, docs.
- **scope:** phần bị ảnh hưởng (component, page, api).
- **subject:** mô tả ngắn gọn.

### 💡 **Ví dụ:**
```bash
feat(api): thêm chức năng đăng nhập
fix(component): sửa lỗi giao diện nút đăng ký
```

---

📌 **Tài liệu đã được cập nhật toàn diện với cấu trúc thư mục rõ ràng, hướng dẫn cài đặt, quy tắc ESLint, chuẩn import/export và quy tắc commit.** 🚀✨
