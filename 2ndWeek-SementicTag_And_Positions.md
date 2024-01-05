# CodeitSprint_WeeklyPaper-2nd
About SementicTag and Positions

## Sementic Tag
**Sementic Tag**는 일반적인 역할은 div태그와 동일하나 특별한 이름을 붙여 구분하는 것으로서, 모든 Sementic Tag는 단순히 div로 바꿔도 동일한 동작을 보여준다.

그러나 Sementic Tag가 권장되는 이유는 여러 가지가 있는데, 간단하게는 다음과 같다.

1. 검색엔진에 제공되는 정보를 최적화 함으로서 
2. 접근성 어쩌구
3. 
4. ㄴㅇㄹ
5. ㄴㅇㄹ


## Positions
**Position**은 지정된 블록의 배치 형태를 지정하는 구문이며, 다음과 같은 형태가 있다.
 
1. static
    - 현배 Block을 원래 있어야 할 위치에 배치하며, 별도의 Position을 지정하지 않을 경우의 기본 상태이다.
2. Relative
    - 원래 위치를 기준으로 배치하며, 별다른 조작없이는 Static과 비슷하나 Top, Left 등 위치를 옮기는 구문과 같이 사용할 경우 원래 있었던 공간은 Block이 그대로 있는 것 처럼 간주하고 해당 Block만 재배치한다.
4. Absolute
    - 가장 가까운 Positioning이 된(기본 상태인 Static을 제외) 조상 요소를 기준으로 배치하며, 요소의 원래 자리는 빈 공간이 되어 다른 요소를 위한 공간이 된다.
6. Fixed 
    - 현재 브라우저 화면을 기준으로 배치를 고정하며, 글의 흐름에서 완전히 빠지므로 요소의 원래 자리는 차지하지 않는다.
8. Sticky
    - 일반적으로는 Static형식으로 작동하나, 스크롤하여 해당 Block의 지정된 위치(Top, left등)를 화면에서 넘기려 시도할 경우 지정된 위치에 붙어 fixed와 같이 작동하는 형식으로 변환된다.
