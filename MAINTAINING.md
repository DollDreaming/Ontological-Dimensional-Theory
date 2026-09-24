# 관리 안내

위키를 고치고 관리하는 방법입니다. 방문자용 소개는 [README](README.md)에 있습니다.

## 어떻게 돌아가나

`docs/` 폴더의 마크다운 파일이 곧 위키 페이지입니다. `main` 브랜치에 변경이 들어가면 GitHub Actions의 "위키 배포"가 사이트를 다시 만들어 GitHub Pages에 올립니다. 1~2분 걸립니다.

## Claude에게 맡기기

claude.ai/code 또는 데스크톱 앱의 Code 탭에서 이 저장소를 고르고 새 세션을 연 뒤 할 일을 적습니다. Claude는 `CLAUDE.md`의 규칙대로 고치고 빌드 검사를 거쳐 `claude/`로 시작하는 브랜치에 올린 뒤 풀 리퀘스트를 엽니다. GitHub에서 **Merge**를 누르면 사이트에 반영되고, 작업 브랜치는 자동으로 지워집니다.

## 직접 고치기

- 웹에서 `docs/` 안의 파일을 열고 연필 아이콘 → 수정 → **Commit changes**를 누릅니다.
- 새 페이지를 만들면 `mkdocs.yml`의 `nav`에도 한 줄 추가합니다.
- 저장소 이름을 바꾸면 `mkdocs.yml` 맨 위의 `site_url`, `repo_url`, `repo_name`도 같이 바꿉니다.

## 내 컴퓨터에서 미리 보기

```
pip install -r requirements.txt
mkdocs serve
```

브라우저에서 <http://127.0.0.1:8000>을 엽니다.

## 상태 표시 쓰는 법

문장이나 제목 끝에 아래 표시를 붙입니다. 제목에 붙일 때는 `{ data-toc-label="제목" }`도 함께 달아 목차에 표시어가 섞이지 않게 합니다.

| 표시 | 쓰는 법 |
|---|---|
| 정의 | `<span class="st st-def">정의</span>` |
| 유도 | `<span class="st st-der">유도</span>` |
| 해석 | `<span class="st st-int">해석</span>` |
| 차용 | `<span class="st st-bor">차용</span>` |
| 가설 | `<span class="st st-hyp">가설</span>` |
| 개정 중 | `<span class="st st-rev">개정 중</span>` |

## 폴더 구성

| 경로 | 내용 |
|---|---|
| `docs/index.md` | 대문 |
| `docs/principles/` | 핵심 원리, 연결 구조, 시간 |
| `docs/dimensions/` | 1~9성 각 쪽 |
| `docs/interpretations/` | 물리학·정보이론·의식과 자아·학문 통합·인공지능 |
| `docs/research/` | 열린 과제, 판본 이력 |
| `docs/glossary.md` | 용어집 |
| `docs/about.md` | 이 위키에 대해 |
| `mkdocs.yml` | 사이트 설정과 메뉴 |
| `.github/workflows/deploy.yml` | 자동 배포 설정 |
| `CLAUDE.md` | Claude가 위키를 고칠 때 따르는 규칙 |
| `README.md` | 저장소 첫 화면의 방문자용 소개 |
