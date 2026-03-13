## 📋 웹 개발 기초 구조 및 CSS 정리 메모

다음은 요청하신 내용을 바탕으로 Markdown 파일 형식으로 정리한 메모입니다. 내용을 추가하거나 변경하지 않고, 원본 그대로 가독성을 살려 정리했습니다.

-----

### 🧱 Body 구조 정리 (구조적 태그)

웹사이트의 목적에 따라 구조가 달라집니다. 제목, 부제목, 단락 구조 (강조 UI에 따라)를 사용합니다.

  * `<div>`의 무분별한 사용보다는 **구조적 태그**를 활용합니다.
  * **페이지 맨 위:** `<header>` (네비게이션, 링크 포함)
  * **네비게이션/링크:** `<nav>`
  * **페이지 맨 아래:** `<footer>`
  * **주요 내용:** `<main>`
      * **메인 안 부가적 내용:** `<aside>` (종종 `<main>` 안에 배치)
      * **메인 안 독립적인 한 주제 나열:** `<article>` (스타일 X)
      * **특정한 챕터/영역:** `<section>`

-----

### 📝 태그 분류 정리

| 분류 | 설명 | 예시 태그 |
| :--- | :--- | :--- |
| **Element** / **특정 요소 태그** | 특정한 의미나 역할을 가지는 요소 | `h1-h6`, `address`, `blockquote`, `p`, `pre`, `a`, `abbr`, `table`, `ol`, `ul`, `span`, `cite`, `code`, `data`, `i`, `mark` |
| **Container** / **요소를 담는 태그** | 다른 요소들을 구조적으로 감싸는 컨테이너 | `div`, `section`, `article`, `header`, `footer`, `aside`, `nav`, `main` |
| **Block** / **Inline** | 한 줄 전체를 차지하는 요소 / 나란히 배치되는 요소 | **Block:** 한 줄 전체 차지 / **Inline:** 나란히 배치 |

-----

### 🌐 HTML 태그 참고 사이트

  * [HTML 시작하기 (MDN)](https://developer.mozilla.org/ko/docs/Learn/HTML/Introduction_to_HTML/Getting_started)
  * [HTML 요소 (MDN)](https://developer.mozilla.org/ko/docs/Web/HTML/Element)
  * [HTML Living Standard (WHATWG)](https://html.spec.whatwg.org/)

-----

### 🔎 사이트 구조 분해 (예시)

| 영역 | 태그 | 설명 |
| :--- | :--- | :--- |
| **헤더** | `<header>` | 페이지 상단 영역. |
| **탐색 바** | `<nav>` | 네비게이션 링크 모음. |
| **주요 콘텐츠** | `<main>` | 페이지의 핵심 내용. 다양한 하위 섹션은 `<article>`, `<section>`, `<div>` 요소로 표현됨. |
| **사이드바** | `<aside>` | 부가적인 내용. 종종 `<main>` 내부에 배치됨. |
| **바닥글** | `<footer>` | 페이지 맨 말단 영역. |

  * **개발자 도구 (Tool):** `Ctrl` + `Shift` + `I` (왼쪽 검사 기능)

-----

### 🎨 CSS 스타일 및 특징

#### 1\. CSS 기본 구문

```css
선택자 {
    속성1: "속성값1";
}
```

  * **선택자:** `태그이름`, `.클래스`, `#아이디`
  * **인라인 스타일:** `<태그 style="값:속성;">컨텐츠 내용</태그>`

#### 2\. CSS 특징 (우선순위)

CSS는 **우선순위**가 있는 스타일 시트입니다.

1.  **사용자 브라우저 셋팅**
2.  **작성한 코드**
3.  **브라우저 기본 스타일**

<!-- end list -->

  * **구체적인 것이 우선순위가 높습니다.**
    1.  `!important` (가장 높음)
    2.  **인라인 스타일**
    3.  `#아이디`
    4.  `.클래스`
    5.  **태그**
  * **동일한 레벨**일 경우 **나중에 작성한 것**이 우선순위가 더 높습니다.

#### 3\. Box Model (예시)

```css
box1, 3 {
    padding: 20px; /* 위, 아래, 양옆으로 내용에서 20px 간격 추가 */
    border: 5px solid black; /* 두께 5px, 실선 스타일, 검은색 테두리 */
}

/* 박스 크기 계산 방식 */
box-sizing: border-box;  /* 테두리(border)와 패딩(padding)이 전체 사이즈(width/height) 안에 포함 */
box-sizing: content-box; /* 기본값. 전체 사이즈 = 콘텐츠 크기 + 패딩 + 테두리 */
```