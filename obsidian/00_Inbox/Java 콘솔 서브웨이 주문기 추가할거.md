## 1단계: 제일 먼저 할 실습

## “콘솔 서브웨이 주문기” 만들기

처음엔 웹으로 가지 말고 **콘솔 프로그램**으로 만든다.

https://chatgpt.com/s/t_69bff1edeb5c81918148dd8e0882f816
(보고 내용확장하기)
### 목표

사용자가 숫자를 입력해서

- 샌드위치 선택
- 사이즈 선택
- 추가 재료 선택
- 최종 금액 확인

까지 되게 만들기

### 여기서 배우는 것

- 변수
- if / switch
- Scanner 입력
- 연산
- 출력

### 실습 예시

1. 에그마요  
2. 이탈리안 비엠티  
3. 로스트 치킨  
  
메뉴 번호를 선택하세요: 2  
사이즈를 선택하세요 (15cm / 30cm): 30  
치즈 추가? (y/n): y  
  
선택한 메뉴: 이탈리안 비엠티  
총 금액: 8900원


- 잘못된 입력 방지
- 객체화
- 리스트 기반 메뉴 관리
- Order / OrderItem 분리
- 
1. **네 현재 코드를 기준으로 입력 검증 버전으로 고쳐주기**
2. **이 코드를 Sandwich / OrderItem 구조로 바꾸는 방법 설명하기**
3. **네 코드에 주석을 더 자세히 달아서 복습용 버전으로 다시 정리해주기**

- **지금 코드에서 `if-else`도 없애고 Sandwich 배열/리스트로 바꾸기**
- **`OrderItem` 클래스까지 만들어서 주문 1개를 객체로 만들기**
- **입력 오류까지 막는 버전으로 업그레이드하기**


public class MenuOrder {  
  
static Sandwich eggMayo = new Sandwich("에그마요", 5800);  
static Sandwich bmt = new Sandwich("이탈리안 비엠티", 6000);  
static Sandwich chicken = new Sandwich("로스트 치킨", 6500);


while (isOrdering) {  
Sandwich currentSandwich = null;  
int currentItemPrice = 0;  
  
showMenu();  
int menuNum = selectMenu(sc);  
  
if (menuNum == 1) {  
currentSandwich = eggMayo;  
} else if (menuNum == 2) {  
currentSandwich = bmt;  
} else if (menuNum == 3) {  
currentSandwich = chicken;  
}  
  
if (currentSandwich == null) {  
System.out.println("잘못된 메뉴 번호입니다.");  
continue;



public static int selectSize(Scanner sc) {
    while (true) {
        System.out.print("사이즈 (1. 15cm / 2. 30cm): ");

        if (!sc.hasNextInt()) {
            System.out.println("숫자만 입력해주세요.");
            sc.next();
            continue;
        }

        int sizeNum = sc.nextInt();

        if (sizeNum == 1 || sizeNum == 2) {
            return sizeNum;
        } else {
            System.out.println("1 또는 2만 입력해주세요.");
        }
    }
}



public static boolean cheese(Scanner sc) {  
while (true) {  
System.out.print("치즈 추가? (y/n): ");  
String choice = sc.next();  
  
if (choice.equalsIgnoreCase("y")) {  
return true;  
} else if (choice.equalsIgnoreCase("n")) {  
return false;  
} else {  
System.out.println("y 또는 n만 입력해주세요.");  
}  
}  
}

boolean addCheese = cheese(sc);  
String cheeseText = addCheese ? "치즈추가" : "치즈x";  
if (addCheese) currentItemPrice += 500;