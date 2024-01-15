
# CodeitSprint_WeeklyPaper-4th
About Copy method and Variables in JavaScript

## Copy Method


### 얕은 복사(shallowCopy)
  
### 깊은 복사(deepCopy)

   
## Form of Varialbes
자바스크립트는 현재 let, const를 이용하여 변수, 상수를 지정하나, 그 이전에는 var(riable) 예약어를 이용하여 변수를 지정하던 때가 있었다.

그러나, var는 여러 문제가 있어 현재는 사용되지 않는데, 현재의 let, const와 어떻게 다른지, 왜 쓰지 않게 되었는지를 중복 선언(Duplicate Allow) / 스코프(Scope) / 끌어올림(Hoisting)의 관점에서 서술한다.

### 중복 선언 (Duplicate Allow)
현재의 let, const는 자바스크립트에서 중복 선언을 금지하여, 똑같은 이름의 변수가 선언될 경우 에러가 일어난다. 그러나, 이와 다르게 var는 중복선언을 허용한다. 즉, 다음과 같은 형태를 허용한다.

  > var weeklyPaper = 'selfStudy';
  > 
  > console.log(weeklyPaper);
  > 
  > var weeklyPaper = 'forcedStudy';
  > 
  > console.log(weeklyPaper);
  > 
  >
  > 결과
  > 
  > 
  > 'selfStudy'
  > 
  > 'forcedStudy'

그러나, 이러한 구조는 코드가 길어져 구조를 파악하기 힘들거나 협업을 할 시에 간혹 변수 이름이 겹칠 경우 문제가 발생한다. 

이러한 문제를 방지하기 위하여 let과 const는 중복 방지 개념을 도입하고 같은 코드 내에서 변수 / 상수 이름이 겹치지 않도록 하여 예방하도록 조치한 것이다.


### 스코프 (Scope)
let과 const는 같은 function 같이 중괄호 코드블럭{} 내에서 선언된 경우에는 모드 그 블럭에서만 사용이 가능한 지역 변수로서 선언되지만, 
var의 경우 이 스코프 규칙이 function에만 적용되어 function 외의 다른 중괄호(if, for, switch 등) 내에서 선언된 경우라면 전역 변수로서 사용이 가능했다. 즉,
  
  > if (...) { var x = 3; }
  > 
  > for (...) { var y = 'Rhajiit'; }
  > 
  > console.log(x);
  > 
  > console.log(y);
  > 
  > 결과
  > 
  > 
  > 3
  > 
  > 'Rhajiit'


이런 경우가 발생할 수 있다.

이는 의도치않게 전역 변수를 지정 / 변경함으로서 중복 선언 규칙과 마찬가지로 큰 문제가 발생할 우려가 크다.


### 끌어올림 (Hoisting)
let 과 const는 이를 선언하기 전에는 실 사용이 불가능하다. 즉,

  > console.log(rhajiit);
  > 
  > let rhajiit = 'Meow'
  > 
  > 결과
  > 
  > error : rhajiit이 지정되지 않음

과 같은 순서가 된다. 그러나 var의 경우는 이와 같은 경우에도 error가 발생하는 것이 아니라, 정상적으로 선언한 것처럼 동작이 되는데, 이를 끌어올림 (Hoisting)이라고 한다. 
이때, 선언 값은 그 위치에 그대로 남아 있으므로, 끌어올림된 출력에는 제대로 작동하지 않는다.

참고로, 이 현상은 function에도 그대로 적용된다.

간략한 예시는 다음과 같다.

  > console.log(rhajiit);
  > 
  > var rhajiit = 'Meow';
  > 
  > console.log(rhajiit);
  > 
  > 결과
  >
  > undefined
  > 
  > 'Meow'

이 현상은 코드의 유연함에는 큰 장점이 될 수 있겠지만, 대부분의 코드 흐름에서는 방해가 될 가능성이 높다. function의 경우도 가능하다면 코드 상단에 작성하는 것이 권장된다.
