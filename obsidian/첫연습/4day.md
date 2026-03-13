# 🗒️ 개발 노트

## 5.14 쿨한 애니메이션 ✨

### CSS `@keyframes` 사용법

* **애니메이션 정의:** `@keyframes` 규칙을 사용하여 애니메이션의 중간 단계를 정의합니다.

    ```css
    @keyframes slidein {
      0% {
        border-radius: 0%;
        background-color: /* 시작 색상 */;
      }
      50% {
        background-color: /* 중간 색상 */;
      }
      100% {
        border-radius: 100%; /* + background-color: 최종 색상 */
      }
    }
    ```

* **요소에 적용:** 원하는 요소에 `animation` 속성을 사용해 적용합니다.
    * **기본 적용:**
        ```css
        원하는 요소에 {
          animation: 3s slidein;
        }
        ```
    * **반복 적용:**
        ```css
        원하는 요소에 {
          animation: 3s slidein infinite; /* infinite 추가 */
        }
        ```

* **추가 옵션:**
    * **`alternate`**: 애니메이션이 0%에서 100%로 진행된 후, 다시 100%에서 0%로 자연스럽게 역재생됩니다.

### 참고 자료

* [MDN Web Docs: CSS animation](https://developer.mozilla.org/en-US/docs/Web/CSS/animation)
* [MDN Web Docs: CSS @keyframes](https://developer.mozilla.org/en-US/docs/Web/CSS/@keyframes)

---

## 5.15 CSS 변수 (Custom Properties) 🎨

### 변수 정의

* **:root** 선택자를 사용하여 문서 전체에서 사용할 수 있는 전역 변수를 정의합니다. 변수명은 `--`로 시작합니다.

    ```css
    :root {
      --backround-color: #333; /* 예시 */
      --text-color: #fff; /* 예시 */
    }
    ```

### 변수 사용

* **`var()`** 함수를 사용하여 정의된 변수 값을 가져옵니다.

    ```css
    .first-list {
      background-color: var(--backround-color); /* :root에 정의된 배경색 사용 */
      color: whitesmoke;
      margin-left: 8px;
    }

    .second-list {
      background-color: var(--backround-color); /* :root에 정의된 배경색 사용 */
      color: var(--text-color); /* :root에 정의된 텍스트 색상 사용 */
      margin-left: 16px;
    }
    ```

### 미디어 쿼리에서 변수 변경

* 반응형 디자인을 위해 미디어 쿼리 내에서 변수 값을 재정의할 수 있습니다.

    ```css
    @media screen and (max-width: 768px) {
      :root {
        --backround-color: #007bff; /* 0-768px일 때 배경색 변경 */
        --text-color: #000; /* 0-768px일 때 텍스트 색상 변경 */
      }
    }
    ```

---

## 5.16 HTML `data-*` 속성 (Data Attributes) 💾

### HTML에 데이터 저장

* HTML 요소에 `data-` 접두사를 사용하여 사용자 정의 데이터를 저장할 수 있습니다.

    ```html
    <div data-index="1" data-display-name="dream">드림!!</div>

    <div data-index="2" data-display-name="coding">코딩!!</div>

    <span data-index="1" data-display-name="dream">드림!!</span>
    ```

### CSS에서 데이터 속성 활용

* 속성 선택자를 사용하여 특정 `data-*` 값을 가진 요소에 스타일을 적용합니다.

    ```css
    div[data-display-name='dream'] {
      background-color: gold; /* 예시 */
    }
    ```

### JavaScript에서 데이터 속성 접근

* JavaScript의 **`dataset`** 속성을 사용하여 `data-*` 값에 접근합니다. 하이픈(`-`)으로 연결된 속성명은 카멜 케이스(Camel Case)로 변환됩니다.

    ```javascript
    // 1. 요소 선택
    const dream = document.querySelector('div[data-display-name="dream"]');

    // 2. 모든 data 속성 접근 (DOMStringMap 객체)
    console.log(dream.dataset); // {index: '1', displayName: 'dream'}

    // 3. 특정 data 속성 값 접근 (data-display-name은 .displayName으로 접근)
    console.log(dream.dataset.displayName); // "dream"
    ```

---

## Open Graph (OG) 태그 🌐

Open Graph 태그는 웹페이지가 **소셜 미디어에 공유될 때** 표시될 미리보기 정보를 정의합니다.

| 속성명 | 설명 | 예시 (HTML) |
| :--- | :--- | :--- |
| `og:title` | 공유될 때 표시될 **제목**을 지정합니다. | `<meta property="og:title" content="멋진 개발 블로그" />` |
| `og:description` | 공유될 때 표시될 **페이지 요약 설명**을 지정합니다. | `<meta property="og:description" content="프론트엔드 개발 팁과 최신 기술 동향." />` |
| `og:image` | 공유될 때 표시될 **대표 이미지의 URL**을 지정합니다. | `<meta property="og:image" content="https://example.com/main-thumbnail.jpg" />` |
| `og:url` | 공유될 **페이지의 정식 URL**을 지정합니다. | `<meta property="og:url" content="https://example.com/mypage" />` |
| `og:type` | 페이지 콘텐츠의 **유형**을 지정합니다. (예: `website`, `article`, `video.movie`) | `<meta property="og:type" content="website" />` |