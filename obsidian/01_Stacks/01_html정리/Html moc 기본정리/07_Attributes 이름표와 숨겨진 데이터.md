> [!info] **학습 목표**
> 
> HTML 태그에 정체성을 부여하는 **ID와 Class**의 차이를 명확히 알고, 모든 태그에서 쓸 수 있는 **전역 속성**과 나만의 데이터를 저장하는 **Data 속성** 활용법을 익힙니다.

---

## 1. ID vs Class: 개별 정체성 vs 그룹 소속

HTML 요소에 이름을 붙이는 가장 대표적인 방법입니다. 프론트엔드 개발자에게는 '타겟팅'의 핵심 도구입니다.

### ① ID (`id`) : "이 구역의 미친 존재감은 나야"

- **특징**: 한 페이지 내에서 **중복될 수 없습니다.** 유일무이한 고유 식별자입니다.
    
- **용도**: 특정 요소 하나만 정확히 집어서 스타일을 주거나, 자바스크립트로 제어할 때 사용합니다.
    
- **예시**:
    
    HTML
    
    ```
    <header id="main-navigation"> ... </header>
    ```
    
    - CSS 선택자: `#main-navigation { ... }`
        

### ② Class (`class`) : "우리는 같은 스타일을 공유하는 동아리"

- **특징**: 여러 요소에 **중복해서 사용**할 수 있습니다. 한 요소가 여러 개의 클래스를 가질 수도 있습니다.
    
- **용도**: 공통된 스타일을 여러 곳에 한꺼번에 적용할 때 가장 많이 사용합니다.
    
- **예시**:
    
    HTML
    
    ```
    <button class="btn btn-blue">확인</button>
    <button class="btn btn-red">취소</button>
    ```
    
    - CSS 선택자: `.btn { font-size: 16px; }` (공통) / `.btn-blue { color: blue; }`
        

|**구분**|**ID**|**Class**|
|---|---|---|
|**중복 사용**|불가 (유일무이)|가능 (재사용)|
|**CSS 기호**|`#` (Hashtag)|`.` (Dot)|
|**우선순위**|높음 (Class보다 강함)|보통|

---

## 2. Global Attributes: 모든 태그의 공통 분모

어떤 태그를 쓰더라도 공통적으로 사용할 수 있는 '만능 옵션'들입니다.

- **`title`**: 요소 위에 마우스를 올렸을 때 나타나는 풍선 도움말(Tooltip)입니다.
    
    - `<span title="이것은 도움말입니다">마우스를 올려봐!</span>`
        
- **`lang`**: 해당 요소 내 콘텐츠의 언어를 지정합니다. (검색 엔진과 번역기 도움)
    
    - `<p lang="en">This is English.</p>`
        
- **`hidden`**: 요소를 화면에서 숨깁니다. CSS의 `display: none`과 비슷하게 작동합니다.
    
    - `<div hidden>아직 준비 중인 콘텐츠입니다.</div>`
        
- **`tabindex`**: 키보드 `Tab` 키를 눌렀을 때 포커스가 이동하는 순서를 정합니다. (웹 접근성 강화)
    
- **`style`**: 태그 안에 직접 디자인을 넣습니다. (하지만 실무에서는 지저분해져서 추천하지 않아요!)
    

---

## 3. Data-Attribute: 나만 아는 비밀 데이터 (`data-*`)

HTML에 표준에 없는 데이터를 저장하고 싶을 때 사용합니다. 사용자에게는 안 보이지만 개발자에게는 아주 유용한 저장소입니다.

- **형식**: `data-` 뒤에 원하는 이름을 붙여 사용합니다.
    
- **왜 쓰나요?**: 자바스크립트가 어떤 동작을 할 때 필요한 정보를 미리 HTML에 심어두기 위해서입니다.
    
- **예시**:
    
    HTML
    
    ```
    <ul>
      <li class="user-profile" data-user-id="1024" data-role="admin">홍길동</li>
      <li class="user-profile" data-user-id="2048" data-role="member">김철수</li>
    </ul>
    ```
    
- **JS 접근 방식**:
    
    JavaScript
    
    ```
    const user = document.querySelector('.user-profile');
    console.log(user.dataset.userId); // "1024" 출력
    ```
    

---

## 💡 프론트엔드 개발자의 실무 팁

1. **Naming Convention**: ID나 Class 이름은 보통 `kebab-case` (단어 사이에 하이픈 `-`)를 사용합니다. (예: `login-form`, `user-card-title`)
    
2. **의미 있는 이름**: `red-text`처럼 디자인을 이름으로 쓰지 말고, `error-message`처럼 **역할**을 이름으로 쓰세요. 디자인이 바뀌어도 이름은 그대로 쓸 수 있기 때문입니다.
    
3. **ID 남발 금지**: 스타일링을 할 때는 가급적 Class를 쓰세요. ID는 스타일 우선순위가 너무 높아 나중에 수정하기가 매우 까다롭습니다.