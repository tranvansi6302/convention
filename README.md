# 📚 **Tài Liệu Hướng Dẫn Quy Tắc Viết Mã Dự Án - Chuyên Nghiệp & Chuẩn Hóa**

---

## 📖 **Giới thiệu**
Tài liệu này hướng dẫn chi tiết quy tắc viết mã, cấu trúc thư mục và tiêu chuẩn đặt tên cho dự án. Hướng dẫn phù hợp với các dự án sử dụng **Node.js**, **React (TypeScript)** và **pnpm** để đảm bảo chất lượng, khả năng mở rộng và dễ bảo trì.

---

## ⚙️ **Thiết lập môi trường**

### 🔧 **Phiên bản yêu cầu:**
- **Node.js:** v20.17.0
- **pnpm:** v9.9.0
- **Trình duyệt hỗ trợ:** Chrome, Firefox, Edge (phiên bản mới nhất)

### 💻 **Hướng dẫn cài đặt**

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

### 📦 **Cài đặt pnpm**
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
- **Thư mục:** `kebab-case`, số nhiều.
- **File:** `kebab-case` (ví dụ: `user-profile.ts`).
- **Component:** PascalCase (ví dụ: `UserProfile`).
- **Hook:** `useXyz` (ví dụ: `useUserProfile`).
- **Trang:** `page-name-page.tsx` (ví dụ: `welcome-page.tsx`).
- **Layout:** `layout-name-layout.tsx` (ví dụ: `main-layout.tsx`).
- **Utils:** `[functionality].util.ts` (ví dụ: `format.util.ts`).
- **Libs:** `[functionality].lib.ts` (ví dụ: `format-string.lib.ts`).

### 📁 **Cấu trúc thư mục chi tiết:**
```
├── src/
│   └── app/
│       ├── apis/
│       │   └── users/
│       │       ├── command/
│       │       │   └── user.command.api.ts
│       │       └── query/
│       │           └── user.query.api.ts
│       │
│       ├── assets/
│       │   ├── images/
│       │   └── svgs/
│       │
│       ├── components/
│       │   └── my-button/
│       │       ├── my-button-component.tsx
│       │       ├── my-button-component.module.scss
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
│       │       ├── main-layout.tsx
│       │       ├── main-layout.module.scss
│       │       └── index.ts
│       │
│       ├── pages/
│       │   ├── errors/
│       │   │   └── error-404-page/
│       │   │       ├── error-404-page.tsx
│       │   │       ├── error-404-page.module.scss
│       │   │       └── index.ts
│       │   └── welcome-page/
│       │       ├── welcome-page.tsx
│       │       ├── welcome-page.module.scss
│       │       └── index.ts
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

---

## 🛡️ **Cấu hình ESLint & Quy tắc clean code**

### ⚡ **Cấu hình ESLint:**
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

### 📝 **Các quy tắc ESLint quan trọng và cách tránh cảnh báo:**
- ⚡ **`no-undef`:** Tránh sử dụng biến chưa được khai báo.
- ⚡ **`@typescript-eslint/no-explicit-any`:** Không sử dụng kiểu `any`. Thay vào đó, hãy xác định kiểu cụ thể.
- ⚡ **`@typescript-eslint/no-unused-vars`:** Xóa các biến không sử dụng hoặc thêm dấu gạch dưới (`_`) trước tên biến.
- ⚡ **`react/react-in-jsx-scope`:** Không cần import `React` nếu sử dụng React 17+.
- ⚡ **`react-hooks/rules-of-hooks`:** Gọi hook đúng vị trí (trong component hoặc custom hook, không trong vòng lặp hoặc điều kiện).
- ⚡ **`prettier/prettier`:** Cấu hình Prettier để đảm bảo định dạng mã nhất quán.
- ⚡ **`jsx-a11y/anchor-is-valid`:** Sử dụng thuộc tính `href` hợp lệ cho thẻ `<a>` hoặc thay thế bằng `<button>` nếu cần.

### 🚫 **Quy tắc comment & Clean Code:**
- ✅ **Comment rõ ràng:** Giải thích lý do hơn là cách làm.
- ✅ **Tránh comment không cần thiết:** Mã tự giải thích không cần comment.
- ✅ **TODO & FIXME:**
  ```typescript
  // TODO: Thêm chức năng đăng nhập
  // FIXME: Sửa lỗi hiển thị giao diện trên di động
  ```
- ✅ **Hàm nhỏ gọn, rõ ràng:** Một hàm chỉ nên thực hiện một nhiệm vụ.
- ✅ **Tên biến, hàm có ý nghĩa:** Ví dụ `getUserProfile()` thay vì `getData()`.
- ✅ **Tránh magic numbers:**
  ```typescript
  const MAX_RETRIES = 3;
  ```
- ✅ **Code nhất quán:** Sử dụng ESLint để giữ phong cách mã nhất quán.
- ✅ **Tách logic phức tạp:** Nếu hàm quá dài, chia nhỏ thành các hàm con.

---

📌 **Tài liệu đã được cập nhật với cấu hình ESLint chi tiết, các quy tắc được định nghĩa trong ESLint để tránh cảnh báo và quy tắc clean code, đảm bảo mã nguồn dễ đọc, dễ bảo trì và chất lượng cao.** 🚀✨
