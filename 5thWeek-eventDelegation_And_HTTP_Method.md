
# CodeitSprint_WeeklyPaper-5th
About eventDelegation_And_HTTP_Method

## Event Delegation
Event Delegation (이벤트 위임)이란, 요소에 할당된 이벤트가 발동했을 때, 그 요소와 상하 관계로 연결된 요소에도 동일한 이벤트가 발동하는 현상을 의미한다. 이때, 이 이벤트가 연쇄되는 방향에 따라 Bubbling과 Capturing으로 나뉜다.
이때, 이벤트가 발생한 요소의 Handler의 스크립트 또한 실행한다.

이는 Handler의 작동 원리에서 부수적으로 나타난 현상인데, 최상위 요소 HTML에서 요소를 따라 순차적으로 Handler를 호출한 요소에 도착한 후, 관련 정보를 최상위 요소로 전달하는 과정에서 거쳐가는 순차적인 과정에서 기인한 것이기 때문이다.

이러한 방법을 이용해 각 요소가 아닌 부모 요소에 할당하여 코드의 간략화를 이끌어 낼 수 있다.

### Bubbling
Bubbling은 이벤트가 발생 했을 때, 발동 요소에서 최상위 요소로 이벤트가 거슬러 올라가는 현상을 의미한다. 예를 들어,
 
  > Form 1
  >> Form 2
  >>> Form 3
  >>> 
  >> .
  >> 
  > .

와 같은 식의 구조로 되어 있을 때, Form 3에서 발생한 이벤트는 Form 1 까지 위임되어 호출된다.

'거의 모든' 이벤트는 버블링 된다. - 그러나 focus 이벤트와 같이 버블링 되지 않는 이벤트도 있으므로, 각 이벤트의 특성을 정확하게 알고 있어야 한다.

### Capturing
Capturing은 이벤트가 발생 했을 때, 최상위 요소에서 발동 요소로 이벤트가 거슬러 내려가는 현상을 의미한다. 즉,
 
  > Form 1
  >> Form 2
  >>> Form 3
  >>> 
  >> .
  >> 
  > .

와 같은 식의 구조로 되어 있을 때, Form 1에서 발생한 이벤트는 Form 3 까지 위임되어 호출된다.

캡처링 단계를 이용해야 하는 경우는 흔하지 않으므로 Handler는 Capturing 설정이 기본적으로 비활성화되어있으며, addEventListener의 capture 옵션을 true로 설정해 활성화를 해야한다.
> addEventListener( ...... , {capture: true})
>
> 또는
>
> addEventListener( ...... , true)

### EventTarget
부모 요소의 핸들러는 이벤트가 정확히 어디서 발생했는지 등에 대한 자세한 정보를 얻을 수 있다.

이벤트가 발생한 가장 안쪽의 요소는 타깃(target) 요소라고 불리고, event.target을 사용해 접근할 수 있다.

event.target과 this(=event.currentTarget)는 다음과 같은 차이점이 있습니다.

> event.target은 실제 이벤트가 시작된 ‘타깃’ 요소이다. 버블링이 진행되어도 변하지 않는다.

> this는 버블링으로 위임된 '현재' 요소로, 현재 실행 중인 핸들러가 할당된 요소를 참조한다.

### Caution
이 현상들을 원하지 않는 경우 양 쪽 모두 다음 Method를 이용해 이러한 현상을 막을 수 있다.
 > evnet.stopPropagation();

그러나, 꼭 필요한 경우가 아니면 위의 Method는 권장되지 않는데, 이는 Web Analytics Service 때문이다.

Web Analytics Service는 사이트의 유저 동향이나 데이터를 쌓기 위한 것으로,  event bubbling을 통해 event를 탐지하고 데이터를 수집하는 경우가 할 때
StopPropagation을 사용할 경우 event bubbling이 일어나지 않아 해당 툴이 클릭을 캡쳐하지 못할 수 있다.

사실 이러한 경우를 반드시 막아야 하는 경우는 흔하지 않으며, 간단히 동작하고자 하는 요소에 대한 제한사항을 거는 등의 방법으로도 버블링으로 인한 이벤트 연쇄를 막을 수 있다.
그러므로 stopPropagation은 완전히 통제된 상황이 아닌이상 사용하지 않아야 한다.

## HTTP Method
HTTP Method란, 클라이언트 - 서버 구조에서 서버 구조가 수행할 동작을 지정하여 Request와 Response가 이루어지는 방식이다.

이는 리소스와 동작을 분리하여 URL로 하여금 리소스만 식별하게 하기 위함으로, 종류는 크게 8가지가 있다.
> Get - 리소스 조회
> Post - 데이터 추가/등록
> Put - 리소스 대체/수정 (미보유시 새로 생성)
> Delete - 리소스 삭제
> Patch - 리소스 부분 변경
> Head - Get과 유사하나 HTTP의 Body부분을 제외
> Options - 서버와 브라우저간의 통신옵션 확인
> Connect - 대상으로 식별되는 서버에 대한 연결 요청

### Get

### Post

### put

### Delete

### Patch

### Head

### Options

### Connect
