# Vite React TypeScript Template

## 실행
```bash
$ npm run dev    # 개발 모드 (.env.dev)
$ npm run start  # 실서버 모드 (.env)
```

## 빌드
```bash
$ npm run build:dev  # 테스트 빌드
$ npm run build      # 실서버 빌드
```

## 환경 변수
- `.env` - 실서버용 환경 변수
- `.env.dev` - 테스트용 환경 변수
- `VITE_` 접두사 필수

## 레이아웃 구조

### 구조
```
BaseLayout (공통)
  ├── ThemeProvider
  ├── GlobalStyle
  └── children (Outlet)

각 레이아웃
  ├── MainLayout
  ├── LoginLayout
  ├── TestLayout
  └── AdminLayout
```

### 의도
- **BaseLayout**: 공통 부분(ThemeProvider, GlobalStyle)을 추출하여 중복 제거
- **각 레이아웃**: BaseLayout을 사용하되, 필요시 커스터마이징 가능
  - 예: AdminLayout에 사이드바, 헤더 등 추가 가능
- **확장성**: 각 레이아웃이 독립적으로 관리되어 유지보수 용이

## 컴포넌트 계층 구조 및 네이밍 규칙

### 기본 계층 구조

```
Layout (레이아웃)
  └── Container (컨테이너)
      └── Wrapper (래퍼) [선택적]
          └── Content (콘텐츠)
              └── Section (섹션) [선택적]
                  └── Box/Item (박스/아이템)
```

### 각 레벨의 역할

| 컴포넌트명 | 역할 | 주요 스타일 |
|----------|------|------------|
| **Layout** | 전체 페이지 구조, 라우팅 레벨 | ThemeProvider, GlobalStyle |
| **Container** | 전체 틀 스타일 | `max-width`, `margin: 0 auto`, `padding`, `background` |
| **Wrapper** | 배치 속성 | `display: flex/grid`, `gap`, `align-items` |
| **Content** | 실제 콘텐츠 영역 | 콘텐츠별 스타일링 |
| **Section** | 논리적 구분 | 섹션별 배경, 간격 |
| **Box/Item** | 개별 요소 | 개별 아이템 스타일 |

> **참고**: 프로젝트 규모에 따라 Container와 Wrapper 중 하나를 생략 가능

### 페이지 내부 구조

페이지 내부에서 제목과 데이터를 구분할 때의 구조

```
Container
  ├── Header (페이지 제목 영역)
  │   ├── Title
  │   └── SubTitle
  └── Content (데이터 영역)
      └── List
          └── Item
              ├── ItemHeader (ItemTitle, ItemSubTitle)
              └── ItemContent (ItemDescription)
```

**사용 예시:**
```typescript
<Container>
  <Header>
    <Title>페이지 제목</Title>
    <SubTitle>페이지 부제목</SubTitle>
  </Header>
  <Content>
    <List>
      {data.map((item) => (
        <Item key={item.id}>
          <ItemHeader>
            <ItemTitle>{item.title}</ItemTitle>
            {item.subTitle && <ItemSubTitle>{item.subTitle}</ItemSubTitle>}
          </ItemHeader>
          <ItemContent>
            <ItemDescription>{item.description}</ItemDescription>
          </ItemContent>
        </Item>
      ))}
    </List>
  </Content>
</Container>
```

### Wrapper와 Section 사용 시점

#### Wrapper

**사용 시점:** 요소들의 배치가 바뀔 때 (세로 → 가로, 그리드 등)

**역할:** Container는 전체 틀 스타일, Wrapper는 배치 속성 (`display: flex/grid`, `gap` 등)

```typescript
// Wrapper 없이 (일반적)
<Container>
  <Header>...</Header>
  <Content>...</Content>
</Container>

// Wrapper 사용 (가로 배치, 그리드 등)
<Container>
  <Wrapper>  {/* display: flex/grid */}
    <Sidebar>...</Sidebar>
    <Content>...</Content>
  </Wrapper>
</Container>
```

**필요한 경우:**
- 요소들을 가로로 배치할 때
- 그리드 레이아웃이 필요할 때

#### Section

**사용 시점:** Content 내부에서 논리적으로 구분된 콘텐츠 영역이 여러 개일 때

```typescript
<Content>
  <Section>
    <SectionTitle>인기 상품</SectionTitle>
    <List>...</List>
  </Section>
  <Section>
    <SectionTitle>신상품</SectionTitle>
    <List>...</List>
  </Section>
</Content>
```

**필요한 경우:**
- 같은 페이지에 여러 주제의 콘텐츠가 있을 때
- 각 영역마다 다른 배경색이나 스타일이 필요할 때
- 섹션별로 독립적인 제목과 데이터가 있을 때

## 라이브러리

| 라이브러리 | 설명 |
|----------|------|
| react-router-dom | 라우팅 |
| zustand | 상태 관리 |
| axios | HTTP 클라이언트 |
| @tanstack/react-query | 서버 상태 관리 |
| date-fns | 날짜 처리 |
| libphonenumber-js | 전화번호 처리 |
| react-hook-form | 폼 관리 |
| zod | 스키마 검증 |
| react-spinners | 로딩 스피너 |
| styled-components | CSS-in-JS |
| babel-plugin-styled-components | styled-components 개발자 도구 최적화 (컴포넌트 이름 표시) |
