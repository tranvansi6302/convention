# 📚 **Hướng Dẫn Quy Tắc Viết Mã Dự Án - Toàn Diện, Chuyên Nghiệp & Cụ Thể**

---

## 📂 **Cấu trúc thư mục & Quy tắc đặt tên**

### 🔠 **Quy tắc chung:**
- **Tên thư mục:** `kebab-case`, số nhiều.
- **Tên file:**
  - Theo `kebab-case`.
  - Tệp TypeScript kết thúc bằng `.ts` hoặc `.tsx` (nếu có JSX).
- **Component:** PascalCase cho tên component.
- **Interface & Type:** PascalCase.

---

## 📡 **APIs**

### 🔧 **Cấu trúc file**
- **Tên thư mục:** `kebab-case`, số nhiều (ví dụ: `users`).
- **Bên trong:**
  - `query/` và `command/`:
    - `protos/`: chứa file gRPC được sinh ra.
    - File API: `tên(số ít).[query|command].api.ts`.

### 📝 **Quy tắc code**
- **Export name:** CamelCase, bỏ dấu `.` (ví dụ: `user.query.api` → `userQueryApi`).
- **Tham số:**
  - `body`: dữ liệu chính.
  - `filters`: phân trang, lọc.
- **Tên phương thức:** Trùng với gRPC.
- **Type:** Định nghĩa interface trong `types/`, trùng tên phương thức.

### 💡 **Ví dụ:**
```typescript
export const userQueryApi = async (filters: UserFilters): Promise<UserResponse> => {
  return grpcClient.userQuery(filters);
};
```

---

## 🖼️ **Assets**

### 🔧 **Cấu trúc file**
- **images/**:
  - `bgs/`: hình nền.
  - `icons/`: biểu tượng.
- **svgs/**: file SVG.

### 📝 **Quy tắc đặt tên**
- **Quy tắc:** `kebab-case` (ví dụ: `user-avatar.png`).

---

## 🧩 **Components**

### 🔧 **Cấu trúc file**
- **Thư mục:** `kebab-case` có nghĩa.
- **File:**
  - `[component-name]-component.tsx`
  - `[component-name]-component.module.scss`
  - `index.ts`: export mặc định.
  - `_components/`: chứa sub-component.

### 📝 **Quy tắc code**
- `export default function` declaration.
- **Props destructuring**.
- **Tên rõ ràng, dễ hiểu.**

### 💡 **Ví dụ:**
```tsx
import React from 'react';

interface ButtonProps {
  label: string;
}

export default function MyButtonComponent({ label }: ButtonProps): JSX.Element {
  return <button>{label}</button>;
}
```

---

## ⚙️ **Config**

### 🔧 **Cấu trúc file**
- **Tên file:** `kebab-case` + `config`.

### 📝 **Quy tắc code**
- Export name theo UPPER_SNAKE_CASE.

### 💡 **Ví dụ:**
```typescript
export const COMMON_KEY = {
  LOGO: 'well365-logo',
  BACKGROUND_MENU_MORE: 'well365-bg-menu-more'
};
```

---

## ❗ **Errors**

### 📝 **Quy tắc code**
- Export mặc định.
- Props destructuring.

---

## 🔄 **Hooks**

### 💡 **Ví dụ:**
```typescript
export default function useUserProfile(userId: string) {
  const [profile, setProfile] = useState(null);
  useEffect(() => {
    fetch(`/api/users/${userId}`).then(res => res.json()).then(setProfile);
  }, [userId]);
  return profile;
}
```

---

## 🏛️ **Layouts**

### 🔧 **Cấu trúc file**
- Tên file: `[layout-name]-layout.tsx`.
- SCSS: `[layout-name]-layout.module.scss`.

### 💡 **Ví dụ:**
```tsx
export default function MainLayout({ children }: { children: React.ReactNode }) {
  return <div className="main-layout">{children}</div>;
}
```

---

## 🔌 **Libs & Utils**

### 💡 **Ví dụ:**
```typescript
export function formatString(str: string): string {
  return str.trim().toLowerCase();
}
```

---

## 🌐 **Routers**

### 💡 **Ví dụ:**
```typescript
import { BrowserRouter as Router, Route } from 'react-router-dom';

export default function AppRouter() {
  return (
    <Router>
      <Route path="/home" component={HomePage} />
    </Router>
  );
}
```

---

## 🧬 **Types**

### 💡 **Ví dụ:**
```typescript
export interface UserResponse {
  id: string;
  name: string;
}
```

---

## 📦 **Query Client**

### 💡 **Ví dụ:**
```typescript
import { QueryClient } from '@tanstack/react-query';

export const queryClient = new QueryClient();
```

---

## 🛡️ **Cấu Hình ESLint - Quy Tắc & Cách Tránh Lỗi**

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

## ✍️ **Tiêu Chuẩn Comment**
- **Rõ ràng, súc tích, giải thích logic chính.**

### 💡 **Ví dụ:**
```typescript
// 📌 Lấy thông tin người dùng theo ID
const userProfile = await getUserProfile(id);
```

---

## 🎉 **Hoàn thiện!** 🚀

📌 **Tài liệu đã được cập nhật toàn diện với cấu trúc chi tiết, quy tắc rõ ràng và ví dụ minh họa cụ thể.** ✨
