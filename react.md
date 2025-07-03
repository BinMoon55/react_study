# React 학습 로드맵 : 단계별 상세 가이드  
## 1. 사전 지식 정리 (HTML/CSS/JS 기초 복습)  
### 필수 복습 항목  
- HTML 기본 구조 (div, input, button, form, img, ul/li, a 등)  
- CSS 선택자와 스타일링 방식 (class, id, Flexbox, Grid)  
- JavaScript 기본 문법  
    - 변수 선언 (let, const)
    - 함수 정의, 화살표 함수
    - 조건문 (if, switch), 반복문 (for, map)
    - 객체/배열 조작 (map, filter, push, spread)
    - DOM 조작 (document.querySelector, addEventListener) → React에서는 안 씀. 개념만 이해
   
>❗️React 배우면서 자주 나올 map, filter, spread(...) 꼭 복습!   

### 다시보기
1) web
- HTML & CSS : 2시간
- CSS Layout : 2시간
2) JavaScript
- DOM : 2시간
- Basic syntax 1 : 2시간
- Basic syntax 2 : 2시간
- Controlling Event : 2시간
- 비동기 JS : 2시간  
> 총 시간 : 10시간   

---

## 2. React 기본 개념 익히기  
### 핵심 개념  
| 개념                  | 설명                                     |
| ------------------- | -------------------------------------- |
| **React란?**         | UI를 효율적으로 구성하기 위한 JS 라이브러리             |
| **컴포넌트(Component)** | 하나의 UI 단위를 함수로 분리. 재사용 가능              |
| **JSX**             | JavaScript + XML. HTML처럼 보이는 JS 문법     |
| **props**           | 부모 → 자식에게 값을 전달하는 방식                   |
| **state**           | 컴포넌트 내부에서 데이터 상태를 저장하고 변경              |
| **이벤트 처리**          | `onClick`, `onChange` 등 HTML 이벤트 연결 방식 |

---

## 3. React 앱 만들기  
### 설치 및 실행  
```
# 1. 설치
npm install -g create-react-app

# 2. 프로젝트 생성
npx create-react-app my-app

# 3. 실행
cd my-app
npm start
```
> 또는 vite로 더 빠르게 시작할 수 있음.(React + Vite)   

---

## 4. 컴포넌트 구조화 + props/state 사용  
### 1. 함수형 컴포넌트 작성
```jsx
function Button(props) {
  return <button onClick={props.onClick}>{props.label}</button>;
}
```
   
### 2. 상태(state) 사용하기  
```jsx
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);
  return (
    <div>
      <p>현재 숫자: {count}</p>
      <button onClick={() => setCount(count + 1)}>+1</button>
    </div>
  );
}
```

---

## 5. 조건부 렌더링과 반복 처리
### 조건부 렌더링
```jsx
{isLoggedIn ? <Logout /> : <Login />}
```
   
### 반복 렌더링(리스트)  
```jsx
const fruits = ['사과', '바나나', '포도'];

<ul>
  {fruits.map((fruit, idx) => (
    <li key={idx}>{fruit}</li>
  ))}
</ul>
```

---

## 6. 컴포넌트 간 통신 (props + Lifting state up)  
- 자식 -> 부모로 값 전달은 직접 안됨  
- 대신, 부모가 자식에게 **함수(props)**를 전달하고 자식이 호출  
```jsx
function Child({ onSend }) {
  return <button onClick={() => onSend("안녕!")}>보내기</button>;
}

function Parent() {
  const handleMessage = (msg) => alert(msg);
  return <Child onSend={handleMessage} />;
}
```

--- 

## 7. React Router로 페이지 분기 처리  
### 설치
```jsx
npm install react-router-dom
```
   
### 사용 예시
```jsx
import { BrowserRouter, Routes, Route } from "react-router-dom";

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </BrowserRouter>
  );
}
```

---

## 8. API 통신 (AI/IoT 백엔드 연동)
### 설치
```jsx
npm install axios
```

### 사용 예시
```jsx
import axios from 'axios';

useEffect(() => {
  axios.get('http://localhost:8000/infer').then(res => {
    console.log(res.data);
  });
}, []);
```

---

## 9. 스타일링 방법
| 방법                | 설명                         |
| ----------------- | -------------------------- |
| CSS 파일            | 전통적인 방식 (`App.css`)        |
| CSS Modules       | 파일마다 고유한 CSS 클래스           |
| styled-components | JS 안에 스타일을 정의              |
| Tailwind CSS      | 유틸리티 클래스 기반 CSS 프레임워크 (추천) |

---

## 10. 고급 개념
| 개념             | 설명                       |
| -------------- | ------------------------ |
| useEffect      | 컴포넌트가 렌더링될 때 실행되는 훅      |
| Context API    | 전역 상태 관리                 |
| useReducer     | 복잡한 상태 처리용 Hook          |
| Recoil/Zustand | 상태 관리 라이브러리              |
| React Query    | 서버 상태 관리 (API 요청 캐싱 등)   |
| Next.js        | React 기반 SSR 프레임워크 (필요시) |