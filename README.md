# 📚 **Comprehensive Project Code Style Guide**

---

## 📡 **APIs**

### 🔧 **File Structure**
- **Folder naming:** `kebab-case`, plural (e.g., `users`).
- **Subfolders:**
  - `query/` and `command/`
    - `protos/`: contains generated gRPC files.
    - API files named as `singular.[query|command].api.ts`.
    - **Examples:**
      - `user.query.api.ts` → export as `userQueryApi`.
      - `user-role.command.api.ts` → export as `userRoleCommandApi`.

### 📝 **Coding Rules**
- **Export naming:** Use `camelCase` based on file name.
- **Data parameters:**
  - `body`: main data payload.
  - `filters`: pagination and filtering.
- **Method naming:** Must match gRPC definitions.
- **Type definitions:** All parameters must have corresponding `interface` definitions in `types/`.

### 💡 **Example:**
```typescript
export const userQueryApi = async (filters: UserFilters): Promise<UserResponse> => {
  return grpcClient.userQuery(filters);
};
```

---

## 🖼️ **Assets**

### 🔧 **File Structure**
- **`images/`**
  - `bgs/`: background images.
  - `icons/`: icon assets.
- **`svgs/`**: SVG files.

### 📝 **Naming Rules**
- Files should follow `kebab-case` (e.g., `user-avatar.png`, `background-login.jpg`).

---

## 🧩 **Components**

### 🔧 **File Structure**
- **Folder:** `kebab-case` descriptive names.
- **File naming:**
  - `[component-name]-component.tsx`
  - SCSS file: `[component-name]-component.module.scss`
  - `index.ts`: `export default` the component.
  - `_components/`: nested subcomponents.

### 📝 **Coding Rules**
- Default exports with `function` declarations.
- Descriptive naming for props and components.
- Use props destructuring.

### 💡 **Example:**
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

## ⚙️ **Configuration**

### 🔧 **File Structure**
- **Folder:** `kebab-case` plural (if applicable).
- **File:** `kebab-case` + `config` suffix.

### 📝 **Naming Rules**
- Export constants in `UPPER_SNAKE_CASE`.

### 💡 **Example:**
```typescript
export const COMMON_CONFIG = {
  LOGO: 'well365-logo',
  BACKGROUND_MENU_MORE: 'well365-bg-menu-more'
};
```

---

## 🎯 **Constants**

### 🔧 **File Structure**
- **Folder & File:** Use `kebab-case`.

### 📝 **Usage:**
- Use for static values shared across the project.

---

## ⚡ **Error Handling**

### 🔧 **File Structure**
- **Folder:** `kebab-case` plural.
- **File:** `kebab-case` singular.

### 📝 **Coding Rules**
- Default exports.
- Clear and descriptive naming.
- Props destructuring where applicable.

---

## 🔄 **Custom Hooks**

### 🔧 **File Structure**
- **Folder:** `kebab-case` plural.
- **File:** `use-[functionality].ts`.

### 📝 **Coding Rules**
- Function names follow `useXyz` convention.
- Default function declarations.
- Props destructuring.

### 💡 **Example:**
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

### 🔧 **File Structure**
- **Folder:** `kebab-case` descriptive.
- **File:** `[layout-name]-layout.tsx`.
- SCSS: `[layout-name]-layout.module.scss`.
- `index.ts`: `export default` layout.

### 📝 **Coding Rules**
- Export as default function.
- Clear naming and props destructuring.

### 💡 **Example:**
```tsx
export default function MainLayout({ children }: { children: React.ReactNode }) {
  return <div className="main-layout">{children}</div>;
}
```

---

## 🔌 **Libraries (Libs)**

### 🔧 **File Structure**
- **Folder:** `kebab-case` plural.
- **File:** `[utility-name].util.ts`.

### 💡 **Example:**
```typescript
export function formatString(str: string): string {
  return str.trim().toLowerCase();
}
```

---

## 🌐 **Routing**

### 🔧 **File Structure**
- **Folder:** `kebab-case` plural.
- **File:** `app-router.tsx` (main router).

### 📝 **Usage:**
- Use separate routers for modules if necessary.

### 💡 **Example:**
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

### 🔧 **File Structure**
- **Folder:** `kebab-case` plural.
- **File:** `[entity-name].type.ts`.
- Subfolders: `responses/`, `request/`.

### 📝 **Naming Rules**
- Interfaces and types should match API method names.

### 💡 **Example:**
```typescript
export interface UserResponse {
  id: string;
  name: string;
}
```

---

## 📦 **Query Client Configuration**
```typescript
import { QueryClient } from '@tanstack/react-query';

export const queryClient = new QueryClient();
```

---

## ✍️ **Commenting Standards**
- Clear, descriptive comments explaining code logic.

### 💡 **Example:**
```typescript
// Fetch user profile by ID
const userProfile = await getUserProfile(id);
```

---

## 🛡️ **ESLint Configuration**
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
    'no-undef': 'off',
    '@typescript-eslint/no-require-imports': 'off',
    'prettier/prettier': 'warn',
    'react/prop-types': 'off',
    'react/react-in-jsx-scope': 'off',
    '@typescript-eslint/explicit-module-boundary-types': 'off',
    '@typescript-eslint/no-explicit-any': 'warn',
    '@typescript-eslint/no-unused-vars': ['warn', { argsIgnorePattern: '^_' }],
    'react-hooks/rules-of-hooks': 'warn',
    'jsx-a11y/anchor-is-valid': 'warn'
  }
};
```

---

## 🎉 **Final Notes**

📌 Adhering to these comprehensive guidelines ensures a clean, maintainable, and scalable codebase. Let's code professionally! 🚀✨
