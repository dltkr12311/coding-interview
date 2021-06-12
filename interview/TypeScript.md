# TypeScript

**목차**

**왜 타입스크립트를 써야 할까?**

C#과 JAVA같은 체계적이고 정제된 언어들에서 사용하는 강한 타입 시스템은 높은 가독성과 코드 품질 등을 제공할 수 있고 런타임이 아닌 컴파일 환경에서 에러가 발생한다면 치명적인 오류들을 쉽게 잡아 낼수 있다.

반면 자바스크립트는 동적 프로그래밍 언어로, 변수는 문자열, 숫자, 불린 등 여러가지 타입의 값을 가질 수 있다. 이 때문에 유연하게 개발할 수 있는 환경을 제공하는 한편 런타임 환경에서 쉽게 에러가 발생할 수 있는 단점을 가진다.

타입스크립트는 이러한 자바스크립테에 강한 타입 시스템을 적용해 대부분의 에러를 컴파일 환경에서 코드를 입력하는 동안 체크 할 수 있다.

---

### **타입 지정**

타입스크립트는 일반 변수, 매개 변수, 객체 속성등에 `:TYPE` 과 같은 형태로 타입을 지정할 수 있다.

```jsx
function someFunc(a:TYPE_A, b:TYPE_B): TYPE_RETURN {
  return a + b;
}
let some:TYPE_SOME = someFunc(1, 2);

///ts
function add(a:number, b: number) {
  return a + b;
}
const sum:number = add(1, 2);
console.log(sum) //3

//js로 컴파일 하면...
""use strict"
function add(a, b) {
  return a + b;
}
const sum = add(1, 2);
console.log(sum); //3
1
```

---

### **타입 에러**

만약 다음과 같이 sum을 number가 아닌 string 타입이라고 지정했다면, 컴파일 조차 하지 않고 코드를 작성하는 시점에 에러가 발생한다.

```jsx
function add(a: number, b: number) {
  return a + b;
}
const sum: string = add(1, 2);
console.log(sum);
// TS2322: Type 'number' is not assignable to type 'string'.
```

---

### **타입 선언**

- **불린:Boolean**

  참 / 거짓으로 값을 나타낸다.

  ```jsx
  let isBoolean: boolean;
  let isDone: boolean = false;
  ```

- **숫자:Number**

  모든 부동 소수점 값을 사용할 수 있다.

  ```jsx
  let num: number;
  let integer: number = 6;
  let float: number = 3.14;
  let hex: number = 0xf00d; // 61453
  let binary: number = 0b1010; // 10
  let octal: number = 0o744; // 484
  let infinity: number = Infinity;
  let nan: number = NaN;
  ```

- **문자열:String**

  문자열을 나타낸다.

  ```jsx
  let str: string;
  let red: string = "Red";
  let green: string = "Green";
  let myColor: string = `My color is ${red}.`;
  let yourColor: string = "Your color is" + green;
  ```

- **배열:Array**

  순차적으로 값을 가지는 일반 배열을 나타낸다.

  ```jsx
  // 문자열만 가지는 배열
  let fruits: string[] = ["Dog", "Cat", "Snake"];
  // Or
  let fruits: Array<string> = ["Dog", "Cat", "Snake"];

  // 숫자만 가지는 배열
  let oneToSeven: number[] = [1, 2, 3, 4, 5, 6, 7];
  // Or
  let oneToSeven: Array<number> = [1, 2, 3, 4, 5, 6, 7];
  ```

  문자열과 숫자를 동시에 가지는 배열도 선언 할 수 있다.

  ```jsx
  let array: string | number = ["Dog", 1, 2, "Cat", "Snake", 3];
  ```

  배열이 가는 항목의 값을 단언할 수 없다면 `any` 를 사용할 수 있다.

  ```jsx
  let someArr = any[] = [0, 1, {}. [], 'str', false];
  ```

  인터페이스나 커스텀 타입을 사용할 수도 있다.

  ```jsx

  let userArr: IUser[] = {
    interface IUser {
    name: string,
    age: number,
    isValid: boolean
  }

  let userArr: IUser[] = [
    {
      name: 'Neo',
      age: 85,
      isValid: true
    },
    {
      name: 'Lewis',
      age: 52,
      isValid: false
    },
    {
      name: 'Evan',
      age: 36,
      isValid: true
    }
  ];
  ```

  읽기 전용 배열을 생성할 수도 있다.

  ```jsx
  let arrA: readonly number[] = [1, 2, 3, 4];
  let arrB: ReadonlyArray<number> = [o, 9, 8, 7];
  ```

- **튜플:Tupple**

  배열과 매우 유사하다 차이점이라면 정해진 고정된 길이 배열을 표현한다.

  ```jsx
  let tuple: [string, number];
  tuple = ["a", 1];
  tuple = ["a", 1, 2]; // Error - TS2322
  tuple = [1, "a"]; // Error - TS2322
  ```

  데이터를 개별 변수로 지정하지 않고, 단일 Tuple로 지정해 사용할 수 있다.

  ```jsx
  // Variables
  let userId: number = 1234;
  let userName: string = "HEROPY";
  let isValid: boolean = true;

  // Tuple
  let user: [number, string, boolean] = [1234, "HEROPY", true];
  console.log(user[0]); // 1234
  console.log(user[1]); // 'HEROPY'
  console.log(user[2]); // true
  ```

  2차원 배열에서도 사용할 수 있다.

  ```jsx
  let users: [number, string, boolean][];
  // Or
  // let users: Array<[number, string, boolean]>;

  users = [
    [1, "Neo", true],
    [2, "Evan", false],
    [3, "Lewis", true],
  ];
  ```

- **열거형:Enum**

  숫자 혹은 문자열 값 집합에 이름을 부여할 수 있는 타입으로, 값의 종류가 일정한 범위로 정해져 있는 경우 유요하다.

  기본적으로 0 부터 시작하며 값은 1씩 증가한다.

  ```jsx
  enum Color {
    Red = 'red',
    Green = 'green',
    Blue = 'blue'
  }
  console.log(Color.Red); // red
  console.log(Color['Green']); // green
  ```

- **모든 타입:Any**

  Any는 모든 타입을 의미한다.
  따라서 자바스크립트 변수와 동일하게 어떤 타입의 값도 할당할 수 있다.

  ```jsx
  let result: any = 123;
  result = "Hello world";
  result = {};
  result = null;
  ```

  다양한 값을 포함하는 배열을 나타낼 때 사용할 수도 있다.

  ```jsx
  const list: any[] = [1, true, "Anything!"];
  ```

  강한 타입 시스템의 장점을 유지하기 위해 Any 사용을 엄격하게 금지하려면, 컴파일 옵션

  `noImplicitAny: true`를 통해 Any 사용 시 에러를 발생시킬 수 있다.

- **알 수 없는 타입: Unknown**

  Any와 같이 최상위 타입인 Unknown은 알 수 없는 타입을 의미한다.
  Any와 같이 Unknown에는 어떤 타입의 값도 할당훌 수 있지만, Unknown은 다른 타입에는 할당 할 수 없다.

  ```jsx
  let a: any = 123;
  let b: unknown = 123;

  let v1: boolean = a; //할당 가능
  let v2: number = b; // any타입을 제외한 다른 타입에 할당 할 수 없다.

  let v3: any = b; //할당 가능
  let v4: number = b as number // 타입을 단언하면 할당할 수 있다.
  ```

  다양한 타입을 반환할 수 있는 API에서 유용할 수 있다.

- **객체:Object**

  기본적으로 `typeof` 연산자가 `"object"` 로 반환하는 모든 타입을 나타낸다.

  컴파일러 옵션에서 엄격한 타입검사를 `true`로 설정하면, `null` 은 포함되지 않는다.

  ```jsx
  let obj: object = {};
  let arr: object = [];
  let func: object = function () {};
  let nullValue: object = null;
  let date: object = new Date();
  ```

  여러 타입의 상위 타입이기 때문에 그다지 유용하지 않다.
  보다 정확하게 타입 지정을 하기 위해서는 객체 속성에 대한 타입을 개별적으로 지정하는게 좋다.

  ```jsx
  let userA: {name: string, age: number} = {
    name = 'LEE',
    age: 20
  };

  let userB: {name: string, age: number} = {
    name 'LEE',
    age: false, // Error
    email: 'abc123@defg.oi' // Error
  }
  ```

  반복으로 사용할 경우 `interface` `type` 을 사용하는 것을 추천한다.

  ```jsx
  interface IUser {
    name: string;
    age: number;
  }

  let userA: IUser = {
    name: "LEE",
    age: 20,
  };

  let userB: IUser = {
    name: "LEE",
    age: false, // Error
    email: "abc123@defg.oi", // Error
  };
  ```

- **Null과 Undefined**

  null 과 undefined는 모든 타입의 하위 타입으로, 각 타입의 할당 할 수 있다.
  컴파일 옵션 `"stricNullChecks": true` 을 통해 엄격하게 Null과 Undefined 서로의 타입까지 더 이상 할당 할 수 없게 합니다.

  단, Void에는 Undefined를 할당 할 수 있다.

- **Void**

  void는 일반적으로 값을 반환하지 않는 함수에서 사용한다.
  `:void` 위치는 함수가 반환 타입을 명시 하는 곳이다.

  ```jsx
  function hello(msg: string) void {
    console.log(`Hello ${msg}`)
  }
  ```

  값을 반환하지 않는 함수는 실제로 **`undefined`**를 반환한다.

- **Never**

  Never은 절대 발생하지 않을 값을 나타내며, 어떠한 타입도 적용할 수 없다.

  ```jsx
  function error(message: string): never {
    throw new Error(message);
  }
  ```

- **유니언(Union)**

  2개 이상의 타입을 허용한 경우, 이를 유니언이라고 한다.

  `|` 를 통해 타입을 구분하며, `()` 는 선택 사항이다.

  ```jsx
  let union: string | number;
  union = "Hello type!";
  union = 123;
  union = false; // Error - TS2322: Type 'false' is not assignable to type 'string | number'.
  ```

- **인터섹션(Intersection)**

  `&` 를 사용해 2개 이상의 타입을 조합하는 경우, 이를 인터섹션 이라고 한다.
  인터섹션은 새로운 타입을 생성하지 않고 기존의 타입들을 조합할 수 있기 때문에 유용하지만, 자주 사용되지는 방법이다.

  ```jsx
  // 기존 타입들이 조합 가능하다면 인터섹션을 활용할 수 있다.
  interface IUser {
    name: string;
    age: number;
  }
  interface IValidation {
    isValid: boolean;
  }
  const heropy: IUser = {
    name: "Heropy",
    age: 36,
    isValid: true, // Error -  TS2322: Type '{ name: string; age: number; isValid: boolean; }' is not assignable to type 'IUser'.
  };
  const neo: IUser & IValidation = {
    name: "Neo",
    age: 85,
    isValid: true,
  };

  // 혹은 기존 타입(IUser, IValidation)과 비슷하지만, 정확히 일치하는 타입이 없다면 새로운 타입을 생성해야 한다.
  interface IUserNew {
    name: string;
    age: number;
    isValid: boolean;
  }
  const evan: IUserNew = {
    name: "Evan",
    age: 36,
    isValid: false,
  };
  ```

- **함수(Function)**

  화살표 함수를 이용해 타입을 지정할 수 있다.
  인수의 타입과 반환 값의 타입을 입력한다.

  ```jsx
  //myFunc는 2개의 숫자 타입 인수를 가지고, 숫자 타입을 반환하는 함수
  let myFunc(arg1: number ,arg2: number) => number;
  myFunc = function (x, y) {
    return x + y;
  }

  //인수가 없고, 반환도 없는 경우
  let yourFunc: () => void;
  yourFunc = function() {
    console.log('Hello world~');
  }
  ```

---

### 타입추론(Inference)

**명시적으로 타입 선언이 되어있지 않은 경우, 타입스크립트는 타입을 추론해 제공한다.**

`추론: 어떠한 판단을 근거로 삼아 다른 판단을 이끌어 냄`

```jsx
let num = 30;
num = "Hello type!"; // TS2322: Type '"Hello type!"' is not assignable to type 'number'.
```

변수 `num` 을 숫자 30를 할당해 number 타입으로 추론되 었고 따라서 `"Hello type"` 이라는 string 타입의 값은 할달 수 없게 되었다 오류가 난다.

**이렇게 타입스크립트가 타입을 추론하는 경우는 다음과 같다.**

- 초기화된 변수
- 기본값이 설정된 매개변수
- 반환 값이 있는 함수

---

### 타입 단언(Assertions)

타입스크립트가 타입 추론의 범주를 넘었을 경우, 더 이상 추론하지 않도록 지시할 수 있다.

이를 **타입 단언**이라고 \*\*\*\*하며, 이는 프로그래머가 타입스트립트 보다 타입에 대해 잘 이해하고 있는 상황을 의미한다.

`단언:주저하지 아니하고 딱 잘라 말함.`

---

### 타입 가드(Guards)

다음 예제와 같이 val의 타입을 매번 보장하기 위해 타입 단언을 여러 번 사용하게 되는 경우가 있다.

```jsx
function someFunc(val: string | number, isNumber: boolean) {
  if (isNumber) {
    (val as number).toFixed(2);
    isNaN(val as number);
  } else {
    (val as string).split('');
    (val as string).toUpperCase();
    (val as string).length;
  }
}
```

이 경우 타입 가드를 제공하면 타입스크립트가 추론 가능한 거리 특정한 범위(scope)에서 타입을 보장할 수 있다.

타입 가드는 `NAME is TYPE` 형태의 타입 술부**(Predicate)**를 반환 타입으로 명시한 함수이다.

`술부: 주어의 상태, 성질 따위를 서술하는 말`

```jsx
// 타입 가드
function isNumber(val: string | number): val is number {
  return typeof val === 'number';
}

function someFunc(val: string | number) {
  if (isNumber(val)) {
    val.toFixed(2);
    isNaN(val);
  } else {
    val.split('');
    val.toUpperCase();
    val.length;
  }
}
```

---

### 인터페이스(Interface)

인터페이스는 타입스크립트 여러 객체를 정의하는 일종의 규칙이며 구조이다.

```jsx
interface IUser {
  name: string;
  age: number;
  isAdult: boolean;
}

let user1: IUser = {
  name: "Neo",
  age: 123,
  isAdult: true,
};

// Error - TS2741: Property 'isAdult' is missing in type '{ name: string; age: number; }' but required in type 'IUser'.
let user2: IUser = {
  name: "Evan",
  age: 456,
};
```

`:` `,` 혹은 기호를 사용하지 않을 수 있다.

```jsx
interface IUser {
  name: string,
  age: number
}
// Or
interface IUser {
  name: string;
  age: number;
}
// Or
interface IUser {
  name: string
  age: number
}
```

옵셔널로 타입 뒤에 `?` 를 넣으면 생략해도 오류가 나지 않는다.

```jsx
interface IUser {
  name: string;
  age: number;
  isAdult?: boolean; // Optional property
}

// `isAdult`를 초기화하지 않아도 에러가 발생하지 않습니다.
let user: IUser = {
  name: "Neo",
  age: 123,
};
```

---

### 제네릭(Generic)

재사용 목적으로 함수나 클래스의 선언이 아닌, 사용 시점에 타입을 선언할 수 있는 방법을 제공한다.

_`타입을 인수로 받아서 사용한다고 이해하면 쉽다.`_

`toArray` 함수가 인수로 받은 값을 배열로 반환하도록 작성되었다.
매개변수가 `number` 타입만 받도록 되어있어서 `string`타입은 오류가 난다.

```jsx
function toArray(a: number, b: number): number[] {
  return [a, b];
}
toArray(1, 2);
toArray("1", "2"); /* Error - TS2345: Argument of type '"1"' is not assignable 
to parameter of type 'number'. */
```

이번에는 Generic을 사용한다.

함수 이름 우측에 `<T>` 를 작성해 시작한다.

`T` 는 타입 변수(Type variable)로 사용자가 제공한 타입으로 변환될 식별자이다.

`타입 변수는 매개 변수처럼 원하는 이름으로 지정할 수 있다.`

```jsx
function toArray<T>(a: T. b: T): T[] {
  return [a, b];
}

toArray<number>(1, 2);
toArray<string>("1", "2");
toArray<number | string>(1, "2");
toArray<number>(1, "2"); //Error
```

타입 추론을 활용해, 사용 시점에 타입을 제공하지 않을 수 있다.

```jsx
function toArray<T>(a: T, b: T): T[] {
  return [a, b];
}

toArray(1, 2);
toArray("1", "2");
toArray(1, "2"); // Error
```

**제약 조건(Constraints)**

인터페이스나 타입 별칭을 사용하는 제네릭을 작성할 수도 있다.

타입변수 `T` 가 `string` 과 `number` 인 경우만 허용하려면 `extends` 키워드를 사용하는 제약 조건을 추가 할 수 있다.

```jsx
T extends U

interface MyType<T extends string | number> {
	name: string,
	value: T
}

const DataA: MyType<string> = {
	name: "Data A",
	value: "1234"
}

const DataB: MyType<number> = {
	name: "Data B",
	value: 1234
}

const DataC: MyType<boolean> = { //TS2344: Type 'boolean' does not satisfy the constraint 'string | number'.
	name: "Data C",
	value: true
}
```

**조건부 타입(Conditional Types)**

제약 조건과 다르게 타입 구현 영역에서는 `extends` 는 삼항 연산자를 사용할 수 있다.

```jsx
T extends U ? X : Y

type U = string | number | boolean

//type 식별자 = 타입 구현
type MyType<T> = T extends U ? string : never;

// interface 식별자 {타입구현}
interface IUser<T extends boolean> {
  name:string,
  age: T extends true ? string : number //T 타입이 ture인 경우 string 반환 아닌경우 number 반환.
}

const str: IUser<true> = {
	name: "Lee",
  age: "20", //string
  isString: true
}

const num: IUser<false> = {
  name: 'Eun',
  age: 20, //number
  isString: false
}
```

**infer**

`infer` 키워드를 사용해 타입 변수의 타입 추론 여부를 확인 할 수 있다.

```jsx
//U가 추론 가능한 타입이면 참, 아니면 거짓
T extends infer U ? X : Y
```

---

### 함수

**오버로드**(**Overloads)**

타입스크립트의 함수 오버로드는 매개변수 타입과 반환 타입이 다른 여러 함수를 가질수 있는 것을 말한다.
함수 오버로드를 통해 다양한 구조의 함수를 생성하고 관리할 수 있다.

```jsx
function add(a: string, b: string): string; //함수 선언
function add(a: number, b: number): number; //함수 선언
function add(a: any, b: any): any { //함수 구현
  return a + b;
}

add("Hello", "World");
add(1, 2)
add("Hello", 2) // Error - No overload matches this call.
```

인터페이스나 별칭 등의 메소드 정의에도 오버로드를 활용할 수 있다.
타입 단언이나 타입가드를 통해 함수 선언부의 동적인 매개변수와 반환 값을 정의할 수 있다.

```jsx
interface IUser {
  name: string;
  age: number;
  getData(x: string): string[];
  getData(x: number): string;
}

let user: IUser = {
  name: "Lee",
  age: 20,
  getData: (data: any) => {
    if (typeof data === "string") {
      return data.split("");
    } else {
      return data.toString();
    }
  },
};

user.getData("Hello"); // ['h', 'e', 'l', 'l', 'o']
user.getData(123); // '123'
```

---

### 클래스

클래스의 생성자 메소드(`constructor`)와 일반 메소드 멤버와는 다르게, 속성은 `name:string;` 와 같이 클래스 바디에 별도로 타입을 선언한다.

```jsx
class Animal {
  name: string;
  constructor(name: string) {
    this.name = name;
  }
}
class Cat extends Animal {
  getName(): string {
    return `Cat name is ${this.name}.`;
  }
}

let cat: Cat;
cat = new Cat("Lucy");
console.log(cat.getName()); // Cat name is Lucy.
```

**클래스 수식어**

클래스 멤버(속성, 메소드)에서 사용할 수 있는 접근 제어자들이 있다.

`접근 제어자는 클래스, 메서드 및 기타 멤버의 접근 가능성을 설정하는 객체 지향 언어의 키워드 이다.`

[접근 제어자](https://www.notion.so/46db9ac1796b4d37a8f9c31834376482)

다음 수식어는 접근제어자와 함께 사용 가능하다.
`static` 의 경우 정적 메소드뿐만 아니라 정적 속성도 사용할 수 있다.

[수식어](https://www.notion.so/9e5ccdfd289243ca82ae0bac8048e9f3)

`Animal`클래스의 속성은 `public` 이기 때문에 파생된 자식 클래스 `Cat`에서 `[this.name](http://this.name)` 으로 참조하거나 인스턴스에서 `[cat.name](http://cat.name)` 으로 접근하는데 아무런 문제가 없다.

```jsx
class Animal {
  public name:string;
  construtor(name: string) {
		this.name = name
  }
}
class Cat extends Animal {
  getName(): string {
		return `Cat name is ${this.name}.`;
	}
}

let cat = new Cat('Lucy');
console.log(getName()); //Cat name is Lucy.

cat.name = 'John';
console.log(cat.getName()); //Cat name is John.

```

다음은 `Animal`클래스의 속성은 `protected` 이기 때문에 파생된 자식 클래스 `Cat`에서 `[this.name](http://this.name)` 으로 참조할 수는 있지만, 인스턴스에서 `[cat.name](http://cat.name)` 으로 접근할 수 없다.

```jsx
class Animal {
  protected name:string;
  construtor(name: string) {
		this.name = name
  }
}
class Cat extends Animal {
  getName(): string {
		return `Cat name is ${this.name}.`;
	}
}

let cat = new Cat('Lucy');
console.log(getName()); //Cat name is Lucy.
console.log(cat.name); //Error

```

다음은 `Animal`클래스의 속성은 `private` 이기 때문에 파생된 자식 클래스 `Cat`에서 `[this.name](http://this.name)` 으로 참조할 수는 없고, 인스턴스에서도 `[cat.name](http://cat.name)` 으로 접근할 수 없다.

```jsx
class Animal {
  protected name:string;
  construtor(name: string) {
		this.name = name
  }
}
class Cat extends Animal {
  getName(): string {
		return `Cat name is ${this.name}.`; //Error
	}
}

let cat = new Cat('Lucy');
console.log(getName());
console.log(cat.name); //Error

```

**추상(Abstract)클래스**

추상 클래스는 다른 클래스가 파생될 수 있는 기본 클래스로 인터페이스와 유사하다.
`abstract` 는 클래스 뿐만 아니라 속성과 메소드에도 사용 할 수 있다.
추상 클래스는 직접 인스턴스를 생성 할 수 없기 때문에 파생된 후손 클래스에서 인스턴스를 생성해야 한다.

```jsx
//Abstract Class
abstract class Animal {
 abstract name:string; //파생된 클래스에서 구현해야 한다.
 abstract getName(): string; //파생된 클래스에서 구현해야 한다.
}

class Cat extends Animal {
  constructor(public name: string) {
		super();
  }
  getName() {
		return this.name;
	}
}
new Animal(); //Error

const cat = new Cat('Lucy');
console.log(cat.getName()) // Lucy

//interface
interface IAnimal {
  name: string;
	getName(): string;
}

class Dog extends Animal {
  constructor(public name: string) {}
  getName() {
		return this.name;
  }
}
```

추상클래스가 인터페이스와 다른점은 속성, 메소드, 멤버에 대한 세부 구현이 가능하다는 점이다.
