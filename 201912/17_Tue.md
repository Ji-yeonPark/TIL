# 2019.12.17 화요일

### :movie_camera: Django

- **#5.0 ~ #5.3 All Other Apps**
  - 다른 app들 models 정의관련
- **#6.0 ~ #6.3 Room Admin**
  - admin화면 디자인관련

### :book: 리액트를 다루는 기술(개정판)

- 13장. 리액트 라우터로 SPA 개발하기
  - SPA : Single page application 한 개의 페이지로 이루어진 애플리케이션
  - 라우터 : 다른 주소에 다른 화면을 보여주는 것
  ```javascript
  <Route path="주소" component={컴포넌트} exact>
  <Route path={["주소1", "주소2"]} component={컴포넌트} exact>
  ```
  - 링크(Link) : 클락하면 다른 주소로 이동시켜 주는 컴포넌트, a태그
    ```javascript
    <Link to="주소">이름</Link>
    ```
    - a태그를 사영하먄 페이지를 전환하는 과정에서 새로운 페이지를 불러오기 때문에 다시 렌더링하게되어 갖고 있던 상태를 모두 날려버리게 된다. 그래서 a 태그 대신 link를 사용해야 한다.
    - HTML5 History API를 사용하여 페이지의 주소만 변경해준다.
    - URL 파라미터 :
    ```javascript
    <Route path="주소/:유동적인값" component={컴포넌트}>
    ```
    - URL 쿼리 : location 객체에 들어 있는 search 값에서 조회
      - search 값에서 특정 값을 읽기 위해서는 이 문자열을 객체 형태로 변환해줘야 하며 `qs`라이브러리를 이용
    ```javascript
    const query = qs.parse(location.search, {
      ignoreQueryPrefix: true // 문자열 맨 앞 ? 생략
    });
    ```
    - histroy
      - 뒤로가기, 홈으로 이동등 컴포넌트 내에 구현하는 메서드에서 라우터 API호출 가능.
    - withRouter
      - 라우트로 사용된 컴포넌트가 아니어도 match, location. history 객체를 접근할 수 있게 해줌.
    - switch
      - 여러 Route를 감싸서 그중 일치하는 단 하나의 라우트만 렌더링시켜 줌.
      - Not Found 페이지도 구현 가능.
    - NavLink
      - 현재 경로와 Link에서 사용하는 경로가 일치하는 경우 특정 스타일 혹은 CSS클래스를 적용할 수 있는 컴포넌트.
      - activeStyle : 링크가 활성화되었을 때의 스타일 적용
      - activeClassName : CSS 클래스를 적용
