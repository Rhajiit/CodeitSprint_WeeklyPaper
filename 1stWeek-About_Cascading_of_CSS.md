# CodeitSprint_WeeklyPaper-1st
About Cascading of CSS

## CSS와 Cascading
우선, Cascading은 **'폭포수처럼 쏟아지는'** 이라는 뜻을 지닌다. CSS는 Cascading Style Sheet의 약자로, 이름에서 드러나듯이 Cascading은 **CSS의 중심 개념**이라고 볼 수 있다.

>  `<div style="background-color: #dfdfdf; color: #000000;">`
> 
>  `  <p style="background-dolor: #101010;">Code it</p>`
> 
>  `</div>`

이와 같이 CSS를 작성할 때 같은 요소(예시에서는 Code it)에 여러 스타일이 중복될 수 있는데, 이는 CSS파일에서 흔하게 일어나는 일이다. 
이러한 상황에서 최종 요소에 적용할 스타일에 대한 규칙을 세운 것을 **Cascading** 이라고 부른다.

Cascading은 다음 원칙을 이용하여 해당 요소에 어떠한 스타일을 적용할 것인지 판단한다.

1. 스타일 우선순위
2. 스타일 상속

## 스타일 우선순위
우선 순위란 한 요소에 대하여 어떤 스타일을 적용할 지 결정하는 규칙을 의미하며, 규칙의 종류는 다음과 같다.
1. 중요도
2. 명시도
3. 코드상 순서

### 중요도
**중요도**는 스타일이 선언된 위치에 따라 우선순위를 매기는 것으로, 작성자(Author), 사용자(User), 사용자 도구(User agent 브라우저가 대표적임) 세종류가 있다. 각 스타일 시트의 우선 순위는 다음과 같다.
> 1.Author > 2.User > 3.User Agent

이때, !important를 이용하면 우선순위를 최우선으로 끌어올린다.(이 때에도 적용된 위치에 따라 !important간의 우선순위를 동일하게 적용한다.)

### 명시도


### 코드상 순서



## 스타일 상속
