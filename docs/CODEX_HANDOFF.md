# Codex 인수인계 — WITTENSTEIN Dark Shelf

## 목표
현재 운영 중인 WITTENSTEIN Dark Shelf 페이지를 독립적인 정적 웹 프로젝트로 Git 관리하고, 이후 Codex가 수정·검수·배포할 수 있게 한다.

## 기준 원본
- 현재 서빙 URL: `http://72.62.74.36:8080/wittenstein-dark-shelf.html`
- 원본 파일: `/root/wittenstein-dark-shelf.html`
- 원본 SHA-256: `docs/asset-manifest.json`의 `source_sha256` 참조
- 패키지 진입점: `index.html`

## 작업 범위
- 화면 구조와 디자인을 유지한 상태에서 코드 관리 구조로 전환
- 외부로 참조하던 영상과 폰트를 로컬 자산으로 수집
- HTML 내부에 임베드되어 있던 8개 WebP 이미지를 `assets/cards/`로 분리
- 제품 링크, 문구, 반응형 동작을 필요에 따라 개선
- 수정 후 로컬 렌더링 및 링크 동작 검수

## 현재 기술 구조
- 순수 HTML/CSS
- JavaScript 없음
- 빌드 도구 없음
- 외부 JS 라이브러리 없음
- 로컬 정적 서버만 있으면 실행 가능
- `index.html`에서 `assets/` 상대경로 사용

## 제품 링크

1. Servo Gearboxes — `https://www.wittenstein-group.com/int-en/products/servo-gearboxes`
2. Servo Motors — `https://www.wittenstein-group.com/int-en/products/servo-motors`
3. Rack & Pinion Systems — `https://www.wittenstein-group.com/int-en/products/rack-and-pinion-systems`
4. Servo Actuators — `https://www.wittenstein-group.com/int-en/products/servo-actuators`
5. Servo Drive Systems — `https://www.wittenstein-group.com/int-en/products/servo-drive-systems`
6. Servo Drives — `https://www.wittenstein-group.com/int-en/products/servo-drives`
7. Software & Digitalization — `https://www.wittenstein-group.com/int-en/products/software-and-digitalization`
8. Accessories — `https://www.wittenstein-group.com/int-en/products/accessories`

## Codex 작업 시 주의사항

- `source/` 아래 원본 파일은 기준 비교용이므로 직접 수정하지 않는다.
- 디자인 변경 전 현재 화면을 기준으로 스크린샷을 남긴다.
- 제품 링크는 임의로 변경하지 말고 공식 URL 응답을 확인한다.
- WITTENSTEIN 이미지·영상·폰트의 재배포 권한을 확인하기 전 공개 GitHub 저장소에 push하지 않는다.
- 외부 서비스 게시·배포·DNS·VPS 설정 변경은 사용자 승인 후 수행한다.
- 비밀값, API 키, 서버 인증정보를 저장소에 넣지 않는다.

## 검수 명령

```bash
python3 -m http.server 8080
```

확인 항목:

- 8개 카드가 모두 렌더링되는가
- hero WebM이 재생되는가
- 모바일에서 2열·1열 반응형이 정상인가
- 카드 hover 확대 및 이미지 밝기 전환이 정상인가
- 8개 공식 제품 링크가 올바른 탭으로 열리는가
- Network 탭에 누락된 로컬 자산이 없는가
- 원본과 비교해 문구·카테고리 순서·레이아웃이 의도대로 유지되는가

## 완료 조건

- 변경 파일과 이유를 명시
- 로컬 실행 결과 기록
- 데스크톱·모바일 검수 결과 기록
- 링크 점검 결과 기록
- 공개 배포가 필요한 경우 배포 전 승인 요청
