# Hugo + Cloudflare Pages 블로그 시작 체크리스트

## 1. 사전 준비

- [ ] GitHub 계정 생성 (이미 있다면 스킵)
- [ ] Cloudflare 계정 생성 (https://dash.cloudflare.com/sign-up - 무료)
- [ ] 도메인 구매 (선택사항, 나중에 연결 가능)
- [ ] Hugo 설치
  - **macOS**: `brew install hugo`
  - **Windows**: `choco install hugo-extended` 또는 [GitHub Releases](https://github.com/gohugoio/hugo/releases)에서 다운로드
  - **Linux**: `sudo snap install hugo` 또는 패키지 매니저 사용
  - 설치 확인: `hugo version`
- [ ] Git 설치 확인
  - 확인: `git --version`
  - 없다면: https://git-scm.com/downloads 에서 설치

---

## 2. 로컬 블로그 세팅

- [ ] 터미널에서 블로그 프로젝트 생성
  ```bash
  hugo new site my-blog
  cd my-blog
  ```

- [ ] Git 저장소 초기화
  ```bash
  git init
  ```

- [ ] Hugo 테마 선택 및 설치
  - [Hugo Themes](https://themes.gohugo.io/)에서 테마 선택
  - 추천 테마: PaperMod, Stack, Ananke, Terminal 등
  - Git submodule로 테마 설치 예시:
    ```bash
    git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
    ```

- [ ] 설정 파일 수정 (`hugo.toml` 또는 `config.toml`)
  ```toml
  baseURL = 'https://your-site.pages.dev/'  # 나중에 실제 URL로 변경
  languageCode = 'ko-kr'
  title = '내 블로그 제목'
  theme = 'PaperMod'  # 설치한 테마 이름
  ```
  - 테마별 추가 설정은 해당 테마 문서 참고

---

## 3. 첫 포스팅 작성

- [ ] 첫 포스트 생성
  ```bash
  hugo new posts/my-first-post.md
  ```

- [ ] `content/posts/my-first-post.md` 파일 편집
  - Front Matter에서 `draft: true`를 `draft: false`로 변경
  - 마크다운으로 본문 작성
  ```markdown
  ---
  title: "첫 번째 포스트"
  date: 2024-01-01T00:00:00+09:00
  draft: false
  tags: ["hugo", "블로그"]
  ---

  # 안녕하세요!

  첫 번째 포스트입니다.
  ```

- [ ] 로컬에서 미리보기 확인
  ```bash
  hugo server -D
  ```
  - 브라우저에서 `http://localhost:1313` 접속
  - 파일 저장 시 자동으로 새로고침됨
  - 종료: `Ctrl + C`

---

## 4. GitHub 저장소 설정

- [ ] GitHub에 새 저장소 생성
  - https://github.com/new 접속
  - Repository name 입력 (예: my-blog)
  - **Public** 선택 (Private도 가능하지만 Public 추천)
  - "Add a README file" 체크 **해제**
  - Create repository

- [ ] `.gitignore` 파일 생성
  ```bash
  cat > .gitignore << EOF
  # Hugo
  public/
  resources/_gen/
  .hugo_build.lock

  # OS
  .DS_Store
  Thumbs.db
  EOF
  ```

- [ ] 로컬 변경사항 커밋 및 푸시
  ```bash
  git add .
  git commit -m "Initial commit: Hugo blog setup"
  git branch -M main
  git remote add origin https://github.com/USERNAME/REPOSITORY.git
  git push -u origin main
  ```
  - `USERNAME`과 `REPOSITORY`를 실제 값으로 변경

---

## 5. Cloudflare Pages 배포

- [ ] Cloudflare 대시보드 로그인 (https://dash.cloudflare.com)

- [ ] Workers & Pages 메뉴로 이동

- [ ] "Create application" 클릭

- [ ] "Pages" 탭 선택 > "Connect to Git" 클릭

- [ ] GitHub 연결
  - "Connect GitHub" 클릭
  - Cloudflare Pages에 권한 허용
  - 모든 저장소 또는 특정 저장소 선택

- [ ] 배포할 저장소 선택
  - 생성한 블로그 저장소 선택
  - "Begin setup" 클릭

- [ ] 빌드 설정
  - **Project name**: 원하는 이름 입력 (URL에 사용됨)
  - **Production branch**: `main`
  - **Framework preset**: `Hugo` 선택
  - **Build command**: `hugo` (자동 입력됨)
  - **Build output directory**: `public` (자동 입력됨)
  - **Environment variables** 추가:
    - Variable name: `HUGO_VERSION`
    - Value: `0.139.3` (최신 버전 확인: https://github.com/gohugoio/hugo/releases)

- [ ] "Save and Deploy" 클릭

- [ ] 빌드 완료 대기 (보통 1-2분 소요)
  - 빌드 로그에서 진행 상황 확인 가능
  - 성공 시 "Success" 표시

- [ ] 배포된 URL 확인
  - `https://프로젝트이름.pages.dev` 형태

---

## 6. 사이트 확인 및 마무리

- [ ] Cloudflare Pages에서 제공한 URL로 접속

- [ ] 블로그가 정상적으로 보이는지 확인
  - 첫 포스팅이 표시되는지 확인
  - 테마가 제대로 적용되었는지 확인
  - 모바일 반응형 확인

- [ ] (선택) 커스텀 도메인 연결
  - Cloudflare Pages > Custom domains > "Set up a custom domain"
  - 도메인 입력 후 DNS 설정 안내 따라하기

- [ ] (선택) Analytics 설정
  - Cloudflare Web Analytics (무료, 프라이버시 중심)
  - 또는 Google Analytics 등

---

## 7. 일상적인 포스팅 워크플로우

### 새 포스트 작성

```bash
# 1. 새 포스트 생성
hugo new posts/새-포스트-제목.md

# 2. 파일 편집
# VSCode나 선호하는 에디터로 content/posts/새-포스트-제목.md 편집
# draft: false로 변경 (배포하려면)

# 3. 로컬 미리보기
hugo server -D

# 4. 확인 후 Git 커밋
git add .
git commit -m "Add: 새 포스트 제목"
git push

# 5. Cloudflare Pages 자동 빌드/배포 완료 대기 (1-2분)
```

---

## 8. 문제 해결 팁

### 빌드 실패 시
- [ ] Cloudflare Pages 빌드 로그 확인
- [ ] `HUGO_VERSION` 환경변수가 설정되어 있는지 확인
- [ ] 로컬에서 `hugo` 명령어 실행해서 오류 확인
- [ ] Git submodule이 제대로 push 되었는지 확인: `git submodule update --init --recursive`

### 테마가 적용되지 않을 때
- [ ] `hugo.toml`에서 `theme` 설정 확인
- [ ] Git submodule이 제대로 있는지 확인: `.gitmodules` 파일 존재 확인
- [ ] GitHub 저장소에 themes 폴더가 푸시되었는지 확인

### 포스트가 보이지 않을 때
- [ ] `draft: false`로 설정했는지 확인
- [ ] Front Matter 형식이 올바른지 확인
- [ ] 날짜가 미래로 설정되지 않았는지 확인

---

## 참고 자료

- Hugo 공식 문서: https://gohugo.io/documentation/
- Hugo 테마: https://themes.gohugo.io/
- Cloudflare Pages 문서: https://developers.cloudflare.com/pages/
- 마크다운 가이드: https://www.markdownguide.org/

---

## 완료!

위 체크리스트를 모두 완료하셨다면 블로그가 성공적으로 배포되었습니다. 🎉

앞으로는 마크다운으로 글을 작성하고 `git push`만 하면 자동으로 배포됩니다.