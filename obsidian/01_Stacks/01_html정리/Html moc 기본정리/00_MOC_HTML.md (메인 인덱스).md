📂 **HTML**

- `00_MOC_HTML.md` (메인 인덱스)
    
- 📂 **01_Structure**: 문서 기본 구조, Meta 태그, Head 정보
    
- 📂 **02_Text**: 제목, 본문, 목록, 강조 등 텍스트 관련
    
- 📂 **03_Media**: 이미지, 비디오, 오디오, iframe
    
- 📂 **04_Forms**: Input, Button, Form, Validation
    
- 📂 **05_Semantic**: 시맨틱 태그 (SEO 및 레이아웃)
    
- 📂 **06_Accessibility**: 웹 접근성 (ARIA, Alt 속성 등)
  
  ## 📂 07_Attributes: 이름표와 숨겨진 데이터 (ID, Class, Data)

태그에 '별명'을 붙여주는 방법입니다. 나중에 CSS로 옷을 입히거나 JS로 움직이게 할 때 필수예요.

- **ID vs Class**:
    
    - `id`: 전교에 딱 한 명뿐인 이름 (중복 불가).
        
    - `class`: 같은 동아리 부원들 (여러 태그에 중복 사용 가능).
        
- **Global Attributes**: 모든 태그에서 공통으로 쓸 수 있는 속성들 (`title`, `lang`, `hidden` 등).
    
- **Data-Attribute**: 나만의 커스텀 데이터를 숨겨두는 법 (`data-*`).
    

---

## 📂 08_Social_SEO: 링크 공유의 마법 (Open Graph)

카톡이나 슬랙에 내 사이트 링크를 올렸을 때, 예쁜 썸네일과 설명이 뜨게 만드는 설정입니다.

- **Open Graph (og:tags)**: 페이스북, 카톡 등에서 사용하는 공유 메타 데이터.
    
- **Twitter Cards**: 트위터 전용 공유 설정.
    
- **Favicon 고도화**: 기기별(아이폰, 안드로이드) 아이콘 설정법.
    

---

## 📂 09_Graphics: 코드로 그리는 그림 (SVG & Canvas)

이미지 파일(png, jpg)을 쓰는 대신 코드로 직접 그림을 그리는 방법입니다.

- **SVG (Scalable Vector Graphics)**: 아무리 키워도 깨지지 않는 '코드형 이미지'. 아이콘 만들 때 최고!
    
- **Canvas**: 자바스크립트로 역동적인 게임이나 그래프를 그리는 도화지.
    
- **Figure & Figcaption**: 이미지와 설명을 세트로 묶어주는 시맨틱한 방법.
    

---

## 📂 10_Scripting: 뇌(JS) 이식하기 (Script & Performance)

HTML(뼈대)에 JavaScript(기능)를 연결할 때 '언제, 어떻게' 불러올지가 중요합니다.

- **Script 태그**: 외부 JS 파일 연결법.
    
- **Async vs Defer**: "잠깐만 기다려!" vs "나중에 몰아서 해!" - 페이지 로딩 속도를 결정짓는 마법의 단어.
    
- **NoScript**: 자바스크립트가 꺼진 브라우저를 위한 배려.
    

---

## 📂 11_Entities: 금지된 문자 쓰기 (Entities)

HTML 코드 안에서 `<`, `>`, `&` 같은 문자를 그냥 쓰면 브라우저가 "어? 태그 시작인가?" 하고 오해합니다. 이때 쓰는 특수 암호입니다.

-  : 한 칸 띄어쓰기 (스페이스).
    
- **< / >**: 작다(<), 크다(>) 표시.
    
- **©**: 저작권 표시(©).
    
- **Emojis**: 웹에서 이모지를 안전하게 표시하는 법.
    

---

## 📂 12_Validation: 내 코드는 건강한가? (W3C & Debug)

코드를 다 짠 뒤에 실수가 없는지 검사하는 '건강검진' 단계입니다.

- **W3C Validator**: 문법 오류 찾아주는 사이트 활용법.
    
- **Can I Use**: "내가 쓴 이 기능, 인터넷 익스플로러에서도 돌아갈까?" 확인하는 법.
    
- **Chrome DevTools**: 브라우저 개발자 도구로 내 HTML 뜯어보기.
  
  
  


# 🌐 HTML 지식 지도 (MOC)

> [!abstract] HTML은 웹 페이지의 구조를 정의하는 마크업 언어입니다.
> 핵심은 **의미에 맞는 태그(Semantic)**를 사용하는 것입니다.

## 🏗️ 1. 기본 구조 및 설정 (Root & Metadata)
- [[01_Structure 문서 기본 구조, Meta 태그, Head 정보]] (DOCTYPE, html, head, body)
- [[Meta_태그와_SEO]] (charset, viewport, description)
- [[Link_태그와_Favicon]]

## 📝 2. 텍스트 요소 (Text Content)
- [[Heading_태그_H1_to_H6]]
- [[단락_P_와_줄바꿈_BR_HR]]
- [[목록_UL_OL_LI]]
- [[텍스트_강조_Strong_Em_Mark]]

## 🔗 3. 하이퍼링크 및 멀티미디어 (Links & Media)
- [[A_태그와_절대경로_상대경로]]
- [[IMG_태그와_Alt_속성의_중요성]]
- [[Video_및_Audio_임베딩]]
- [[Iframe_활용과_주의사항]]

## 📋 4. 표와 양식 (Tables & Forms) - *중요*
- [[Table_태그_구조_Thead_Tbody]]
- [[Form_태그와_Action_Method]]
- [[다양한_Input_타입_정리]]
- [[Label_태그와_접근성_연결]]



## 🏗️ 5. 시맨틱 웹 (Semantic HTML)
- [[왜_Semantic_태그를_써야하는가]]
- [[Header_Nav_Main_Footer_구조]]
- [[Section_vs_Article_구분하기]]
- [[Aside_및_Details_Summary]]



## ♿ 6. 웹 접근성 및 성능 (A11y & Optimization)
- [[웹_접근성_기초와_ARIA_Roles]]
- [[HTML_파일_최적화_팁]]