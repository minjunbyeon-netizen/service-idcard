# HANDOFF - 2026-06-08 12:19

## 완료
- [x] `/doctor` 신고 16건 수정 — `C:\Users\USER\.claude\settings.json`(글로벌)의 무효 권한 규칙(`mcp__github__get_*` 등 부분 글로브)을 읽기 전용 도구명 단건 81개로 교체. github·supabase·linear·sentry·replicate·vercel 6개 서버. 쓰기 도구는 의도적 제외(§4 "write는 묻기 유지"). JSON 검증 통과, allow 규칙 총 124개. **다음 Claude Code 재시작부터 적용**(현 세션은 옛 규칙 메모리 상주). `mcp__exa__*`/`mcp__tavily__*` 전체 와일드카드는 유효 패턴이라 유지
- [x] idcard 포트폴리오 로컬 QA — `python -m http.server 8133` + playwright. 콘솔 에러 0, 깨진 이미지 0(빈 src 1건은 라이트박스 placeholder 정상), 8섹션·3갤러리 정상. 풀페이지 정적 캡처가 비어 보인 건 스크롤 리빌(`.reveal`) 정상 동작. **코드 변경 없음**
- [x] 웅진프리드라이프 명함(황채민) 인쇄용 PDF 제작 — 바탕화면 PNG 2장(앞/뒤)을 92×52mm(재단 90×50 + 사방 1mm bleed) 2페이지 PDF로. 결과: `C:\Users\USER\Desktop\프리드라이프_명함_황채민_인쇄용.pdf`(약 457 DPI, RGB)

## 진행중
- (없음)

## 대기
- [ ] 명함 PDF CMYK 변환본 — 사용자 요청 시. 주의: ICC 프로파일 없는 PIL 변환은 파란색 탁해짐. 인쇄소 RGB 입고 자체 변환 가능하면 불필요
- [ ] 명함 재단선(트림마크)·여백 가이드 표시본 — 사용자 요청 시

## 관련 파일
- idcard 산출물: `index.html` 단일 파일 + `shots/` 캡처 (이번 세션 미변경)
- 명함(레포 밖): 원본 `C:\Users\USER\Desktop\f1abbff2-...png`(앞)·`b4cfd07a-...png`(뒤) / 결과 `...\프리드라이프_명함_황채민_인쇄용.pdf` / 규격 참고 `...\프리드라이프 명함.pdf`(92×52mm)
- 글로벌 설정: `C:\Users\USER\.claude\settings.json`

## 결정사항 / 주의
- 인쇄 규격 SSOT: 재단 90×50mm + 사방 1mm bleed = 작업 92×52mm (260.8×147.4pt). 직전 프리드라이프 명함 PDF와 동일
- 명함 비율이 풀블리드 비율(1.769)과 거의 같아 cover-fit으로 단색 배경 가장자리 1% 미만만 크롭 — 텍스트/로고/인물 손실 없음(미리보기 확인)
- 제작 스크립트 스택: PIL(cover_crop) + reportlab(mm pagesize) + pypdf(검증) + PyMuPDF(미리보기 렌더)
- QA/미리보기 임시 산출물(jpeg·png)은 레포에 남기지 않음 — autopush(Stop hook git add -A) 커밋 방지 위해 삭제
- 로컬 서버: `cd /c/dev/services/idcard && python -m http.server 8133`(다른 cwd면 404). 현재 백그라운드 :8133 떠 있을 수 있음
- 배포 URL: https://minjunbyeon-netizen.github.io/service-idcard/

## idcard 디자인 참고 (이전 세션 인계 — 보존)
- 다크 토큰: `--bg:#0c0e13 --ink:#eef1f5 --sub:#8a93a3 --line:#1e232d --mint:#7cf6c8`, 폰트 Space Grotesk + JetBrains Mono
- 커스텀 글로벌 커서(`* { cursor:none }`) — 새 인터랙티브 요소 추가 시 HOVER 셀렉터 리스트에 클래스 추가
- 스크롤 리빌(`.reveal`/`.in`) — 새 섹션 추가 시 `sel` 문자열에 셀렉터 추가
- 갤러리 셀 이미지 높이 함정: auto-height grid 셀 안 `img{height:100%}`는 intrinsic 높이로 풀림 → 반드시 `position:absolute;inset:0`
- 3개 featured 사이트 링크: ubpa→http://ubpa.hhost.site/ , skview→https://yj-sk.co.kr/build_view.php , mqube→http://mc.hhost.site/

## 다음 세션 권장 첫 프롬프트
`/resume`
