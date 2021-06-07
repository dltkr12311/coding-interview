![https://image.toast.com/aaaadh/alpha/2016/techblog/javascriptoverview.png](https://image.toast.com/aaaadh/alpha/2016/techblog/javascriptoverview.png)

**클로저에 대한 정의는 없다.** 클로저는 자바스크립트가 채용하고 있는 기술적 기반 혹은 컨셉으로, 자바스크립트는 클로저를 이용하여 스코프적 특징과 일급 객체로서의 함수에 대한 명세를 구현한 것이다.

# 스코프(Scope)

프로그래밍에서 변수나 함수의 이름을 부여하여 의미를 갖도록 한다. 만약 이름이 없다면 그저 하나의 메모리 주소에 지나지 않는다. 그래서 프로그램은 "이름:값"의 대응표를 만들어 사용한다. 이 대응표의 이름을 가지고 코드를 보다 쉽게 이해하고, 또 이름을 통해 값을 저장하고, 다시 가져와 수정한다.

초기 프로그래밍 언어는 이 대응표를 프로그램 전체에서 하나로 관리했는데, 이름 충돌의 문제가 있었다. 그래서 충돌을 피하기 위해, 각 언어마다 스코프 규칙을 만들어 정의하였다.

### **스코프의 규칙**

(**함수 레벨 스코프**

- 자바스크립트에서는 `var`키워드로 선언된 변수나, `함수 선언식`으로 만들어진 `함수는 함수 레벨` 스코프를 갖는다. 즉, 함수 내부 전체에서 유요한 식별자가 된다.
- **블록 레벨 스코프**

- ES6의 `let` , `const` 키워드는 블록 레벨 스코프 변수를 만들어 준다.

**렉시컬 스코프**

- 렉시컬 스코프에서는 **소스코드가 작성된 그 문맥에서 결정된다**. 요즘 프로그래밍에서는 대부부분의 언어들은 렉시컬 규칙을 따르고 있다.
- 렉시컬 스코프를 규칙을 따르는 자바스크립트의 **함수는 호출 스택과 관계없이 각각의 대응표를 소스코드 기준으로 정의하고, 런타임에 그 대응표를 변경시키지 않는다**.

### 중첩 스코프(스코프 체인 또는 스코프 버블)

자바스크립트의 스코프는 ECMAScript 언어 명세에서 렉시컬 환경(`Lexical enviroment`)과 환경레코드(`Enviroment Record`) 라는 개념으로 정의되어있다.

![https://image.toast.com/aaaadh/alpha/2016/techblog/executioncontext.png](https://image.toast.com/aaaadh/alpha/2016/techblog/executioncontext.png)

"이름:값의 대응표가" 환경 레코드과 같다고 볼 수 있고, 렉시컬 환경은 이 환경레코드와 상위 렉시컬 환경에 대한 참조로 이루어진다.

현재-렉시컬 환경의 대응표(환경 레코드)에서 변수를 찾아보고, 없다면 바깥(상위) 렉시컬 환경을 참조하여서 찾아보는 식으로 중첩 스코프가 가능해진다. 이 중첩 스코프 탐색은 해당하는 이름을 찾거나 바깥 렉시컬 환경 참조가 `null` 이 될 때 탐색을 멈춘다.

---

# 클로저(Closure)

- 함수 밖에서 선언된 변수를 함수 내부에 사용할 때 클로저가 생겨난다.

```jsx

클로저 = 함수 + 함수를 둘러싼 환경(Lexical environment)

function outer() {
  let name = 'lee';
  function inner() {
		console.log(name);
  }
	return inner;
}

let innerFunc = outer();
innerFunc();
```

함수를 둘러싼 환경이라는 것이 바로 렉시컬 스코프이다. 함수를 만들고 그 함수 내부의 코드가 탐색하는 스코프를 함수 생성 당시의 렉시컬 스코프로 고정하면 바로 클로저가 된다.

### 자바스크립트의 클로저

- 자바스크립트에서 클로저는 함수가 생성되는 시점에 생성된다.
  = 함수가 생성될 때 그 함수의 렉시컬 환경을 포섭(closure)하여 실행될 때 이용한다.

따라서 개념적으로 자바스크립트 모든 함수는 클로저라고 할 수 있지만, **실제로 모든 함수가 클로저라고 부르지는 않는다.**

**닳고 닳은 유명한 클로저**

```jsx
function count() {
  var i;
  for (i = 1; i < 10; i++) {
    setTimeout(function timer() {
      console.log(i);
    }, i * 100);
  }
}
count();
```

이 코드는 1 부터 9까지 0.1초마다 출력해야 하는데 결과로는 10이 9번 출력이 된다.

- 1~9까지 차례대로 출력할수 있는 두 가징 방법

  1. 새로운 스코프를 추가하여 반복 시마다 각각 따로 값을 저장하는 방식

  ```jsx
  function count() {
    var i;
    for (i = 1; i < 9; i++) {
      (function (countingNumber) {
        setTimeout(function timer() {
          console.log(countingNumber);
        }, i * 100);
      })(i);
    }
  }
  count();
  ```

      2. ES6에서 추가된 블록 스코프를 이용하는 방식

  ```jsx
  function count() {
    for (let i = 1; i < 9; i++) {
      setTimeout(function timer() {
        console.log(i);
      }, i * 100);
    }
  }
  count();
  ```

클로저는 함수와 함수가 선언된 어휘적 환경에 조합이다.

```jsx
function outer() {
  let name = "서울"; //outerName은 outer에 의해 생성된 지역 변수다.
  function inner() {
    //inner는 내부 함수이며 클로저 이다.
    console.log(name); //부모 함수에 선언된 변수를 사용한다.
  }
  inner();
}
outer();
```

outer는 지역변수인 name과 inner를 생성한다. inner함수는 outer 함수에 의해 정의된 내부 함수이며, outer 함수 본문에서만 사용 할 수있다. inner함수에서는 지역 변수가 없다. 함수 내부에서 외부 함수에 접근 할 수 있기 때문에 inner함수에서 outer함수에 선언된 지역변수 name에 접근 할 수 있다. 만약에 inner함수 지역변수를 가지고 있다면 this.name으로 사용 할 수 있다.
