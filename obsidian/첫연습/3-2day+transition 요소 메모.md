## 🚀 CSS `transition` 문법 및 구성 요소 메모

---

### 1. 단축 속성 (Shorthand Syntax)

`transition`은 4가지 하위 속성을 한 번에 설정하는 **단축 속성**입니다.

```css
transition: property duration timing-function delay;

구성 요소,설명,예시,필수 여부
property,전환 효과를 적용할 CSS 속성 이름.,"all, opacity, transform",필수
duration,전환이 완료되는 데 걸리는 시간.,"0.5s, 300ms",필수
timing-function,전환 속도의 변화 패턴 (가속도).,"ease, linear, ease-in-out",선택
delay,전환 시작 전 대기 시간.,"1s, 200ms",선택

2. 각 구성 요소 상세 설명
① transition-property
역할: 어떤 속성에 애니메이션을 적용할지 결정합니다.

값:

all (기본값): 변경되는 모든 속성에 적용.

특정 속성: background-color, transform 등. (쉼표로 여러 개 나열 가능)

② transition-duration
역할: 전환이 얼마나 오래 지속될지 설정합니다.

단위: 초(s) 또는 **밀리초(ms)**를 사용해야 합니다.

③ transition-timing-function
역할: 속도의 변화 곡선을 정의합니다.

주요 값:

ease (기본값): 느리게 시작 → 빨라졌다가 → 느리게 끝.

linear: 처음부터 끝까지 일정한 속도.

ease-in: 느리게 시작하여 점점 빨라짐.

ease-out: 빠르게 시작하여 점점 느려짐.

cubic-bezier(...): 사용자 정의 속도 곡선.

④ transition-delay
역할: 속성이 변경된 후, 실제로 전환이 시작되기까지 기다리는 시간을 설정합니다.

단위: 초(s) 또는 **밀리초(ms)**를 사용합니다.

/* 1. 기본: 배경색을 0.3초 동안 부드럽게 (ease) 변화 */
.box-1 {
  transition: background-color 0.3s;
}

/* 2. 전체 속성에 적용: 모든 변화를 0.5초 동안 일정 속도(linear)로 적용 */
.box-2 {
  transition: all 0.5s linear;
}

/* 3. 지연 시간 포함: 1초 기다린 후, 크기 변화를 0.4초 동안 적용 */
.box-3 {
  transition: transform 0.4s ease-out 1s;
}

[https://developer.mozilla.org/en-US/docs/Web/CSS/transition](https://developer.mozilla.org/en-US/docs/Web/CSS/transition)

[https://cubic-bezier.com/#.17,.67,.83,.67](https://cubic-bezier.com/#.17,.67,.83,.67)