
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
