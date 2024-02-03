
# CodeitSprint_WeeklyPaper-6th
About Asynchronous_Processing_And_VirtualDOM_In_React

## Asynchronous Processing


```javaScript:Asynchronous.js
// 1번
let num = 1;

// 2번
setTimeout(() => {
  num = 2;
}, 0);

// 3번
num = 3;

// 4번
console.log(num);
```
예시 코드를 실행하면 콘솔에는 3이 출력될 것이다. 그러나, 이 코드 실행이 완전히 끝난 이후에 num에는 3이 아닌 2가 담겨있게 되는데, 이는 setTimeout이 비동기 처리식 함수이기 때문이다.

비동기 처리는 실행을 명령받았을 때, 그 명령을 임시로 저장하여 실행한다. 이후 일반적인 코드 흐름, 즉 동기 흐름이 끝난 이후에 결과를 반환하는데, 여기에서는 console.log가 해당한다.

따라서, 이 코드에서의 코드 흐름은 다음과 같다.

```javaScript:Asynchronous.js
// 1번 실행 및 결과(num 선언 및 1 할당)
let num = 1;

// 2번 실행 (결과 대기)
setTimeout(() => {
  num = 2;
}, 0);

// 3번 실행 및 결과(num 변수에 3 할당)
num = 3;

// 4번 실행 및 결과(num을 console에 출력)
console.log(num);

// 2번 결과(num에 2 할당)
```

이때 이러한 비동기 함수를 동기 코드에 넘겨줘야 할때 .then의 콜백함수를 이용하여 값을 할당할 수 있으며, 2017년 이후 ECMA Script에서 정립된 async await를 선언하여 동일한 기능을 수행 가능하다. 

이때 await의 경우에는 async 내에서만 정상적으로 작동하며, .then 콜백 함수는 프로미스 객체일 경우에만 정상적으로 작동한다.

각각의 활용 경우는 다음과 같다.

```javaScript:Asynchronous.js
// /then 콜백 함수
const testPromise = new Promise ((resolve) => {
   setTimeout(() => {num = 2;}, 0);
   resolve();
})
   .then(() => {num = 3})
   .then(() => {console.log(num)})


// await 동기화 선언
await setTimeout(() => {
  num = 2;
}, 0);
num = 3;
```

이때, 이후의 동작까지 .then 콜백을 이용해야 할 경우 await를 이용하면 훨씬 간략해지는 모습을 볼 수 있다.


## VirtualDOM In React

### DOM
DOM이란 Document Object Moedl의 약자로, 현재 HTML 문서의 전체 요소를 Node라는 단위로 표현한 것으로, HTML의 계층 구조를 반영하여 나무에 비유한 것을 DOM Tree라고 부른다. 각 노드간 관계는 상하관계에 따라 Parent, Children으로, 수평 관계에 따라 Sibling으로 표현된다.

### Virtual DOM
Virtual DOM (VDOM)은 UI의 가상적인 표현을 저장하여, ReactDOM과 같은 라이브러리에 의해 실제 DOM과 동기화하는 프로그래밍 개념이다.

이러한 방식은 React의 선언적 API를 가능하게 하는데, React에게 원하는 UI의 상태를 알려주면 그 상태와 일치하도록 DOM을 재구성 한다. 이러한 방식은 일반적으로 앱 구축에 사용해야 하는 이벤트 처리, 수동 DOM 업데이트를 추상화합니다.

“virtual DOM”은 패턴에 가깝기 때문에 사람들마다 의미하는 바가 다른데, React에서 “virtual DOM”이라는 용어는 보통 사용자 인터페이스를 나타내는 객체이기 때문에 React elements와 연관된다.

### Reflow, Repaint
VDOM이 등장한 배경을 알기 위해서는 위 두 개념이 중요하다.

Reflow는 화면 구조의 변형이 발생할 경우, 요소의 위치 및 크기 등을 재계산하는 것을 의미한다. DOM의 동적 변화에 따른 현상이며, 단일 요소를 reflow하기 위해 모든 요소를 reflow해야할 수 있는 가능성이 생긴다.

Repaint는 reflow 발생시에 변형된 요소를 화면에 다시 그려주는 작업이다. 레이아웃에 영향을 주지는 않지만 각종 스타일 변형 또한 이에 속한다.

위 두 작업은 컴퓨터 리소스를 크게 요구하는데, 이는 웹 이용 경험에 큰 장애를 줄 수 있다.

### Why use VDOM
리액트 이전에는 서버와 통신하며 DOM 객체의 속성값을 변화시키거나 DOM을 변형하도록 만들었는데, 이는 Reflow, Repaint 연산이 많아지며 리소스를 과도하게 사용하는 현상이 빈번했다. 

그러나 리액트는 VDOM을 이용해 가상 표현을 메모리에 저장하고, ReactDOM 등의 라이브러리를 통해 실제 DOM과 동기화 시킨다.
이를 통해 웹 페이지의 최종 변화를 구현하는데 들어가는 작업을 획기적으로 줄여주어 하드웨에에 대한 부담을 줄임과 동시에, 추상화를 통한 작업 편의성을 제공한다.

