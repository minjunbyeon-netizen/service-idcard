# HANDOFF - 2026-06-01 11:34

## 완료
- [x] 포트폴리오 시각 개편: 텍스트 row 리스트 → 큰 슬라이더 + TAB row + 원본 row 병존 (section 05 SELECTED WORK)
- [x] 슬라이더 레이아웃 버그 2건 픽스 — (1) 3번째 슬라이드부터 카드가 480→1336px로 늘어나며 페이지 깨짐: `.pcard .pshot img`를 `position:absolute;inset:0`로 고정. (2) 마지막 슬라이드에서 탭 스트립이 움직임: `.ptabs`를 `overflow-x:auto`→`flex-wrap:wrap`, `scrollIntoView` 제거, dots는 `transform:scale`로 변경
- [x] SELECTED WORK 위에 분양 3개사 featured 섹션 신설 (각각 별도 섹션, 10컷씩): feat-ubpa(02), feat-skview(03), feat-mqube(04) — 멀티 인스턴스 갤러리 JS(`document.querySelectorAll('.gallery').forEach`), 썸네일 strip, 라이트박스 줌
- [x] 중복돼 보이던 캡처 17장 재촬영 — 분양 사이트들이 페이지마다 같은 히어로 배너라 스크롤 0에서 찍으니 다 같아 보임 → 페이지별 고유 콘텐츠(평면도·입지 항공뷰·상업시설 CG) 나오는 Y구간으로 재캡처 후 덮어씀 (ubpa 6장·yjsk 9장·mc 2장)
- [x] 3개 섹션 제목을 실제 사이트로 하이퍼링크(↗, target=_blank, hover 시 민트색) + 소개글에서 "(라이브 10컷)" 제거
- [x] 모두 커밋·푸시 완료 (master = GitHub Pages 자동 배포)

## 진행중
- (없음)

## 대기
- (없음 — 사용자 추가 지시 대기)

## 관련 파일
- `index.html` — 유일한 산출물. 섹션 구조: hero / about(01) / feat-ubpa(02) / feat-skview(03) / feat-mqube(04) / work(05) / skills(06) / process(07) / contact(08)
- `shots/feat/*.jpg` — featured 갤러리용 캡처 30장 (사이트당 10장, 1440x900, JPEG q90)
- `shots/*.jpg` — 기존 work 슬라이더 모달용 캡처 (재사용)

## 결정사항 / 주의
- 디자인 동기: 비개발 광고주가 "디자인이 없다"고 느낄 우려 → 실물 프로젝트 비주얼 강조
- 다크 토큰 유지: `--bg:#0c0e13 --ink:#eef1f5 --sub:#8a93a3 --line:#1e232d --mint:#7cf6c8`, 폰트 Space Grotesk + JetBrains Mono
- 커스텀 글로벌 커서(`* { cursor:none }`) — 새 인터랙티브 요소 추가 시 HOVER 셀렉터 리스트에 클래스 추가 필요
- 스크롤 리빌(`.reveal`/`.in`) — 새 섹션 추가 시 `sel` 문자열에 셀렉터 추가
- **갤러리 셀 이미지 높이 함정**: auto-height grid 셀 안 `img{height:100%}`는 intrinsic 높이로 풀림 → 반드시 `position:absolute;inset:0`
- **로컬 서버**: Bash cwd 유지됨 → `cd /c/dev/services/idcard && python -m http.server 8133` (다른 디렉터리에서 띄우면 404)
- 배포 URL: https://minjunbyeon-netizen.github.io/service-idcard/
- 3개 사이트 링크: ubpa→http://ubpa.hhost.site/ , skview→https://yj-sk.co.kr/build_view.php , mqube→http://mc.hhost.site/

## 다음 세션 권장 첫 프롬프트
`/resume`
