
# CodeitSprint_WeeklyPaper-5th
About eventDelegation_And_HTTP_Method

## Event Delegation
Event Delegation (이벤트 위임)이란, 요소에 할당된 이벤트가 발동했을 때, 그 요소와 상하 관계로 연결된 요소에도 동일한 이벤트가 발동하는 현상을 의미한다. 이때, 이 이벤트가 연쇄되는 방향에 따라 Bubbling과 Capturing으로 나뉜다.
이때, 이벤트가 발생한 요소의 Handler의 스크립트 또한 실행한다.

이는 Handler의 작동 원리에서 부수적으로 나타난 현상인데, 최상위 요소 HTML에서 요소를 따라 순차적으로 Handler를 호출한 요소에 도착한 후, 관련 정보를 최상위 요소로 전달하는 과정에서 거쳐가는 순차적인 과정에서 기인한 것이기 때문이다.

Handler는 Capturing 설정이 기본적으로 비활성화되어있어 따로 활성화를 해야하며, 일반적으로 Bubbling에 비해 잘 쓰이지 않는다.

이러한 방법을 이용해 각 요소가 아닌 부모 요소에 할당하여 코드의 간략화를 이끌어 낼 수 있다.
이 현상을 원하지 않는 경우 양 쪽 모두 다음 Method를 이용해 이러한 현상을 막을 수 있다.
 > evnet.stopPropagation();

그러나, 꼭 필요한 경우가 아니면 위의 Method는 권장되지 않는데, 이는 Web Analytics Service 때문이다.

Web Analytics Service는 사이트의 유저 동향이나 데이터를 쌓기 위한 것으로,  event bubbling을 통해 event를 탐지하고 데이터를 수집하는 경우가 할 때
StopPropagation을 사용할 경우 event bubbling이 일어나지 않아 해당 툴이 클릭을 캡쳐하지 못할 수 있다.

그러므로 stopPropagation은 완전히 통제된 상황이 아닌이상 사용하지 않아야 한다.

### Bubbling
Bubbling은 이벤트가 발생 했을 때, 발동 요소에서 최상위 요소로 이벤트가 거슬러 올라가는 현상을 의미한다. 

### Capturing
Capturing은 이벤트가 발생 했을 때, 최상위 요소에서 발동 요소로 이벤트가 거슬러 내려가는 현상을 의미한다. 



## HTTP Method

