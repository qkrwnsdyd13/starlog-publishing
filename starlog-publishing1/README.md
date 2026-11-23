# STARLOG 퍼블리싱

스프링부트 백엔드 없이 HTML·CSS·이미지만 떼어 낸 버전입니다.
`index.html`을 더블클릭하거나 VS Code Live Server로 열면 바로 동작합니다.

## 구성

```
index.html          메인 (원본 home.html)
login.html          로그인
register.html       회원가입
post-list.html      게시판 목록
post-detail.html    게시글 상세
post-write.html     글쓰기
post-edit.html      글 수정
mypage.html         마이페이지
chatai.html         오늘의 운세 (AI 대화)
announcement.html   채용공고
css/                원본 CSS 그대로
images/             원본 이미지 그대로
```

## 원본과 달라진 점

- **Thymeleaf 문법(`th:...`)을 모두 제거**하고, 서버가 넣어주던 값은 샘플 데이터로 채웠습니다.
  - 게시판 목록 13건, 인기 게시글 5건, 상세 글 1건, 댓글·대댓글 예시
  - 로그인 상태는 `user1` 사용자로 로그인한 화면으로 고정
- **경로 변경**: `/static/css/...` → `css/...`, `/posts` → `post-list.html` 등 상대경로로 바꿨습니다.
- **폼 전송**: 로그인 → 메인, 회원가입 → 로그인, 글쓰기·수정 → 상세 화면으로 이동만 합니다. 실제 저장은 되지 않습니다.
- **게시글 상세**: 추천/비추천과 댓글·답글 등록이 서버 없이 화면에서만 동작합니다. 새로고침하면 원래대로 돌아갑니다.
- **에러/성공 메시지**(`.error-message`, `.success-message`, `.empty-message`)는 주석으로 남겨 두었습니다. 스타일 작업 때 주석을 풀어서 확인하세요.
- 게시판 페이지 넘김 시 표 칸이 어긋나던 문제를 수정했습니다(행에 `display:block` 대신 기본값 적용).
- 로그인 화면 로고 오타(SATRLOG → STARLOG), 마이페이지의 없는 파일 링크(starTalkAI.html → chatai.html)를 고쳤습니다.
- 백엔드 확인용 페이지 `patch.html`(크롤링 데이터 출력, CSS 없음)과 `images/` 안의 PDF는 제외했습니다.

## GitHub Pages 배포

1. 새 저장소를 만들고 **이 폴더 안의 내용물**을 저장소 맨 위(루트)에 올립니다.
   저장소 첫 화면에 `index.html`, `css/`, `images/`가 바로 보여야 합니다. 폴더째로 올리거나 zip 파일을 그대로 올리면 동작하지 않습니다.
2. 저장소 Settings → Pages → Build and deployment에서 Source는 `Deploy from a branch`, Branch는 `main` / `/(root)`로 선택한 뒤 Save를 누릅니다.
3. 1~2분 뒤 `https://<깃허브아이디>.github.io/<저장소이름>/` 으로 접속합니다.

이미지 파일명은 배포 오류를 막기 위해 영문으로 바꿨습니다(예: `로그인 페이지 이미지.png` → `login.png`).

## 백엔드에 다시 합칠 때

이 폴더의 `css/`, `images/`는 원본 `src/main/resources/static/` 아래에 그대로 덮어쓰면 됩니다.
HTML은 Thymeleaf 문법이 빠져 있으므로 원본 `templates/`를 기준으로 마크업 변경분만 옮겨야 합니다.
