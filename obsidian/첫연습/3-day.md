## 📝 CSS 핵심 개념 메모

---

### 5.6 보더(Border)와 아웃라인(Outline)
* **`content-box` (기본값):** `width/height`는 콘텐츠 영역. **패딩+보더**가 **밖으로 추가**되어 요소 크기가 커짐.
* **`border-box`:** `width/height`에 **패딩+보더**가 **포함**됨 (지정 넓이 유지).
* **`outline` 특징:** `border-box`를 써도 `outline`은 **지정 넓이 밖**에 그려지며, 레이아웃에 **영향을 주지 않음**.

---

### 5.7 `display`: 블록, 인라인, 인라인-블록
| 유형 | 특징 | 예시 |
| :--- | :--- | :--- |
| **블록** | 가로 전체, 수직 나열. 너비/높이/마진/패딩 모두 적용. | `h1`, `p` |
| **인라인** | 콘텐츠 크기, 수평 나열. **수평 마진/패딩만** 적용 가능. | `span` |
| **인라인-블록**| 수평 나열 가능 + 너비/높이/수직/수평 마진/패딩 모두 적용 가능. | `.class` |
* **링크:** [https://developer.mozilla.org/en-US/docs/Web/CSS/display](https://developer.mozilla.org/en-US/docs/Web/CSS/display)

---

### 5.8 `position`: `relative` vs `absolute`
* **`relative`:** **기존 자리 유지**하며 `top/bottom/left/right`로 **상대적** 이동. (1,2,3 중 2를 변경해도 3은 제 위치)
* **`absolute`:** **문서 흐름에서 제거** (기존 자리 X). 가장 가까운 `relative` 부모 또는 `body` 기준으로 이동. (1,2,3 중 2를 변경하면 3이 2 위치로)
    * **Tip:** 부모 안에서 이동시키려면 **부모에 `position: relative;`** 지정.
* **링크:** [https://developer.mozilla.org/en-US/docs/Web/CSS/position](https://developer.mozilla.org/en-US/docs/Web/CSS/position)

---

### 5.9 `position`: `sticky` vs `fixed`
* **`sticky`:** **기존 위치 유지**하다가 스크롤이 **기준 부분에 닿으면 고정**.
* **`fixed`:** **뷰포트(화면) 기준**으로 위치가 **항상 고정**. (문서 흐름에서 나감)
* **링크:** [https://developer.mozilla.org/en-US/docs/Web/CSS/position](https://developer.mozilla.org/en-US/docs/Web/CSS/position)

---

### 5.10 정렬 테크닉 (수평/수직 중앙)
1.  **블록 수평:** `margin: auto;` (부모 기준으로 중앙 배치)
2.  **인라인/텍스트 수평:** `text-align: center;` (부모에 적용)
3.  **단일 텍스트 수직:** `height: 100px;` + `line-height: 100px;`
4.  **Absolute 중앙:** `top: 50%; left: 50%;` **(부모 기준)** + `transform: translate(-50%, -50%);` **(자기 기준)**
5.  **Flexbox 중앙:** `display: flex;` + `justify-content: center;` + `align-items: center;`

---

### 5.11 반응형 배경 (`background`)
* `background-repeat: no-repeat;` / `background-position: center;`
* **`background-size: cover;`:** 이미지가 요소를 **덮도록** 크기 조정 (**반응형**).
* **`background-size: contain;`:** 이미지가 **잘리지 않고** 포함되도록 크기 조정.
* **고정:** `background-attachment: fixed;` (커버이지만 반응 X, 고정 느낌)
* **단축:** `background: url(uri) center / cover no-repeat;`
* **링크:**