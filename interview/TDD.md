**Test Driven Development(테스트 주도 개발)**

```jsx
프로그램을 작성하기 전에 테스트를 먼저하라!
- 캔트 백 -
```

### TDD란?

XP(eXtream Programming)의 창시자중 한명이며, TDD를 주도한 켄트 벡은 "프로그램을 작성하기 전에 테스트를 작성하는 것"이라고 테스트 주도 개발을 정의 했다.

**"업무 코드를 작성하기 전에 테스트 코드를 먼저 만드는 것!"**

최초에는 테스트 우선 개발이라 불린다. 테스트 코드부터 작성한다는 TDD의 정의가 다소 과격하게 들릴 수도 있지만, 메소드나 함수 같은 프로그램 모듈을 작성할 때 '작성 종료 조건을 먼저 정해놓고 코딩을 시작한다'는 의미로 받아들이면 편하다. 간단한 두 숫자의 합을 구하는 sum함수를 작성 할 때 TDD라는 용어를 꺼내지 않더라도, 프로그램을 작성할 때 머릿속으로 생각하는 내용과 별반 다르지 않다. 다만

`'문서로 만들어 머리로 생각하고 눈으로 확인할 것인가?'` 아니면, `'예상 결과를 코드로 표현해놓고 해당 코드가 자동으로 판단하게 할 것인가?'`의 차이가 있다.

### 테스트 주도 개발의 목표

```jsx
잘 동작하는 깔끔한 코드
- 론 제프리 -
```

TDD라는 방식을 통해 얻고자 하는 최종 목적은 `'잘 동작하는 깔끔한 코드'`이다. 일반적인 소프트웨어 개발의 목표와 별반 다르지 않다. 다만 TDD에선 정상적으로 동작하는 코드만을 개발의 목표로 삼지 않고, 작성된 코드도 명확한 의미를 전달할 수 있게 작성돼야 한다고 말한다. 즉, 제대로 동작함 뿐 아니라 깔끔함 까지도 동등한 수준의 개발 목표로 심는다는 점이 일반적인 개발 방식과 다르다. 이 차이점은 소프트웨어의 비용과 안전성 품질을 비롯한 유지보수의 편의성, 가독성, 그리고 그에 따른 소프트웨어의 비용과 안정성 등의 여러가지 측면의 의미를 내포한다.

### 테스트 주도 개발의 기원

```jsx
애자일 개발 방식 중 하나인 XP의 실천 방식 중 하나

/*
애자일
발에 임하는 것을 말하며, 개발 그 자체에 집중할 수 있도록 개발환경을 조성한다.
전통적인 개발 방법론들이 소프트웨어 개발 업무 그 자체보다는 문서와 프로세스 같은
부가적인 부분들에 집중하는 모습에 대항하여 나온 방식이기도 하다.
*/
```

TDD는 XP에서 등장하는 여러 가지 실천 방법 중 하나로 테스트 우선 개발과 동일한 의미를 갖는다. 애자일 소프트웨어 개발론의 하나로 단순성, 상호소통, 피드백 용기 등의 원칙에 기반해 `'고객에게 최고의 가치를 최대한 빨리 전달하는 것'`을 목표로 삼는다.

### 개발에 있어 테스트 주도 개발의 위치

```jsx
개발자가 처음으로 수행하는 테스트
```

소프트 웨어 개발에서 TDD는 '개발자 자신을 위해 처음으로 수행하는 테스트'에 해당한다. 그래서 흔히 개발자 테스트 라고 부르기도 한다. 때로는 그냥 단위 테스트라고도 하데, 이는 보통 전통적인 테스트 방법론에서 이야기하는 단위 테스트보다는 범위가 다소 협소하다. 따라서 구분해서 이야기할 필요가 있는데 TDD에서 말하는 단위 테스트는 일반적으로 메소드 및 함수 단위의 테스트를 뜻하고, 전통적인 테스트 방법론에서 이야기하는 단위 테스트는 사용자 측면에서 제품의 기능을 테스트 하는 쪽에 가깝다. TDD에서 개발자는 자신이 작성한 프로그램에 대해 메소드 혹은 함수 단위로 테스트를 수행하며, 이는 결과적으로 이후에 발생하는 테스트 단계(통합 테스트나 인수 테스트 등)에서의 결함발생 비용을 줄여준다. 결함은 빨리 발견하면 할수록 비용으로 처리가 가능하기 때문에 규모가 큰 프로그램일수록 적용 효과가 크다.

### 테스트 주도 개발의 진행 방식

```jsx
- 질문(Ask): 테스트 작성을 통해 시스템에 질문한다. (테스트 수행 결과는 실패)
- 응답(Responed): 테스트를 통과하는 코드를 작성해서 질문에 대답한다.(테스트 성공)
- 정제(Refine): 아이디어를 통합하고, 불필요한 것은 제거하고, 모호한 것은 명확히 해서 대답을 정제한다.(리펙토링)
- 반복(Repeat): 다음 질문을 통해 대화를 계속 진행한다.
```

TDD를 이용한 개발은 크게 `질문 -> 응답 -> 정제` 라는 세 단계가 반복적으로 이루어진다.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3b06ea60-bf98-44b8-a159-89d58447fb96/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3b06ea60-bf98-44b8-a159-89d58447fb96/Untitled.png)

TDD는 위와 같은 형태의 반복적인 흐름을 갖는다.

- **@테스트 주도 개발 : 고품질 쾌속개발을 위한 TDD 실천법과 도구 참고 -**
