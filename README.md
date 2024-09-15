# mui와 github api 활용한 예제

## 사용할 api

```
https://api.github.com/search/users
: 유저 검색

쿼리 매개 변수
q: 서치키워드
per_page: 한 페이지에 보여질 아이템 수
page: 페이지 번호

https://api.github.com/users/{username}
: {username} 정보


https://api.github.com/users/minhanPark/repos?sort=updated&page=1&per_page=10
: 레포지토리 검색

sort: 정렬 기준(updated로 가장 최근에 수정한 순서대로 불러오기)
per_page: 한 페이지에 보여질 아이템 수
page: 페이지 번호
```

## 필요한 패키지 설치

```bash
# mui 사용 시 필요한 기본 패키지 설치
npm install @mui/material @emotion/react @emotion/styled
```

> [ 관련 문서 확인](https://mui.com/material-ui/getting-started/installation/)

```bash
# mui 아이콘 관련 패키지 설치
npm install @mui/icons-material
```

> [ 관련 문서 확인](https://mui.com/material-ui/getting-started/installation/#icons)

```bash
# 페이지 라우팅을 위한 패키지 설치
npm install react-router-dom
```

> [ 관련 문서 확인](> [ 관련 문서 확인](https://mui.com/material-ui/getting-started/installation/#icons))

## 공통 레이아웃 작성

### 1.레이아웃 파일을 만든다

```jsx
// src/components/layout.tsx

import { Outlet } from "react-router-dom";
import CssBaseline from "@mui/material/CssBaseline";

export function Layout() {
  return (
    <>
      // CssBaseline은 기본적인 css를 초기화해준다.
      <CssBaseline />
      // react-router-dom 패키지가 chidren을 렌더링하는 방법
      <Outlet />
    </>
  );
}
```

### createBrowserRouter를 만들고 element로 렌더링한다.

```jsx
// src/maintsx

import { createBrowserRouter, RouterProvider } from "react-router-dom";

const router = createBrowserRouter([
  {
    path: "/",
    element: <Layout />,
    // 밑에 children에 해당하는 부분이 Outlet으로 렌더링된다.
    children: [],
  },
]);
```
