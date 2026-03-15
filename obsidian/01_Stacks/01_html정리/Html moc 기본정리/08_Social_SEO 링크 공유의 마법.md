> [!info] **학습 목표** 사용자가 웹사이트 링크를 SNS(카카오톡, 페이스북, 트위터 등)에 공유했을 때, 매력적인 미리보기(Preview)가 생성되도록 설정하는 방법을 익힙니다. 이것은 클릭률(CTR)에 직접적인 영향을 주는 중요한 작업입니다.

---

## 1. Open Graph (og:tags): SNS 공유의 표준

오픈 그래프(Open Graph)는 페이스북에서 시작되었지만, 현재는 카카오톡, 네이버 블로그, 슬랙 등 대부분의 플랫폼에서 표준처럼 사용합니다.

- **주요 태그와 역할**:
    
    - `og:title`: 공유될 때 표시될 제목
        
    - `og:description`: 제목 아래에 보일 짧은 설명
        
    - `og:image`: 미리보기에 들어갈 썸네일 이미지 (권장 크기: 1200 x 630px)
        
    - `og:url`: 페이지의 표준 주소
        
- **코드 예시**:
    

HTML

```
<meta property="og:type" content="website">
<meta property="og:url" content="https://www.mysite.com">
<meta property="og:title" content="멋진 코딩 공부방">
<meta property="og:description" content="초보자도 쉽게 배우는 HTML 기초 강의!">
<meta property="og:image" content="https://www.mysite.com/images/thumb.jpg">
```

---

## 2. Twitter Cards: 트위터를 위한 최적화

트위터는 자체적인 메타 태그를 사용합니다. 오픈 그래프와 비슷하지만 `name` 속성을 사용한다는 차이가 있습니다.

- **주요 태그와 역할**:
    
    - `twitter:card`: 카드의 형태를 결정합니다. (`summary` 또는 큰 이미지를 보여주는 `summary_large_image`)
        
    - `twitter:title` / `twitter:description` / `twitter:image`: 역할은 오픈 그래프와 동일합니다.
        
- **코드 예시**:
    

HTML

```
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="멋진 코딩 공부방">
<meta name="twitter:description" content="초보자도 쉽게 배우는 HTML 기초 강의!">
<meta name="twitter:image" content="https://www.mysite.com/images/thumb.jpg">
```

> [!tip] **중복을 피하려면?** 트위터는 자기 태그가 없으면 오픈 그래프 태그(`og:`)를 대신 읽어옵니다. 따라서 `twitter:card` 정도만 설정해주고 나머지는 오픈 그래프로 통합 관리하기도 합니다.

---

## 3. Favicon 고도화: 모든 기기에서 빛나게 하기

파비콘(Favicon)은 브라우저 탭에 뜨는 작은 아이콘입니다. 하지만 모바일 시대에는 스마트폰 홈 화면에 '바로가기 추가'를 할 때 사용되는 고화질 아이콘 설정도 필수입니다.

- **기본 파비콘 (ICO/PNG)**:
    
    HTML
    
    ```
    <link rel="icon" href="/favicon.ico" type="image/x-icon">
    <link rel="icon" href="/favicon-32x32.png" sizes="32x32" type="image/png">
    ```
    
- **애플 기기용 (Apple Touch Icon)**: 아이폰 홈 화면 추가 시 사용됩니다.
    
    HTML
    
    ```
    <link rel="apple-touch-icon" href="/apple-touch-icon.png">
    ```
    
- **안드로이드/크롬용 (Manifest)**: 웹앱 형태로 인식하게 해줍니다.
    
    HTML
    
    ```
    <link rel="manifest" href="/site.webmanifest">
    ```
    

---

## 💡 프론트엔드 개발자의 실무 팁

1. **캐시 초기화 필수**: 메타 태그를 수정했는데 카톡 미리보기가 안 바뀐다면? 플랫폼마다 '캐시'를 저장하고 있기 때문입니다. 아래 도구들에서 URL을 입력해 캐시를 새로고침하세요.
    
    - [카카오톡 디버거](https://developers.kakao.com/tool/debugger/sharing)
        
    - [페이스북 공유 디버거](https://developers.facebook.com/tools/debug/)
        
2. **절대 경로 사용**: `og:image` 주소를 적을 때는 `./images/logo.png` 같은 상대 경로가 아니라 `https://mysite.com/logo.png` 같은 **전체 주소(절대 경로)**를 적어야 이미지가 제대로 나타납니다.
    
3. **이미지 용량**: 미리보기 이미지가 너무 무거우면 공유 시 텍스트만 뜨고 이미지는 안 뜰 수 있습니다. 300KB 이하로 최적화하는 것이 좋습니다.