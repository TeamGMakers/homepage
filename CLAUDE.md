# Team G Makers Homepage — Claude 작업 가이드

이 문서는 Team G Makers 홈페이지 저장소에서 Claude가 작업할 때 따라야 할 규칙과 워크플로우를 기록합니다. 사람이 읽어도 동일하게 이해 가능하도록 작성합니다.

## 저장소 개요

- 정적 HTML + CSS + JS (빌드 단계 없음)
- GitHub Pages로 배포 (https://www.teamgmakers.com)
- 주요 페이지: `index.html`, `support.html`, `support/parkhere.html`, `privacy.html`, `notice.html`
- 개인정보 처리방침(`privacy.html`)은 한국 「개인정보 보호법」 2026.9.11 개정 시행을 반영함

## Privacy 처리방침 개정 워크플로우 (중요)

`privacy.html`을 직접 수정하지 말 것. 아래 단계를 따른다.

1. **브랜치 생성**: `git checkout -b privacy-next-YYYYMMDD`
2. **편집**: 이 브랜치에서 자유롭게 커밋. GitHub Pages는 `main` 브랜치만 배포하므로 공개에 영향 없음
3. **확정 단계**: 브랜치를 `main`에 머지하되 **별도 파일명**(`privacy-next.html` 또는 `privacy-YYYYMMDD.html`)으로 배치. 기존 `privacy.html`은 건드리지 않음
4. **숨김 처리**: 새 파일 상단에 `<meta name="robots" content="noindex, nofollow">` 삽입, 필요 시 `robots.txt`에도 `Disallow` 추가 ("unlisted" 수준)
5. **공지 연동**: `notice.html`에서 개정안 링크로 가리킴. 이 단계에서 이용자·교차 검토 Claude·팀 검토 가능
6. **시행일 도래**: `privacy-next.html` 내용을 `privacy.html`로 이관하거나 파일 rename, 구 `privacy.html` 폐기. `notice.html` 링크 정리

**이유**: 과거 개정 작업 시 라이브 `privacy.html`을 다회 직접 수정·푸시하면서 미완성 버전이 이용자에게 노출되고 git history 정리(squash/force-push) 필요. 브랜치+별도파일 하이브리드가 "visual preview 가능 + 라이브 영향 없음"을 동시에 충족.

## 일반 원칙

- **커밋은 사용자 명시 요청 시에만** 생성. "저장해"·"커밋해"·"푸시" 등 명시 지시 전까지는 수정만 진행
- **Force push / 파괴적 git 조작**은 사용자가 직접 요청한 경우에만
- **개인 실명**(대표자 이름 등)은 git diff에 남기지 않음 — 처리방침에도 조직 명칭·부서 명칭으로 표기
- **기술 용어 최소화**: CloudKit, CKAsset, iOS Sandbox 등 개발자 용어는 이용자용 문서에 쓰지 않음. "iCloud" 같은 이용자 대면 제품명은 허용

## 관련 리소스

- 법령 템플릿 레퍼런스: [kimlawtech/korean-privacy-terms](https://github.com/kimlawtech/korean-privacy-terms)
- 교차 검토 Notion: 홈페이지 ↔ 프로젝트 교차 검토 페이지 (ID: `34a1eb15b18e8126a97beeb146a42ee0`)
