tôi có các rule code như sau bạn hãy tổng hợp lại cho chuyên nghiệp và bổ sung các ví dụ đơn giản hoặc bỏ sung gì đó bạn cho là thiếu vào và tôi muốn viết lại thành code markdown trong git
* apis 
- Cấu trúc file
+ tên thư mục kebab-case, số nhiều ví dụ users, bên trong có 2 thư mục chính query và command bên trong query và command đều có thư mụcprotos nơi gen ra các grpc, và ngang cấp với protos là tên file
+ với các file thì tên (số ít).[query, command].api.ts ví dụ user.query.api, nếu tên có từ 2 chữ thì dấu (-), ví dụ user-role.command.api
- Rule code
+ export name, tên giống tên file bỏ dấu (.) theo quy tắc camelcase ví dụ user.query.api -> userQueryApi
+ Tham số dữ liệu vào body, các tham số khác liên quan đến phân trang lọc filters
+ Tên các phương thức giống với grpc trả về
+ Định nghĩa cụ thể các type trong thư mục types lưu ý có 1 tham số cũng phải định nghĩa interface và tên interface giống với tên phương thức

* các tài nguyên (thư mục asssets)
- Cấu trúc file
+ images ( chứa ảnh, icon dạng png, jpg...) bên trong chia ra bgs và icons
+ svgs chứa các file dạng svg
- Rule code
+ Tên file ảnhm icon đặt theo quy tắc kebab-case.

* components
- Cấu trúc file
+ tên thư mục kebab-case đặt có nghĩa
+ Tên file giống tên thư mục + component ví dụ my-button-component
+ file scss giống tên file + module ví dụ my-button-component.module.scss
+ file index export default tên file
+ đệ quy thư mục _components nếu có nhiều thành phần con
- Rule code
+ export default function declaration
+ Đặt tên rõ ràng dễ hiểu dài không thành vấn đề
+ Props desttructoring

import React from 'react';

interface ButtonProps {
  label: string;
}

export default function Button({ label }: ButtonProps): JSX.Element {
  return <button>{label}</button>;
}

* config
- cấu trúc file
+ tên thư mục (nếu có) kebab-case số nhiều
+ tên file kebab-case số ít (nếu liên quan đến tên thư mục, có thể đặt số nhiều nếu nó là file) + config
- Rule code
+ export name, tên đặt theo UPPER_SNAKE_CASE vídụ 

export const COMMON_KEY = {
    LOGO: 'well365-logo',
    BACKGROUND_MENU_MORE: 'well365-bg-menu-more'
}
* constants 
- cấu trúc file
+ tên thư mục (nếu có) kebab-case số nhiều
+ tên file kebab-case số ít(nếu liên quan đến tên thư mục,có thể đặt số nhiều nếu nó là file)

* errors (Liên quan đến các trang lỗi)
- cấu trúc file
+ Tên thư mục kebab-case (số nhiều) , tên file kebab-case số ít
- Rule code
+ export default
+ Đặt tên rõ ràng dễ hiểu dài không thành vấn đề
+ Props desttructoring
 

* hooks (chứa custom hooks)
- cấu trúc file
+ Tên thư mục kebab-case (số nhiều) , tên file kebab-case số ít(nếu liên quan đến trhư mục)
- Rule code
+ export default function declaration
+ Đặt tên theo quy tắc của hook
+ Props desttructoring

* layouts (chứa các layouts chính)
- Cấu trúc file
+ tên thư mục kebab-case đặt có nghĩa ví dụ main
+ Tên file giống tên thư mục + layout ví dụ main-layout
+ file scss giống tên file + module ví dụ main-layout.module.scss
+ file index export default tên file
+ đệ quy thư mục _components nếu có nhiều thành phần con
- Rule code
+ export default function declaration
+ Đặt tên rõ ràng dễ hiểu dài không thành vấn đề
+ Props desttructoring

* libs (chứa các helpdesks thư viện thứ 3)
+ Tên thư mục kebab-case (số nhiều) , tên file kebab-case số ít (nếu liên quan đến thư mục)
- Rule code
+ tên rõ ràng dễ hiểu


* layouts (chứa các layouts chính)
- Cấu trúc file
+ tên thư mục kebab-case đặt có nghĩa ví dụ welcome
+ Tên file giống tên thư mục + page ví dụ welcome-page
+ file scss giống tên file + module ví dụ welcome-page.module.scss
+ file index export default tên file
+ đệ quy thư mục _components nếu có nhiều thành phần con
- Rule code
+ export default function declaration
+ Đặt tên rõ ràng dễ hiểu dài không thành vấn đề
+ Props desttructoring

* routers
- Cấu trúc file
Tên thư mục kebab-case (số nhiều) , tên file kebab-case số ít (nếu liên quan đến trhư mục)
Rule code
+ app chứa toàn bộ router của dự án
+ Có thể tạo từng router riêng biệt cho tưng module

* shared
- Cấu trúc file
Tên thư mục kebab-case (số nhiều) , tên file kebab-case số ít (nếu liên quan đến trhư mục)

* types
- Cấu trúc file
+ Tên thư mục kebab-case (số nhiều) , tên file kebab-case số ít (nếu liên quan đến trhư mục) ví dụ users
+ Bên trong users ục responses và request và đặt tên theo kebab-case số ít + type ví dụ user.type , my-address.type

- Rule code
+ đặt tên các interface, các type rõ ràng dễ hiểu, với các responses request liên quan đến api thì nên đặt trùng với phương thức api

* libs (chứa các tiện ích)
+ Tên thư mục kebab-case (số nhiều) , tên file kebab-case số ít (nếu liên quan đến thư mục) + util ví dụ format-string.util
- Rule code
+ tên rõ ràng dễ hiểu


query-client.ts
- Cấu hình tanstack query

* QUy tắc comment
- Comment rõ ràng dễ hiểu 

* Rule eslint
module.exports = {
    root: true,
    parser: '@typescript-eslint/parser',
    parserOptions: {
        ecmaVersion: 2020,
        sourceType: 'module',
        ecmaFeatures: {
            jsx: true
        }
    },

    settings: {
        react: {
            version: 'detect'
        },
        'import/resolver': {
            typescript: {}
        }
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
}

