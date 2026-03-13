## 자바 변수

변수는 데이터 값을 저장하는 컨테이너입니다.

자바에는 다양한 **유형** 의 변수가 있습니다. 예를 들면 다음과 같습니다.

- `String`- "안녕하세요"와 같은 텍스트를 저장합니다. 문자열 값은 큰따옴표로 묶입니다.
- `int`- 소수점 이하 자릿수 없이 정수(자연수)를 저장합니다. 예를 들어 123 또는 -123과 같습니다.
- `float`- 19.99 또는 -19.99와 같이 소수점 이하 자릿수가 있는 부동 소수점 숫자를 저장합니다.
- `char`- 'a' 또는 'B'와 같은 단일 문자를 저장합니다. 문자 값은 작은따옴표로 묶입니다.
- `boolean`- 참 또는 거짓의 두 가지 상태를 갖는 값을 저장합니다.

type variableName = value;
```java
String name = "John";
System.out.println(name);
System.out.println("Hello " + name);

```

```java
String firstName = "John ";
String lastName = "Doe";
String fullName = firstName + lastName;
System.out.println(fullName);
```

 변수가 "final" 또는 "constant"로 선언되어 변경할 수 없고 읽기 전용이 됩니다.)

같은 코드 줄에 텍스트와 숫자를 함께 사용할 때는 주의해야 합니다. 괄호 없이 사용하면 Java는 첫 번째 문자열 이후의 숫자를 텍스트로 처리합니다.

```java
int x = 5;
int y = 6;

System.out.println("The sum is " + x + y);   // Prints: The sum is 56
System.out.println("The sum is " + (x + y)); // Prints: The sum is 11
```

자바 데이터유형 숫자