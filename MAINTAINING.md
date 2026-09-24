# 관리 안내

위키를 고치고 관리하는 방법입니다. 방문자용 소개는 [README](README.md)에 있습니다.

## 어떻게 돌아가나

`docs/` 폴더의 마크다운 파일이 곧 위키 페이지입니다. 한국어 쪽 `page.md` 옆에 영문 쪽 `page.en.md`가 짝으로 있고, 영문 사이트는 `/en/` 아래에 만들어집니다(머리글의 언어 버튼으로 오갑니다). `main` 브랜치에 변경이 들어가면 GitHub Actions의 "위키 배포"가 사이트를 다시 만들어 GitHub Pages에 올립니다. 1~2분 걸립니다.

## 쪽마다 최신본

쪽마다 지금의 내용만 싣습니다. 지난 내용은 저장소의 변경 이력(커밋)에 남으므로, 본문에 판 번호나 옛 판과의 대조를 쓰지 않습니다.

## 자동 갱신

`docs/`의 쪽은 저자 PC의 위키 원본에서 옵니다. 저자 PC에서 하루 한 번, 원본에서 바뀐 쪽만 복사해 검사를 통과하면 바로 게시합니다(저자 결정, 2026-09-24).

- 한국어 쪽이 바뀌었는데 영문 짝이 그대로면 그 쪽만 Claude Code가 영어로 옮깁니다. 번역이 끝나기 전에는 영문 쪽 위에 "Translation in progress" 상자가 붙습니다.
- 검사: 저자 인용이 저자 원문 기록에 글자 그대로 있나, 영문 짝의 구조(제목 · 링크 · 수식 · 표 · 상자 · 상태 표시)가 한국어 쪽과 같나, 내부 이름 · 경로 · 연락처가 섞이지 않았나, `mkdocs build --strict`가 통과하나, 변경이 너무 크지 않나.
- 검사에 걸린 쪽은 올리지 않고 저자에게 알립니다. 빌드가 깨지거나 변경이 너무 크면 `claude/wiki-sync-hold` 브랜치에 둡니다. `main`과 비교해 보고 괜찮으면 합치면 됩니다.
- 쪽을 새로 만들거나 지우는 일은 메뉴(`mkdocs.yml`의 `nav`)를 함께 정해야 해서 자동으로 하지 않습니다.
- 자동 갱신 커밋은 작성자가 `Claude (위키 자동 갱신)`으로 찍히고, 메시지에 바뀐 쪽이 적힙니다.
- 잘못 올라간 갱신은 Claude에게 "마지막 위키 갱신 되돌려 줘"라고 하면 됩니다. 저자 PC에서 그 커밋을 되돌린 판을 올리고, 사이트도 다시 배포됩니다.
- 이 저장소에서 `docs/`를 직접 고치면 자동 갱신이 그 쪽을 덮어쓰지 않고 저자에게 알립니다. 원본에도 같은 수정을 해 두어야 다음 갱신 때 어긋나지 않습니다.

## Claude에게 맡기기

claude.ai/code 또는 데스크톱 앱의 Code 탭에서 이 저장소를 고르고 새 세션을 연 뒤 할 일을 적습니다. Claude는 `CLAUDE.md`의 규칙대로 고치고 빌드 검사를 거쳐 `claude/`로 시작하는 브랜치에 올린 뒤 풀 리퀘스트를 엽니다. GitHub에서 **Merge**를 누르면 사이트에 반영되고, 작업 브랜치는 자동으로 지워집니다.

## 직접 고치기

- 웹에서 파일을 열고 연필 아이콘 → 수정 → **Commit changes**를 누릅니다. `docs/`의 쪽이라면 위 "자동 갱신"의 마지막 항목을 보세요.
- 새 페이지는 한국어 `이름.md`와 영문 `이름.en.md`를 함께 만들고, `mkdocs.yml`의 `nav`에 한 줄, `nav_translations`에 영문 메뉴 이름을 더합니다.
- 저장소 이름을 바꾸면 `mkdocs.yml` 맨 위의 `site_url`, `repo_url`, `repo_name`도 같이 바꿉니다.

## 내 컴퓨터에서 미리 보기

```
pip install -r requirements.txt
mkdocs serve
```

브라우저에서 <http://127.0.0.1:8000>을 엽니다. 영문판은 <http://127.0.0.1:8000/en/>입니다.

## 상태 표시 쓰는 법

성격이 다른 설명에만 붙입니다. 표시가 없는 문장은 저자의 이론 본문입니다. 제목에 붙일 때는 `{ data-toc-label="제목" }`도 함께 달아 목차에 표시어가 섞이지 않게 합니다.

| 표시 | 영문 | 뜻 | 쓰는 법 |
|---|---|---|---|
| 대응 | Correspondence | ODT의 틀로 다른 분야의 개념을 짝지은 것 | `<span class="st st-int">대응</span>` |
| 차용 | Borrowed | 다른 이론에서 빌려 온 가정 | `<span class="st st-bor">차용</span>` |
| 가설 | Hypothesis | 아직 검증되지 않은 주장이나 예측 | `<span class="st st-hyp">가설</span>` |
| 열림 | Open | 아직 정해지지 않은 물음 | `<span class="st st-rev">열림</span>` |

## 영문 쪽 머리

영문 쪽 맨 위에는 짝 한국어 쪽의 지문이 있습니다.

```
---
ko_sha: 3858d9c280804f75
---
```

한국어 쪽 파일의 sha256 값 앞 16자입니다. 한국어 쪽을 고치고 영문 쪽도 맞췄다면 이 값을 새로 계산해 넣습니다.

```
python -c "import hashlib,sys; print(hashlib.sha256(open(sys.argv[1],'rb').read()).hexdigest()[:16])" docs/index.md
```

이 값이 옛값이면 자동 갱신이 영문이 낡았다고 보고 그 쪽을 다시 옮깁니다.

## 폴더 구성

| 경로 | 내용 |
|---|---|
| `docs/index.md` | 대문 |
| `docs/principles/` | 핵심 원리, 연결 구조, 시간 |
| `docs/dimensions/` | 1~9성 각 쪽 |
| `docs/interpretations/` | 물리학 · 정보이론 · 의식과 자아 · 학문 통합 · 인공지능 |
| `docs/research/open-problems.md` | 열린 과제 |
| `docs/glossary.md` | 용어집 |
| `docs/about.md` | 이 위키에 대해 |
| `docs/**/*.en.md` | 각 쪽의 영문판 |
| `mkdocs.yml` | 사이트 설정, 메뉴, 영문 메뉴 이름 |
| `requirements.txt` | 빌드에 쓰는 패키지(MkDocs, Material 테마, 두 언어 플러그인) |
| `.github/workflows/deploy.yml` | 자동 배포 설정 |
| `CLAUDE.md` | Claude가 위키를 고칠 때 따르는 규칙 |
| `README.md` | 저장소 첫 화면의 방문자용 소개 |
