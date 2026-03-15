> [!info] **학습 목표**
> 
> 픽셀 방식(Bitmap)이 아닌 수학적 계산 방식인 **SVG**의 특징을 이해하고, 실시간 그래픽 구현을 위한 **Canvas**의 기초, 그리고 이미지를 의미 있게 묶어주는 **Figure** 태그의 사용법을 익힙니다.

---

## 1. SVG (Scalable Vector Graphics): 깨지지 않는 마법

SVG는 점과 선의 좌표값을 계산해서 그리는 **벡터(Vector)** 방식의 이미지입니다. 사진(JPG, PNG)과는 본질적으로 다릅니다.

![Vector vs Raster graphics comparison, AI로 생성](https://encrypted-tbn1.gstatic.com/licensed-image?q=tbn:ANd9GcSQNooTWqUR_CcoL5AoTzPTsLW7RsGg6J1kxlj1td2x_W44iBN8P464VeJcmxOQr5PMtz9DA4URwA4Wm8QY5n0Dg2IuFCMdzxn5Yw-HbHWLl3Fipzk)

Shutterstock

- **특징**:
    
    - **무한 확장**: 아무리 확대해도 테두리가 깨지지 않고 선명합니다. (로고, 아이콘에 최적)
        
    - **코드 형태**: HTML 문서 안에 직접 넣을 수 있으며, CSS나 JS로 색상을 바꾸거나 애니메이션을 줄 수 있습니다.
        
    - **경량화**: 단순한 도형 위주의 이미지는 파일 용량이 매우 작습니다.
        
- **코드 예시 (직접 그리기)**:
    
    HTML
    
    ```
    <svg width="100" height="100">
      <circle cx="50" cy="50" r="40" stroke="black" stroke-width="3" fill="red" />
    </svg>
    ```
    

---

## 2. Canvas: 자바스크립트 전용 도화지

Canvas는 HTML 태그 하나만 만들어두고, 실제 그림은 **JavaScript**로 그리는 방식입니다.

- **특징**:
    
    - **비트맵(Bitmap) 방식**: 픽셀을 직접 찍어서 그립니다. (확대하면 깨짐)
        
    - **고성능**: 수천 개의 객체를 실시간으로 움직여야 하는 **웹 게임, 실시간 차트, 복잡한 애니메이션**에 적합합니다.
        
    - **휘발성**: 한 번 그리면 '그림'이 될 뿐, 내부 요소를 개별적으로 수정(CSS 적용 등)할 수 없습니다.
        
- **코드 예시 (기본 구조)**:
    
    HTML
    
    ```
    <canvas id="myCanvas" width="200" height="100"></canvas>
    
    <script>
      const canvas = document.getElementById('myCanvas');
      const ctx = canvas.getContext('2d');
      ctx.fillStyle = 'blue';
      ctx.fillRect(10, 10, 150, 80); // 파란색 직사각형 그리기
    </script>
    ```
    

---

## 3. Figure & Figcaption: 이미지에 이름표 달아주기

단순히 `<img>`만 쓰는 것보다, 이미지와 그에 대한 설명을 하나로 묶어주는 것이 **시맨틱(Semantic)**한 설계입니다.

- **`<figure>`**: 이미지, 도표, 사진, 코드 리스트 등 독립적인 콘텐츠를 감쌉니다.
    
- **`<figcaption>`**: 그 콘텐츠에 대한 설명(캡션)을 작성합니다.
    
- **코드 예시**:
    
    HTML
    
    ```
    <figure>
      <img src="mountain.jpg" alt="설악산의 설경">
      <figcaption>그림 1. 겨울철 설악산의 아름다운 풍경</figcaption>
    </figure>
    ```
    
- **장점**: 검색 엔진이 "이 글자는 저 이미지에 대한 설명이구나!"라고 정확히 인지하게 됩니다.
    

---

## 💡 프론트엔드 개발자의 선택 가이드 (SVG vs Canvas)

|**구분**|**SVG**|**Canvas**|
|---|---|---|
|**방식**|벡터 (수식)|비트맵 (픽셀)|
|**확대 시**|깨짐 없음 (선명)|깨짐 발생 (계단 현상)|
|**제어**|CSS/JS로 개별 요소 제어 가능|JS로만 전체 다시 그리기 가능|
|**적합한 곳**|아이콘, 로고, 정적 일러스트|게임, 주식 차트, 화려한 효과|

---

## 🛠️ 실무 활용 팁

1. **아이콘 폰트 대신 SVG**: 예전에는 `FontAwesome` 같은 폰트 아이콘을 썼지만, 요즘은 성능과 커스텀 자유도 때문에 **Inline SVG**를 선호합니다.
    
2. **Alt 속성 잊지 말기**: `figure` 안에 `img`를 넣을 때도 시각 장애인을 위한 `alt` 속성은 반드시 작성해야 합니다. `figcaption`이 있다고 해서 생략하지 마세요.