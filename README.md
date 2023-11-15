# GitDong

## 프로젝트 소개
<img width="1076" alt="20231104_183451" src="https://github.com/piouy001/gitdong/assets/60591071/813da0f5-91d2-468b-b49f-b74e70a72a41">
Github 유저를 찾아볼 수 있는 개인 프로젝트입니다.
평소에는 webpack으로 react환경을 구축했는데 이번에 vite장점을 알아보고자 vite로 환경을 구축했습니다.

배포주소 : https://gitdong.vercel.app/

- React와 Vite를 사용했고 Typescript로 개발했습니다.
- 눈의 피로함을 줄여주는 다크모드를 적용하였습니다.
- prettier과 eslint rules를 추가하여 가독성이 좋고 잠재적인 오류와 버그를 쉽게 수정할 수 있는 환경을 구축하였습니다.
- React Query를 이해하고 적용하여 데이터 패치, 캐싱, 업데이트, 로딩처리를 보다 쉽게 개발하였습니다.
- IOS 아키텍쳐 패턴인 VIPER패턴을 이해하고 적용하여 각 도메인의 역할이 명확하게 구분되는 유지보수하기 좋은 개발을 했습니다.
- 웹표준을 준수하여 디자인 퍼블리싱 및 Media Query를 이용한 반응형 작업을 했습니다.
## 기술 스택

React, Vite, Typescript, React Query, Context API

## 프로젝트 구조

```jsx

└── src
     ├── components
     │     ├── layout
     │     ├── user
     │     │     ├── UserProfile.tsx
     │     │     └── UserScreen
     │     │     │     ├── UserScreen.tsx
     │     │     │     ├── UserScreen.interactor.tsx
     │     │     │     ├── UserScreen.presenter.tsx
     │     │     │     └── UserScreen.router.tsx
     ├── asset
     │     ├── fonts
     │     ├── svg
     ├── constants
     ├── contexts
     ├── hooks
     ├── model
     ├── queries
     ├── services
     ├── styles
     ├── theme
     ├── utils
```

### components

1. 재사용 할 수 있는 component들 보관합니다.
2. UserScreen 폴더에는 UserScreen과 interactor, presenter, router 이렇게 4개가 한 세트로 들어있습니다. 각 파일은 다음과 같이 역할을 맡습니다.
- Interactor : 비즈니스 로직을 담당하며, API 통신 등의 네트워킹이나 data에 대한 처리를 하고 결과를 Presenter에 전달합니다.
- Presenter : Presenter는 View, Router, Interactor에 대한 의존성을 가지고 있으며, View에 Event를 전달받아 Interactor를 통해 처리하고 View에 data와 함께 UI  Update요청을 보내거나 Router를 통한 화면 이동을 처리합니다.
- Router : 와이어프레임이라고도 불리며 화면 전환과 각 구성요소의 의존성 주입을 처리합니다.
- View :View는 ViewController를 의미하며 UI와 관련된 처리만합니다.  Presenter에 대한 의존성을 가지고 있으며 viewDidLoad 같은 LifeCycle과 button touch 등의 Event에 대한 처리를 Presenter에게 위임하고 Presenter의 요청을 받아 UI를 Update합니다. 말 그대로 UI만 담당한다고 보면 됩니다.

### services

각 endpoint에 대한 http요청 함수를 정의합니다.

### queries

react query로직을 정의합니다. 이 파일에서 services 폴더에서 선언한 함수를 사용합니다.

### model

http 요청에 대한 response를 가공하기위한 model을 정의합니다.

### hooks

custom hook들을 정의합니다.

### contexts

Context API의 Provider 및 Selector를 정의합니다.

### utils

자주 사용하는 util 함수를 정의합니다.

### constants

자주 사용하는 util 상수를 정의합니다.

### styles

media query에서 사용하는 값, 자주 사용하는 text style 등을 정의합니다.

### theme

컬러 팔레트를 정의합니다.

### asset

fonts, svg를 정의합니다.
