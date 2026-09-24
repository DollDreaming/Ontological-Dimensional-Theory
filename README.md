# 존재론적 차원이론(ODT) 위키

이 저장소는 ODT 공개 위키의 원본입니다. `docs/` 폴더의 마크다운 파일이 곧 위키 페이지이며, `main` 브랜치에 올리면 GitHub Pages로 자동 배포됩니다.

## 처음 한 번: 공개하기

1. GitHub에 로그인해 새 저장소를 만듭니다. 이름은 예를 들어 `odt-wiki`, 공개 범위는 **Public**.
2. zip 파일의 압축을 풀고, 이 폴더의 파일을 모두 저장소에 올립니다.
   - 웹에서 올릴 때: 빈 저장소 화면의 **uploading an existing file** 을 누르고, 이 폴더 안의 파일과 폴더를 끌어다 놓은 뒤 **Commit changes**.
   - `.github` 폴더는 숨김 폴더라 끌어 놓기에서 빠질 수 있습니다. 올린 뒤 저장소에 `.github/workflows/deploy.yml` 이 없으면, **Add file → Create new file** 에서 파일 이름 칸에 `.github/workflows/deploy.yml` 을 그대로 입력하고, 이 폴더의 같은 파일 내용을 붙여 넣어 저장하세요.
3. 저장소의 **Settings → Pages** 에서 **Source** 를 **GitHub Actions** 로 고릅니다.
4. **Actions** 탭에서 '위키 배포'가 초록색으로 끝나면(1~2분), `https://<사용자이름>.github.io/<저장소이름>/` 에서 위키가 열립니다. 처음 한 번은 **Actions → 위키 배포 → Run workflow** 로 직접 돌려야 할 수도 있습니다.
5. 사이트 주소와 저장소 주소는 `mkdocs.yml` 맨 위에 이미 들어 있습니다(`DollDreaming/Ontological-Dimensional-Theory` 기준). 저장소 이름을 바꾸면 그 줄들도 같이 바꾸세요.

## 고치기

- 웹에서 `docs/` 안의 파일을 열고 연필 아이콘 → 수정 → **Commit changes**. 1~2분 뒤 사이트에 반영됩니다.
- 새 페이지를 만들면 `mkdocs.yml` 의 `nav` 에도 한 줄 추가하세요.

## Claude가 직접 고치게 하기

한 번만 설정하면, 그다음부터는 Claude에게 할 일을 말하는 것으로 위키가 갱신됩니다.

1. <https://github.com/apps/claude> 에서 Claude GitHub 앱을 설치합니다. 저장소 선택에서 **Only select repositories** 를 고르고 이 저장소만 지정합니다.
2. <https://claude.ai/code> 에 처음 들어가면 나오는 안내에 따라 GitHub 계정을 연결합니다.
3. claude.ai/code 또는 데스크톱 앱의 Code 탭에서 이 저장소를 고르고 새 세션을 연 뒤, 할 일을 적습니다.

Claude는 `CLAUDE.md` 의 규칙대로 고치고 빌드 검사를 거쳐 `claude/` 로 시작하는 브랜치에 올린 뒤 풀 리퀘스트를 엽니다. GitHub에서 **Merge** 를 누르면 1~2분 뒤 사이트에 반영됩니다. 커밋은 연결한 GitHub 계정 이름으로 남습니다.

## 내 컴퓨터에서 미리 보기

```
pip install -r requirements.txt
mkdocs serve
```

브라우저에서 <http://127.0.0.1:8000> 을 엽니다.

## 상태 표시 쓰는 법

문장 끝에 아래 표시를 붙입니다.

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

## 라이선스

본문은 [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.ko)을 따릅니다. © 2025–2026 서원용 (Seo Won-Yong)
