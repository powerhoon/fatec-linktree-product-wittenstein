# fatec-linktree-product-wittenstein

FATEC LinkTree에서 연결하는 WITTENSTEIN 제품 소개용 독립 정적 페이지입니다. 기존 `wittenstein-dark-shelf.html`의 화면과 링크 동작을 유지하면서 Git과 Cloudflare Pages에서 개별 관리합니다.

## 실행

```bash
python3 -m http.server 8080
```

브라우저에서 `http://127.0.0.1:8080/` 접속.

## 배포

- 공개 페이지: `https://fatec-linktree-product-wittenstein.pages.dev`
- GitHub 저장소: `https://github.com/powerhoon/fatec-linktree-product-wittenstein`
- 기본 브랜치: `main`
- Cloudflare Pages 빌드 명령: 없음
- Cloudflare Pages 출력 디렉터리: `/`
- 진입 파일: `index.html`

## 구조

```text
.
├── index.html                              # 로컬 자산을 참조하는 관리용 페이지
├── assets/
│   ├── cards/01.webp ... 08.webp           # 기존 HTML에 임베드되어 있던 카드 이미지
│   ├── fonts/inter-300.ttf ... 900.ttf      # Google Fonts Inter 로컬 사본
│   └── video/WIT_Header_products_V3.webm    # 기존 외부 hero 영상 로컬 사본
├── source/
│   ├── wittenstein-dark-shelf.original.html # 패키징 전 원본
│   └── wittenstein-dark-shelf.served-copy.html # 당시 서빙 파일의 사본
└── docs/
    ├── asset-manifest.json                 # 자산·크기·SHA-256·원본 URL 목록
    └── CODEX_HANDOFF.md                    # Codex 작업 인수인계 문서
```

## 현재 페이지 구성

- 한국어 WITTENSTEIN alpha 히어로 섹션
- WITTENSTEIN 공식 WebM 배경 영상
- 8개 제품 카테고리 카드
- 카드 이미지 8개
- Inter 300–900 로컬 폰트
- CSS는 HTML 안에 인라인으로 포함
- JavaScript 없음
- 제품 링크는 WITTENSTEIN 공식 사이트로 연결
- `/sizing-tools/` 경로에 WITTENSTEIN 공식 설계 도구로 바로 연결되는 모바일 우선 선택 페이지 제공
- sizing-tools 헤더 표기는 `WITTENSTEIN`과 `FAtec`만 사용

## 중요 사항

- `index.html`은 외부 런타임 자산 없이 실행되도록 로컬 자산을 참조합니다.
- 제품 카드의 링크 대상은 외부 WITTENSTEIN 공식 페이지입니다.
- 이미지·영상·폰트는 원본 페이지 재현을 위한 로컬 사본입니다. GitHub 공개 저장소에 push하기 전 회사의 사용권·재배포 권한을 확인해야 합니다.
- 기존 VPS 주소는 비교용 원본으로 유지하며 이 저장소와 배포는 별도로 관리합니다.
