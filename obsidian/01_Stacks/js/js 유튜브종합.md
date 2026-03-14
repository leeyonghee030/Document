
---

# 📚 JavaScript 종합 학습 노트 (Full Guide)

이 노트는 자바스크립트의 기초 문법부터 객체 지향(OOP), 동작 원리(Closure, Prototype), 그리고 비동기 프로그래밍까지의 전체 과정을 다룹니다.

---

## 🟦 Part 1. 자바스크립트 기초 원리와 문법

### 1.1 메모리 (Memory) 이해

컴퓨터가 데이터를 저장하는 물리적인 방식입니다.

- **메모리 셀**: 메모리는 수많은 칸(셀)으로 나뉘어 있으며, 각 셀은 데이터를 저장하는 공간입니다.
    
- **주소(Address)**: 각 셀은 0부터 시작하는 고유한 번호를 가집니다.
    
- **크기**: 각 메모리 셀은 **1바이트(8비트)** 크기를 가집니다.
    
- **특징**: 데이터(숫자, 문자 등)는 이 셀에 2진수 형태로 저장됩니다.
    

### 1.2 변수 이름 짓기 (Naming Rules)

- **✅ 가능**: 영어, 숫자, `_` (언더바), `$` (달러 표시).
    
- **❌ 불가능**:
    
    - 숫자로 시작하는 이름 (예: `1apple` X).
        
    - 자바스크립트 예약어(키워드) 사용 (예: `let`, `if`, `const` X).
        

### 1.3 네이밍 컨벤션 (Naming Convention)

- **camelCase**: 첫 단어는 소문자, 다음 단어부터 대문자 (예: `isGoodDay`). -> **자바스크립트 표준**.
    
- **snake_case**: 단어 사이에 언더바 사용 (예: `is_good_day`). -> **파이썬 스타일**.
    
- **PascalCase**: 모든 단어 첫 글자 대문자 (예: `IsGoodDay`). -> **C# / 클래스명**.
    

### 1.4 데이터 타입 (Data Types)

자바스크립트에는 **6개의 프리미티브 타입**과 **1개의 오브젝트 타입**이 존재합니다.

- **Number**: 정수, 음수, 실수뿐만 아니라 `Infinity`(무한대), `NaN`(숫자가 아님)을 포함합니다.
    
- **String**: `' '` 또는 `" "`를 사용하며, 백틱(`` ` ``)을 사용한 **Template Literal**은 `${변수}` 삽입과 줄바꿈이 자유롭습니다.
    
- **undefined**: 사용자가 값을 직접 초기화하지 않았을 때 자동으로 지정되는 값입니다.
    
- **null**: 개발자가 의도적으로 "값이 없음"을 나타내기 위해 명시적으로 사용하는 값입니다.
    
- **Object (객체)**: 키와 값의 쌍(`key:value`)으로 이루어진 집합입니다.
    
- **Array (배열)**: 값을 리스트로 나열한 타입으로, 인덱스는 **0부터 시작**합니다.
    

### 1.5 연산자 (Operators)

#### 증감 연산자 위치의 차이

- `result = number++`: **현재 값**을 먼저 `result`에 넣고 나서 `number`를 증가시킵니다.
    
- `result = ++number`: `number`를 **먼저 증가**시킨 후 그 결과를 `result`에 넣습니다.
    

#### 비교 및 논리 연산자

- **비교**: `==` (값만 비교), **`===` (값과 타입 모두 비교 - 강력 추천)**.
    
- **삼항 연산자**: `조건 ? 참일 때 : 거짓일 때` (예: `10 > 0 ? '큼' : '작음'`).
    
- **단축 평가**: `&&`(좌측 True면 우측 반환), `||`(좌측 True면 좌측 반환).
    

#### Null 병합 (`??`)

왼쪽 값이 `null`이나 `undefined`일 때만 오른쪽 값을 선택합니다.

JavaScript

```
let nickname = null;
let defaultName = "익명";

// nickname이 null이므로 "익명"이 저장됨
let result = nickname ?? defaultName; 
console.log(result); // "익명"

nickname = "자바최고";
// nickname에 값이 있으므로 "자바최고"가 저장됨
result = nickname ?? defaultName;
console.log(result); // "자바최고"
```

### 1.6 제어문 (Control Flow)

- **if...else if...else**: 조건의 참/거짓에 따라 실행 흐름을 나눕니다.
    
- **Switch**: 특정 **값**에 따라 케이스를 나눕니다. (`break` 필수).
    
- **Loops**:
    
    - `for`: 정해진 횟수만큼 반복.
        
    - `while`: 조건을 먼저 확인.
        
    - `do...while`: 일단 1번 실행 후 조건 확인.
        
    - `for...in`: 객체의 **키(Key)**나 배열의 **인덱스** 반복.
        
    - `for...of`: 배열의 실제 **값(Value)** 반복.
        

---

## 🟧 Part 2. 타입 변환, 함수, 배열, 객체 심화

### 2.1 타입 변환 (Type Coercion)

자바스크립트는 데이터의 타입이 상황에 따라 유연하게 변합니다.

#### 1) 명시적 변환 (Explicit)

JavaScript

```
let age = 32;
// 숫자를 문자열로
let stringAge = age.toString(); 
// 문자를 숫자로
console.log(parseInt('0')); // 0
```

#### 2) 암묵적 변환 (Implicit)

JavaScript

```
let test = age + ''; // 숫자 + 문자열 = 문자열
console.log('98' + 2); // '982' (문자열 연결 우선)
console.log('98' * 2); // 196 (곱하기는 숫자로 변환)
```

#### 3) Truthy vs Falsy

`!!` 연산자를 사용해 Boolean으로 변환할 때의 규칙입니다.

- **🔴 Falsy (거짓)**: `false`, `0`, `''`(빈문자열), `null`, `undefined`, `NaN`.
    
- **🟢 Truthy (참)**: Falsy를 제외한 모든 값. `'0'`, `'false'`, `[]`, `{}`(빈 객체)는 **True**입니다.
    

### 2.2 함수 (Function)

#### 1) 기본 및 Default Parameter

JavaScript

```
// y에 값이 안 들어오면 기본값 10 사용
function multiply(x, y = 10) {
    return x * y;
}
console.log(multiply(2)); // 20
```

#### 2) Arrow Function (화살표 함수)

JavaScript

```
// 기본형
const multiply2 = (x, y) => { return x * y; };
// 생략형 (return 생략 가능)
const multiply3 = (x, y) => x * y;
// 커링 (함수를 리턴하는 함수)
const multiply5 = x => y => z => `x: ${x} y: ${y} z: ${z}`;
```

#### 3) Rest Parameters

JavaScript

```
const multiplyAll = function(...args) {
    // args는 [3, 4, 5]와 같은 배열이 됨
    return args.reduce((a, b) => a * b, 1);
};
console.log(multiplyAll(3, 4, 5)); // 60
```

### 2.3 배열 (Array) 함수

배열 함수는 원본 변경 여부가 핵심입니다.

- **🔴 Mutable (원본 변경)**: `push`, `pop`, `shift`, `unshift`, `splice`, `sort`, `reverse`.
    
- **🟢 Immutable (새 배열 반환)**: `concat`, `slice`, `join`, `map`, `filter`.
    

#### Sort & Map 예시

JavaScript

```
const numbers = [1, 10, 5, 3];
// 오름차순 정렬
numbers.sort((a, b) => a - b); 

// Map: 모든 요소를 변환
// Filter: 조건에 맞는 요소만 추출
// Reduce: 요소를 하나로 합침
```

### 2.4 객체 (Object) & 복사

- **const와 객체**: `const`로 선언해도 객체 내부의 프로퍼티(`student.name`)는 변경 가능합니다.
    
- **참조 복사 주의**: 객체는 변수에 할당할 때 **주소값**이 복사됩니다.
    

JavaScript

```
let original = { name: 'A' };
let clone = original; // 주소만 복사됨
clone.name = 'B';
console.log(original.name); // 'B' (원본도 같이 바뀜!)

// 💡 얕은 복사 해결책: Spread Operator
let safeClone = { ...original };
```

### 2.5 에러 핸들링 (Try-Catch)

JavaScript

```
try {
    throw new Error('🔴 의도적인 에러 발생!'); 
} catch (e) {
    console.log(e.message); 
} finally {
    console.log('무조건 실행');
}
```

---

## 🟩 Part 3. Class & OOP (객체 지향 프로그래밍)

### 3.1 Class Keyword & Constructor

클래스는 객체(인스턴스)를 생성하기 위한 틀입니다.

JavaScript

```
class IdolModel {
    name; year;

    // 생성자: 인스턴스 초기화
    constructor(name, year) {
        this.name = name;
        this.year = year;
    }

    sayName() {
        return `안녕하세요 ${this.name}입니다.`;
    }
}
const yuJin = new IdolModel('안유진', 2003);
```

### 3.2 Getter and Setter

JavaScript

```
class IdolModel {
    #name; // Private 필드 (#)
    year;
    constructor(name, year) { this.#name = name; this.year = year; }

    get nameAndYear() { return `${this.#name}-${this.year}`; }
    set setName(name) { this.#name = name; }
}
const idol = new IdolModel('가을', 2002);
console.log(idol.nameAndYear); // 변수처럼 호출
```

### 3.3 Static & Factory Constructor

`static`은 인스턴스가 아닌 클래스 자체에 귀속됩니다.

JavaScript

```
class IdolModel {
    name; year;
    static groupName = '아이브'; // 클래스 소유 변수

    constructor(name, year) { this.name = name; this.year = year; }

    // Factory Constructor: 다양한 입력 방식으로 객체 생성 지원
    static fromObject(object) {
        return new IdolModel(object.name, object.year);
    }
}
const yuJin = IdolModel.fromObject({name: '안유진', year: 2003});
```

### 3.4 Inheritance (상속) & Override

`extends`로 상속받고, `super`로 부모에 접근하며, 메소드를 `Override`(재정의) 할 수 있습니다.

JavaScript

```
class FemaleIdolModel extends IdolModel {
    part;
    constructor(name, year, part) {
        super(name, year); // 부모 생성자 호출 필수
        this.part = part;
    }
    
    // 오버라이딩
    sayHello() {
        return `${super.sayHello()} ${this.part}를 맡고있습니다.`;
    }
}
```

---

## 🟪 Part 4. 자바스크립트 동작 원리 심화

### 4.1 객체 심화 (Object Detail)

- **생성 방법**: Object Literal `{}`, Class `new`, Constructor Function `new func()`.
    
- **Property Attribute**: `value`, `writable`(수정가능여부), `enumerable`(열거가능여부), `configurable`(재정의가능여부).
    
- **Immutable Object**:
    
    - `Extensible`: 추가 불가.
        
    - `Seal`: 추가/삭제 불가.
        
    - `Freeze`: **읽기 전용** (수정/추가/삭제 불가).
        

### 4.2 Prototype Chain

- **`__proto__`**: 모든 객체가 가진 속성, 부모를 가리킴.
    
- **`prototype`**: 함수(클래스)만 가진 속성, 인스턴스의 원형.
    
- **장점**: 메모리 절약 (메소드 공유).
    

### 4.3 Execution Context & Closure 💡

**클로저(Closure)**는 함수가 선언된 렉시컬 환경을 기억하여, 외부 함수가 종료되어도 변수에 접근할 수 있는 현상입니다.

#### [예제 1] 데이터 은닉 (Private Variable)

JavaScript

```
function createCounter() {
    let count = 0; // 은닉된 변수

    return {
        increment: function() {
            count++;
            console.log(`현재 값: ${count}`);
        },
        getCount: function() { return count; }
    };
}
const counter = createCounter(); 
counter.increment(); // 1
console.log(counter.count); // undefined (직접 접근 불가)
```

#### [예제 2] 상태 유지 (React Hook 원리)

JavaScript

```
function idGenerator() {
    let id = 1; // 상태 기억
    return function() {
        return id++; 
    }
}
const generateId = idGenerator();
console.log(generateId()); // 1
console.log(generateId()); // 2 (id 변수 살아있음)
```

---

## 🟥 Part 5. 비동기 프로그래밍 (Async)

### 5.1 Event Loop & Thread

자바스크립트는 **Single Thread**이지만 **Event Loop**를 통해 비동기 작업을 처리합니다.

### 5.2 Promise 💡

비동기 작업의 성공/실패를 다루는 객체입니다. '콜백 지옥'을 해결합니다.

JavaScript

```
// 1. 주문 (2초 소요)
const order = () => new Promise((resolve, reject) => {
    setTimeout(() => { resolve("주문 완료"); }, 2000);
});

// 2. 결제 (1초 소요)
const pay = (res) => new Promise((resolve) => {
    setTimeout(() => { resolve("결제 완료"); }, 1000);
});

// Chaining
order()
    .then(res => pay(res))
    .then(res => console.log("배달 시작!"))
    .catch(err => console.log("에러:", err));
```

### 5.3 Async / Await

Promise를 동기 코드처럼 보이게 만드는 문법입니다. `try-catch`로 에러를 잡습니다.

JavaScript

```
async function runOrderSystem() {
    try {
        const orderResult = await order(); // 기다림
        console.log(orderResult);
        const payResult = await pay(orderResult); // 기다림
        console.log("배달 시작!");
    } catch (e) {
        console.log("오류 발생");
    }
}
runOrderSystem();
```