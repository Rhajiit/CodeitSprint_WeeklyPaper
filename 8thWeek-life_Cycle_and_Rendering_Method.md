# CodeitSprint_WeeklyPaper-8th

About life Cycle of React and Rendering Method

## Life cycle of React

리액트에서 생명 주기는 특정한 이벤트를 컴포넌트 실행이나 업데이트, 혹은 제거될 때 호출하는 것이다.

리액트에서의 컴포넌트는 클래스 키워드를 사용하는 클래스형 컴포넌트와 일반적인 함수 선언형식인 함수형 컴포넌트가 있는데, 생명주기는 보통 클래스형 컴포넌트에 해당하는 말이지만
리액트 훅 useEffect 를 이용해 비슷한 효과를 낼 수 있게 한다.

### Class Component Life Cycle

1.  마운트 - 첫 실행시의 생성 단계 중 호출

    - constructor : 컴포넌트의 생성자 메소드 - 가장 먼저 실행
    - getDerivedStateFromProps : props 로 받아온 것을 state 에 설정하고자 할 때 사용
    - render : 컴포넌트를 렌더링
    - componentDidMount : 컴포넌트의 첫번째 렌더링이 마치고 나면 호출

2.  업데이트 - 컴포넌트의 업데이트시 호출

    - getDerivedStateFromProps : 컴포넌트의 props 나 state 가 바뀌었을 때 호출
    - shouldComponentUpdate : 컴포넌트의 리렌더링 여부를 결정
    - render : 업데이트한 내용을 렌더링
    - getSnapshotBeforeUpdate : 컴포넌트에 변화가 일어나기 직전의 DOM에 있는 정보를 가져오고, 해당 메소드에서 반환하는 값은 componentDidUpdate 에 인자로 전달
    - componentDidUpdate : 리렌더링을 마치고, 화면에 원하는 변화가 모두 반영되고 난 뒤 호출하는 메소드

3.  언 마운트 - 컴포넌트를 제거하기 직전 호출

    - componentWillUnmount : 컴포넌트가 제거되기 직전에 호출 - setTimeout , setInterval 등을 사용한 것이 있다면 해당 메소드에서 clearTimeout , clearInterval 등으로 제거할 때 사용.

### Function Component Life Cycle

컴포넌트 생성 속도, 가독성, hook의 활용 등의 이점으로 함수형 컴포넌트를 주로 사용하고 있지만, 함수형 컴포넌트에는 클래스형에서의 생명주기 메소드가 없다. 이러한 기능을 HOOK으로 대체할
수 있다. 각 기능의 대체는 다음과 같다.

1. 마운트

   - constructor : useRef 또는 useState 를 활용해 생성 시 1회성 동작을 만들 수 있음.
   - getDerivedStateFromProps : useState(initialValue)프롭을 받아 초기 상태를 지정
   - render : 함수형 컴포넌트에서의 return
   - componentDidMount : useEffect 를 사용합니다.

```javaScript
useEffect(() => {
// componentDidMount 원하는 실행
}, []);
```

2. 업데이트

   - getDerivedStateFromProps : useState()의 값을 변경하여 새로운 State를 적용
   - shouldComponentUpdate : React.memo 를 사용
   - getSnapshotBeforeUpdate, componentDidUpdate : 변화 감지를 원하는 props, state 를 useEffect deps로 설정하여 사용

3. 언마운트

   - componentWillUnmount : useEffect 에 callback을 return 해서 사용합니다.

```javaScript
useEffect(() => {
   componentDidUpdate
   return () => {
      componentWillUnmount
   }
}, [deps]);
```

## Rendering Method

### CSR (Client Side Rendering)

#### 클라이언트의 웹 브라우저에 javaScript와 HTML을 받아 렌더링하는 방식

장점

- 페이지 전환 속도가 적당히 빠르며, 부드럽게 페이지가 바뀜.
- 자바스크립트의 HTML 연산작업이 서버에 크게 할당되지 않아 서버 부하가 적음.

단점

- SPA(Single Page Application)의 경우 처음 페이지 접근시 서버로부터 전체 페이지에 대한 자바스크립트 번들파일, CSS 파일을 받아야 하므로 페이지를 만들고 유저가 사용하기 까지 시간이 SSR에 비해 오래 걸립니다.
- 자바스크립트를 이용해 동적으로 콘텐츠를 생성한 후에 데이터를 수집이 가능하여 검색엔진 최적화에 불리한 점이 있음.

주 사용처

- 페이지 상호작용이 많으며 검색 엔진에 크게 노출되지 않아야 하는 웹 페이지에 적합.
- 특정 계정 전용 페이지 등을 만드는데 적합.

### SSR (Server-side Rendering)

#### 요청에 맞는 HTML을 서버에서 생성하여 응답으로 보내주는 방식

장점

- 요청에 대하여 완성된 페이지를 제공하므로, 검색엔진 최적화가 용이함.
- 서버로부터 해당 페이지에 필요한 데이터들과 이미 만들어진 HTML을 전달 받으므로, 필요한 데이터를 받아 클라이언트에서 실제로 유저가 사용하기 까지 걸리는 시간이 CSR에 비해 빠름.

단점

- 서버에 단시간 내에 과도한 요청이 발생할 경우, 연산작업이 서버에 큰 부하를 줄 수 있습니다.
- 페이지 전환시 새로운 페이지 HTML을 받으면서 전체 페이지가 사라지고 깜빡임이 발생. - 자연스럽지 못한 현상으로 불쾌감 유발 가능.

주 사용처

- 페이지 내용이 정적이지만, 데이터 변동이 자주 발생하여 서버 내 데이터를 참조하거나 검색엔진 최적화가 필요한 페이지에 적합.
- 컨텐츠 중심의 웹 사이트나 자주 데이터가 변동하는 전자 상거래 웹 사이트에 적합.

### SSG (Static Site Generation)

#### HTML 파일을 서버에 배포한 후, 서버에 요청이 들어오면 이미 만들어진 HTML 파일을 읽어 응답으로 보내주는 방식

장점

- 서버에 미리 만들어 둔 페이지를 클라이언트에 제공. - 렌더링 속도가 매우 빠름!
- SSR과 비슷하게 이미 완성된 페이지를 응답으로 보내므로 검색엔진 최적화에 용이.

단점

- 모든 url에 대한 HTML문서가 필요. - 페이지의 종류가 과도하게 많거나 규모가 클 경우 복잡성이 증대.

주 사용처

- 페이지 내 데이터가 자주 변하지 않으며, 검색 엔진에 노출될 필요가 있는 웹페이지에 유용.
- 뉴스와 같은 정적인 정보성 페이지에 적합.
