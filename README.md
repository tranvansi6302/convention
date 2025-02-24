# 📚 **Hướng Dẫn Quy Tắc Viết Mã Dự Án - Toàn Diện, Cụ Thể & Chuyên Nghiệp**

---

## 📂 **Cấu trúc thư mục & Quy tắc đặt tên**

### 🔠 **Quy tắc chung:**
- **Tên thư mục:** `kebab-case`, số nhiều.
- **Tên file:**
  - Theo `kebab-case` (ví dụ: `user-profile.ts`).
  - Tệp TypeScript kết thúc bằng `.ts` hoặc `.tsx` (nếu có JSX).
- **Component:** PascalCase (ví dụ: `UserProfile`).
- **Interface & Type:** PascalCase (ví dụ: `UserProfileResponse`).
- **Thư mục có sub-component:** Thêm `_components` chứa các thành phần con.

### 📁 **Ví dụ cấu trúc thư mục:**
```
├── apis/
│   ├── users/
│   │   ├── query/
│   │   │   ├── protos/
│   │   │   └── user.query.api.ts
│   │   ├── command/
│   │   │   ├── protos/
│   │   │   └── user-role.command.api.ts
├── assets/
│   ├── images/
│   │   ├── bgs/
│   │   └── icons/
│   └── svgs/
├── components/
│   └── user-profile-component/
│       ├── user-profile-component.tsx
│       ├── user-profile-component.module.scss
│       └── index.ts
├── config/
│   └── api.config.ts
├── constants/
│   └── app.constants.ts
├── errors/
│   └── not-found.tsx
├── hooks/
│   └── use-user-profile.ts
├── layouts/
│   └── main-layout/
│       ├── main-layout.tsx
│       ├── main-layout.module.scss
│       └── index.ts
├── libs/
│   └── format-string.lib.ts
├── pages/
│   └── home-page/
│       ├── home-page.tsx
│       ├── home-page.module.scss
│       └── index.ts
├── routers/
│   └── app-router.tsx
├── shared/
│   └── helpers.ts
├── types/
│   └── users/
│       ├── responses/user.type.ts
│       └── requests/user-request.type.ts
├── utils/
│   └── date.util.ts
└── query-client.ts
```

---

## 📡 **APIs**

### 🔧 **Cấu trúc file**
- **Tên thư mục:** `kebab-case`, số nhiều (ví dụ: `users`).
- **Bên trong:**
  - `query/` và `command/`:
    - `protos/`: chứa file gRPC.
    - File API: `tên(số ít).[query|command].api.ts` (ví dụ: `user.query.api.ts`).

### 📝 **Quy tắc code**
- **Export name:** CamelCase (ví dụ: `userQueryApi`).
- **Tham số:** `body` và `filters`.
- **Tên phương thức:** Trùng với gRPC.
- **Type:** Interface trùng tên phương thức trong `types/`.

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
- `kebab-case` (ví dụ: `user-avatar.png`).

### 💡 **Ví dụ thư mục:**
```
assets/
├── images/
│   ├── bgs/
│   │   └── login-background.jpg
│   └── icons/
│       └── user-avatar.png
└── svgs/
    └── logo.svg
```

---

## 🧩 **Components**

### 🔧 **Cấu trúc file**
- **Thư mục:** `kebab-case`.
- **File:**
  - `[component-name]-component.tsx`
  - `[component-name]-component.module.scss`
  - `index.ts`: `export default` component.

### 📝 **Quy tắc code**
- `export default function` declaration.
- Props destructuring.
- Tên rõ ràng, dễ hiểu.

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

### 📝 **Quy tắc code**
- Tên file: `kebab-case` + `config`.
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
- Tên rõ ràng, props destructuring.

### 💡 **Ví dụ:**
```tsx
export default function NotFoundPage() {
  return <h1>404 - Page Not Found</h1>;
}
```

---

## 🔄 **Hooks**

### 📝 **Quy tắc code**
- Tên file: `use-[feature].ts`.
- Tên hook: `useXyz`.
- Props destructuring.

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

## 🛡️ **Cấu Hình ESLint**

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

---

📌 **Tài liệu đã được bổ sung với các ví dụ cụ thể, cấu trúc thư mục minh họa và quy tắc rõ ràng cho từng mục.** 🚀✨
