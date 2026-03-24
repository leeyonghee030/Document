---
status:
  - done
tags:
  - devops
  - git
created: 2026-01-17
updated: 2026-01-17
---
> 📂 [[DevOps 인덱스]]
# Git & GitHub 입문 6가이드

[[#git]] [[#Git을 사용하는 이유]]

## git
`$ git init` 작업기록 하기 위해 git생성(깃명령어 사용을 위한)
`$ git status` 작업상태 확인(수정,변경,삭제 내용확인)
`$ git branch -M master localNote`(작업영역 이름 변경 )
`$ git add` git에 작업파일 기록할거라고 추가(스태이징) ("add ." 은 전체 추가)
`$ git commit -m"기록내용"` 스태이징된 파일 작업기록 
`$ git log` 작업내역 확인
`$ git checkout (commit code) ` 저장된 파일로 되돌리기
`$ git restore .` 수정된 거 되돌리기 (가장최신 커밋지점)
`$ git remote add origin [방금_복사한_깃허브_주소]
`$ git push -u origin master 프로젝트를 처음 깃허브에 연결할 때 (딱 한 번)

## Git을 사용하는 이유

### 1. 버전 관리

코드의 변경 이력을 자동으로 저장. 언제든지 이전 버전으로 되돌릴 수 있어 실수해도 안전.

### 2. 충돌 관리

여러 명이 같은 파일을 수정해도 자동으로 합치거나, 충돌 부분을 명확히 표시.

### 3. 이력 추적

누가, 언제, 무엇을, 왜 변경했는지 모두 기록. 문제가 생겼을 때 원인을 쉽게 찾을 수 있음.

---

## Git vs GitHub

**Git**: 내 컴퓨터에서 버전을 관리하는 도구 (로컬)  
**GitHub**: Git으로 관리한 코드를 저장하고 공유하는 온라인 플랫폼 (클라우드)
**Git Bash**: Windows에서 Git 명령어를 사용할 수 있게 해주는 터미널 프로그램.

쉽게 말해 Git은 '프로그램', GitHub는 '서비스'.

---

## 기본 개념

### 저장소 (Repository)

Git으로 리되는 프관로젝트 폴더. 줄여서 "레포"라고도 부름.

**로컬 저장소**: 내 컴퓨터에 있는 Git 프로젝트 폴더  
**원격 저장소 (Remote)**: GitHub, GitLab 같은 서버에 있는 저장소

### 로컬 (Local)

내 컴퓨터, 내 작업 환경을 의미. "로컬에서 작업한다" = 내 컴퓨터에서 코드를 수정한다는 뜻.

### 브랜치 (Branch)

코드의 독립적인 작업 공간. 나뭇가지처럼 메인 코드에서 갈라져 나와 따로 작업할 수 있음.

**왜 사용?**

- 메인 코드를 건드리지 않고 새 기능 개발 가능
- 여러 기능을 동시에 개발 가능
- 실험적인 코드를 안전하게 테스트 가능

**예시**

```
main (메인 코드)
 ├── feature/login (로그인 기능 개발)
 ├── feature/payment (결제 기능 개발)
 └── hotfix/bug-123 (긴급 버그 수정)
```

각 브랜치에서 독립적으로 작업하다가, 완성되면 main으로 합침(merge).

### origin

원격 저장소의 기본 별칭. `git push origin main` 에서 origin은 "GitHub에 있는 내 저장소"를 가리킴.

```bash
git remote -v  # origin이 어디를 가리키는지 확인
```

### HEAD

지금 내가 보고 있는 커밋 또는 브랜치를 가리키는 포인터. "현재 위치"라고 생각하면 됨.

```bash
HEAD -> main  # 지금 main 브랜치에 있다는 뜻
```

### clone vs fork

**clone**: 원격 저장소를 내 컴퓨터로 복사

```bash
git clone https://github.com/사용자명/저장소명.git
```

- 내 저장소든 남의 저장소든 로컬로 가져올 때 사용
- 직접 push 권한이 있어야 수정사항 업로드 가능

**fork**: 남의 저장소를 내 GitHub 계정으로 복사

- GitHub 웹에서 "Fork" 버튼 클릭
- 원본 저장소는 건드리지 않고 내 계정에 복사본 생성
- 오픈소스 프로젝트에 기여할 때 주로 사용

**흐름**: fork로 내 계정에 복사 → clone으로 로컬에 다운 → 수정 → push → PR로 원본에 제안

### checkout vs switch

둘 다 브랜치를 전환하는 명령어.

**checkout**: 예전 방식 (여러 기능을 하나의 명령어로)

```bash
git checkout feature/login
```

**switch**: 새로운 방식 (브랜치 전환 전용, Git 2.23부터)

```bash
git switch feature/login
git switch -c feature/new  # 새 브랜치 생성하며 전환
```

요즘은 `switch` 사용을 권장. 더 명확하고 실수가 적음.

### .gitignore

Git이 무시할 파일 목록을 적는 파일. 비밀번호, 개인 설정, 임시 파일 등 저장소에 올리면 안 되는 것들을 지정.

**예시** (.gitignore 파일 내용)

```
# 환경 변수 파일
.env

# 의존성 폴더
node_modules/
venv/

# 빌드 결과물
dist/
build/

# IDE 설정
.vscode/
.idea/

# OS 파일
.DS_Store
Thumbs.db
```

프로젝트 루트에 `.gitignore` 파일을 만들고 위 내용을 넣으면 해당 파일들은 Git이 추적하지 않음.

---

## 핵심 용어 정리

### 기본 명령어


### 1. Commit (커밋) : "내 컴퓨터에 저장"

- **의미:** 작업 중인 내용의 '스냅샷'을 찍는 것입니다. 게임의 **세이브 포인트**와 같습니다.
    
- **상태:** 아직 내 컴퓨터에만 저장된 상태입니다. 인터넷이 안 되어도 할 수 있습니다.
    
- **깃 데스크탑:** 왼쪽 하단에 'c'를 적고 **Commit to [브랜치명]** 버튼을 누르는 동작입니다.
    

### 2. Push (푸시) : "서버에 업로드"

- **의미:** 내 컴퓨터에서 커밋한 기록들을 **GitHub 서버(온라인 저장소)로 전송**하는 것입니다.
    
- **결과:** 이제 다른 사람들이 GitHub 웹사이트나 각자의 컴퓨터에서 내가 작업한 내용을 볼 수 있게 됩니다.
    
- **깃 데스크탑:** 커밋 후 오른쪽 상단에 나타나는 **Push origin** 버튼을 누르는 동작입니다.
    

### 3. Fetch (패치) : "업데이트 확인"

- **의미:** GitHub 서버에 **새로 올라온 내용이 있는지 '확인'**만 하는 것입니다.
    
- **특징:** 내 코드 파일이 실제로 바뀌지는 않습니다. "누가 코드를 올렸나?" 하고 목록만 새로고침하는 느낌입니다.
    
- **깃 데스크탑:** 상단 중앙의 **Fetch origin** 버튼을 누르면 서버를 확인하고, 만약 누군가 코드를 올렸다면 그제서야 'Pull' 버튼으로 바뀝니다.
    

### 4. Pull (풀) : "서버에서 내려받기"

- **의미:** GitHub 서버에 있는 최신 코드를 **내 컴퓨터로 가져와서 합치는(Merge)** 것입니다.
    
- **결과:** 내 컴퓨터의 코드 파일들이 팀원이 수정한 최신 상태로 바뀝니다.
    
- **깃 데스크탑:** **Pull origin** 버튼을 누르는 동작입니다. (보통 Fetch를 먼저 해서 바뀐 게 있는지 확인한 후 실행합니다.)
**add**: 변경된 파일을 저장 준비 구역(staging area)에 올림.

```bash
git add 파일명
git add .  # 모든 변경사항 추가
```

**commit**: 준비 구역의 파일들을 하나의 '세이브 포인트'로 저장.

```bash
git commit -m "변경 내용 설명"
```

**push**: 내 컴퓨터의 커밋들을 GitHub 같은 원격 저장소로 업로드.

```bash
git push origin main
```

**fetch**: 원격 저장소의 변경사항을 확인만 하고, 내 코드에는 반영 안 함.

**pull**: 원격 저장소의 변경사항을 가져와서 내 코드에 바로 반영.

```bash
git pull origin main
```

**stash**: 현재 작업 중인 변경사항을 임시 저장하고 숨김. 나중에 다시 꺼내 쓸 수 있음.

```bash
git stash       # 임시 저장
git stash pop   # 다시 꺼내기
```

### 1. 자동으로 Stash 만들기 (가장 쉬운 방법)

브랜치를 옮길 때 깃 데스크탑이 똑똑하게 물어봅니다.

1. 파일을 수정 중인 상태에서 상단의 **Current Branch**를 눌러 다른 브랜치를 선택합니다.
    
2. 이때 다음과 같은 팝업창이 뜹니다.
    
    - **Leave my changes on [현재 브랜치]:** 수정 사항을 'Stash'에 넣어두고 몸만 가겠다는 뜻입니다. (이게 바로 Stash입니다!)
        
    - **Bring my changes to [이동할 브랜치]:** 작업 중인 수정 사항을 그대로 들고 다른 브랜치로 넘어가겠다는 뜻입니다.
        
3. **Leave my changes...**를 선택하고 브랜치를 이동하면, 기존 브랜치에 작업 내용이 안전하게 보관됩니다.
### 협업 프로세스

**PR (Pull Request)**: "내 코드 확인하고 합쳐줘"라는 요청. GitHub에서 진행.

**review**: PR에 올라온 코드를 다른 팀원이 검토하는 과정.

**merge**: 검토가 끝난 코드를 메인 코드에 합치는 것.

**conflict**: 같은 부분을 서로 다르게 수정해서 자동으로 합칠 수 없는 상황. 수동으로 해결해야 함.

### 브랜치 전략

**main** (또는 master): 배포 가능한 안정적인 코드가 있는 기본 브랜치.

**develop**: 개발 중인 코드가 모이는 브랜치. 다음 배포 준비용.

**feature**: 새 기능을 개발할 때 만드는 브랜치.

```bash
git checkout -b feature/login
```

**release**: 배포 준비를 위한 브랜치. 최종 테스트와 버그 수정.

**hotfix**: 배포된 코드에 긴급 버그가 생겼을 때 빠르게 수정하는 브랜치.

### 기타 용어

**commit convention**: 커밋 메시지를 일정한 규칙으로 작성하는 약속.

```
feat: 로그인 기능 추가
fix: 회원가입 버그 수정
docs: README 업데이트
```

**WIP (Work In Progress)**: "작업 중"이라는 뜻. 커밋 메시지나 PR 제목에 붙여 아직 완성 안 됐음을 표시.

---

## 기본 워크플로우 예시

1. 새 기능 개발 시작

```bash
git checkout -b feature/new-feature
```

2. 코드 수정 후 저장

```bash
git add .
git commit -m "feat: 새 기능 추가"
```

3. GitHub에 업로드

```bash
git push origin feature/new-feature
```

4. GitHub에서 PR 생성 → 리뷰 → 승인 → merge
    
5. 최신 코드 받아오기
    

```bash
git checkout main
git pull origin main
```

---

## 처음 시작할 때

```bash
# Git 설치 확인
git --version

# 사용자 정보 설정 (최초 1회)
git config --global user.name "내이름"
git config --global user.email "내이메일@example.com"

# 새 프로젝트 시작
git init

# 또는 기존 프로젝트 복사
git clone https://github.com/사용자명/저장소명.git
```

**Tip**: 막히면 `git status`로 현재 상태를 확인. 대부분의 문제는 상태 확인으로 해결의 실마리를 찾을 수 있음.

---

## GitHub Desktop 사용법

GitHub Desktop은 Git 명령어를 몰라도 GUI로 쉽게 버전 관리를 할 수 있는 프로그램.

### Git Bash vs GitHub Desktop 차이점

**Git Bash (명령어)**

```bash
git add .
git commit -m "메시지"
git push
```

**GitHub Desktop (GUI)**

- `add` 단계가 없음
- 변경된 파일이 자동으로 UI에 표시되고 체크박스로 선택
- 이미 UI에서 변경사항이 보이기 때문에 별도로 staging area에 올릴 필요 없음

### 기본 사용 흐름

1. **저장소 열기**
    
    - File → Add Local Repository (기존 프로젝트)
    - File → Clone Repository (GitHub에서 받아오기)
2. **코드 수정**
    
    - 에디터에서 코드 수정
    - GitHub Desktop에 자동으로 변경사항 표시됨
3. **커밋하기**
    
    - 왼쪽 체크박스로 커밋할 파일 선택 (이게 `add` 역할)
    - 하단 Summary에 커밋 메시지 입력
    - "Commit to main" 버튼 클릭
4. **푸시하기**
    
    - 상단 "Push origin" 버튼 클릭
5. **풀하기**
    
    - 상단 "Fetch origin" 클릭 후
    - "Pull origin" 버튼 클릭

### 브랜치 관리

- 상단 "Current Branch" 클릭 → "New Branch" 로 생성
- 브랜치 목록에서 클릭하면 전환됨
- "Publish branch"로 GitHub에 업로드

### PR 만들기

- 브랜치 푸시 후 상단에 "Create Pull Request" 버튼 표시
- 클릭하면 GitHub 웹페이지로 이동하여 PR 작성

### 충돌 해결

- 충돌 발생 시 "Open in 에디터" 버튼으로 파일 열기
- 에디터에서 수정 후 저장
- GitHub Desktop에서 "Continue merge" 클릭

### 언제 사용하면 좋을까?

**GitHub Desktop 추천**

- Git 명령어가 익숙하지 않을 때
- 시각적으로 변경사항을 확인하고 싶을 때
- 간단한 작업 위주일 때

**Git Bash 추천**

- 복잡한 Git 작업 (rebase, cherry-pick 등)
- 자동화 스크립트 작성
- 서버 환경에서 작업할 때