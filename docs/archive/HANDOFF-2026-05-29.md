# HANDOFF - 2026-05-29 17:54

## 프로젝트
AD 개인 포트폴리오 사이트 — 단일 파일 `C:\dev\services\idcard\portfolio-final.html`
- 컨셉: 다크(#0c0e13) + 민트(#7cf6c8) + Space Grotesk, 명함(index.html)과 통일 톤
- 정체성: "홈페이지 풀스택 개발자" (분양은 강점으로만, 전면에 안 내세움)
- 카피 톤: 대제목 영문 대문자·마침표 없음 / 한글은 짧은 보조 / 담백한 개발자 말투(자랑·AI슬롭·후기 없음)
- 디자인 룰 면제 프로젝트 (memory `project_idcard_free_design`)

## 완료
- [x] 섹션 구성: hero(파티클 구) → trust 띠 → 01 about → 02 work → 03 skills → 04 process → 05 contact (이전 voice/후기 섹션은 제거)
- [x] 파티클 구 배경(client-hive 이식) — 구↔뫼비우스 2종만, 뫼비우스 1.5배, 회전. fixed z-index:-1, mix-blend screen, 모바일 off
- [x] 크로스헤어 커스텀 커서(client-hive common.js 이식, 민트)
- [x] 스크롤 페이드업(양방향 재생), 통계 count-up(맨 아래 contact 위, 스크롤 진입 시 0→목표)
- [x] 02 work: 프로젝트 6개 = ①client-hive ②autoblog ③facing ④workcheck ⑤chunking ⑥client-gangseo
- [x] 작업물 줄 클릭 → 상세 모달(Overview/What I did/Engineering/stack). 실제 repo 코드 읽고 기술 중심으로 작성
- [x] 모달 이미지: 썸네일 갤러리(여러 장 클릭 swap) + 라이트박스 확대(메인 이미지 클릭/ESC)
- [x] 실제 화면 캡처 → `shots/`. 현재 장수: client-hive 8 · autoblog 2 · facing 2(앱+로그인) · workcheck 1 · chunking 5 · client-gangseo 7

## 진행중 / 대기 (다음 작업)
- [ ] **이미지 10장씩 채우기** — 남은 3개: autoblog·workcheck·facing (로그인/앱 필요라 미완)
  - 중단 지점: 정적 3개(client-hive/chunking/gangseo)만 다장 채움. 로그인/앱 3개는 기존 장수 그대로
  - autoblog 로그인: 슈퍼관리자 = `C:/dev/.env` 의 `APP_TEST_ADMIN_ID`/`APP_TEST_ADMIN_PASSWORD` (autoblog는 demo admin/1234 제외). 로그인 후 대시보드·템플릿·캐릭터·글생성·이력·튜토리얼·관리자 화면 캡처
  - workcheck 로그인: 데모 `admin` / `1234` (폰번호 칸에 admin 입력 → 통과). 대시보드·인원·공사·거래처·급여·양식 캡처
  - facing: 관리자 웹은 위 슈퍼계정 **안 먹음**(별도 계정) → 앱 캡처가 정답. 에뮬 `emulator-5554`(mobile-mcp)에 `com.netizen.facing.facing_app` 설치됨. Select Role 1장 완료, 더 넘기며 캡처. 세로폰이라 `fit:'contain'`

## 관련 파일
- 본체: `portfolio-final.html` (PROJECTS 배열에 프로젝트별 tag/title/sub/summary/did/tech/stack/results/imgs/fit 정의)
- 이미지: `shots/*.png` (proj0=client-hive홈, hive_2~8, proj1/1b=autoblog, proj2=facing로그인·proj2b=facing앱, proj3=workcheck, proj4/4b·chunk_3~5=chunking, proj5/5b·gangseo_3~7)
- 후보 시안(미사용): `portfolio.html`, `portfolio-a/b/c.html`, 명함 `index.html`/`claude.html`

## 결정사항 / 주의
- 로컬 미리보기: `python -m http.server 8799`(idcard 루트) → `http://localhost:8799/portfolio-final.html`. playwright는 file:// 차단 → http 서버 경유 필수
- 재캡처 시 정적 서버 다시: client-hive `--directory C:/dev/web/client-hive/web`(8801), chunking `C:/dev/web/chunking`(8802), gangseo `C:/dev/web/client-gangseo`(8803). (이번 세션 bg 서버 종료됨)
- 세로/폰 스크린샷은 `fit:'contain'`로 넣어야 안 잘림. 가로 웹샷은 cover(object-position top)
- subcri는 5번에서 빠지고 chunking으로 교체(사용자 결정). facing 정체 = WOD 페이싱(결정론 엔진)
- 비밀번호 본문에 안 적음 — `C:/dev/.env` 참조(§2-A 시크릿)

## 다음 세션 권장 첫 프롬프트
`/resume` → "autoblog·workcheck·facing 모달 이미지 10장까지 채워줘 (로그인/앱 화면 다양하게)"
