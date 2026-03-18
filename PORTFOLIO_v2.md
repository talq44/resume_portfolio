# 박창규 — iOS Engineer
`iOS Engineer` `11년차` `팀 리딩 경험 (최대 10인)`

좋은 제품을 만드는 게 목표였고, 그 수단이 코드였습니다. AI가 그 수단의 일부를 맡아주는 지금, 제품과 팀에 더 집중할 수 있게 됐습니다.
이전부터 구조를 개선하고, 프로세스를 다듬고, 데이터로 방향을 잡아온 것도 결국 같은 이유였습니다. 제품에 더 집중하기 위해서. 지금은 그게 더 빠르게 가능해졌습니다.

29CM는 오랫동안 제가 가장 많이 참고해온 앱입니다. UI 구조를 분석하고, PR 문화를 영상으로 배우고, Tuist와 TBD를 도입할 때도, 블로그를 작성할 때도 기준점이었습니다. 이제는 함께 나아가고 싶어졌습니다.

- **GitHub** [talq44](https://github.com/talq44) · [bejewel-changkyu](https://github.com/bejewel-changkyu)

## 기술 스택

```
Core     Swift · RxSwift · ReactorKit · Combine · Async/Await
Architecture     TMA(Tuist) · Clean Architecture · MVVM · Coordinator
UI       SnapKit · FlexLayout · SwiftUI · Code-based UI
CI/CD    GitHub Actions · Xcode Cloud · Feature Flag · TBD
Data     Amplitude · Braze · Airbridge · Firebase · GA4
```

## 경력

| 회사 | 기간 | 역할 |
|---|---|---|
| 버블탭 | 2025.03 ~ 현재 | iOS 개발 |
| 비주얼 (아몬즈) | 2021.07 ~ 2024.12 | Client팀 팀장 |
| 하나모바일 | 2018.01 ~ 2021.06 | iOS 개발 |
| 새움테크 | 2015.05 ~ 2018.01 | iOS / Android 개발 |


## 대표 블로그

> 기술 판단의 배경과 팀 적용 과정을 기록한 글들입니다.

- **Blog** [medium.com/@talq44](https://medium.com/@talq44)
    - **[작은 PR, Feature Flag, TBD 그리고 자동화로 매일 develop, 매주 production 배포하는 팀 되기](https://medium.com/@talq44/작은-pr-feature-flag-trunk-based-developement-그리고-자동화로-매일-develop-매주-production-배포하는-팀-되기-1-c9b2b63f424a)** — 브랜치 전략 전환의 배경과 팀 설득 과정
    - **[GitHub Action과 Self-hosted Runner로 iOS Build Test를 돌리는 거기에 Tuist를 곁들인](https://medium.com/@talq44/github-action과-self-hosted-runner로-ios-build-test를-돌리는-거기에-tuist를-곁들인-ea4af8ace455)** — 모듈러 아키텍처와 CI 연동
    - **[유저 마음에 닿기를 — Analytics 개선기 (0)](https://medium.com/bejewel/유저-마음에-닿기를-analytics-개선기-0-ios-analytics-module-5d669dd07af1)** — Analytics 모듈 설계 의사결정 ([시리즈 전체 보기](https://medium.com/bejewel))

<br>

## 엔지니어링

> 구조가 바뀌면 팀의 속도가 바뀝니다.

### Tuist 기반 모듈러 아키텍처 구축
`비주얼` `2024` `Tuist` `TMA` `SPM` `Swinject`

**배경**
- 단일 타겟 구조로 빌드 시간 증가, 머지 컨플릭 빈발, 테스트 작성 불가

**세부 사항 / 기술 선택 이유**
- 탄탄한 커뮤니티와 문서, 지속적인 업데이트로 장기적 신뢰 가능
- 모듈 생성 스크립트(boilerplate)를 통해 팀 전체가 동일한 구조를 강제할 수 있음
- `.xcodeproj` 를 Git에서 완전히 제거할 수 있어 머지 컨플릭 근본 해결 가능
- 이미 일부 모듈화가 진행 중이어서 점진적 전환 비용이 낮았음
- `tuist build` 명령어가 단순해 GitHub Actions CI 환경과 자연스럽게 연동

**한 일**
- Application / Feature / Domain / Core / Shared 5계층 TMA 구조 설계 및 팀 적용
- CocoaPods → SPM 전환으로 Tuist 도입 기반 마련
- 모듈 자동 생성 스크립트로 팀 전체 동일 구조 강제화
- Swinject 기반 DI 구조 확립, 모듈별 테스트 작성 유도
- SwiftLint 및 미사용 파일 탐지 방식으로 Dead Code 지속 제거 — 미사용 코드를 방치하지 않아야 이후 구조 개선 비용이 낮아짐을 확인

**임팩트**
- CI 빌드 시간 **12분 → 5분 (58% 단축)**
- 테스트 커버리지 **13%p 향상**
- `.xcodeproj` Git ignore로 머지 컨플릭 사실상 제거
- 개발 속도 **10% 향상** (모듈별 독립 빌드)

**기여도** — 설계·개발 단독 주도 / 일부 전환 작업 팀 협업

**아쉬운점**
- 선행 작업(CocoaPods → SPM, Clean Architecture 적용)이 지연되며 도입 시점이 늦어짐
- 마이그레이션 중 기존 코드 제거 프로세스를 확립하지 못해 레거시가 일부 잔존
- 80% 이상 모듈 대체를 목표했으나 회사 사정으로 완수하지 못함

--- 

### ReactorKit 기반 아키텍처 전환
`비주얼` `2022` `버블탭` `2025` `ReactorKit` `RxSwift` `MVVM` `MVI` `Clean Architecture`

**배경**
- MVC 구조로 유지보수 어려움, 테스트 코드 작성의 어려움, 동일 버그 반복 발생 — 비주얼·버블탭 두 곳에서 동일한 문제를 확인

**세부 사항 / 기술 선택 이유**
- 팀이 커질수록 개인마다 다른 패턴을 사용하는 문제가 심화 — 프레임워크 자체가 구조를 강제해야 했음
- 신규 입사자가 누구여도 ReactorKit 스터디만 하면 팀 코드에 빠르게 적응 가능
- 한국인이 만든 오픈소스로 국내 레퍼런스와 커뮤니티가 풍부
- Redux/MVI 계열 단방향 데이터 흐름으로 SSOT 구조에 적합, Action/State 단위 테스트가 명확
- SwiftUI + TCA 등 최신 스택 미채택 이유: 기존 RxSwift 코드베이스가 있는 상태에서 전면 교체 시 점진적 전환이 불가능 — 팀 컨텍스트에 맞는 연속성 있는 선택

**한 일**
- [비주얼] MVC → Input/Output → ReactorKit(Action/State) 단계적 마이그레이션 주도
- [비주얼] Clean Architecture 도입으로 Presenter / Domain / Data 계층 분리
- [비주얼] Action당 테스트코드 작성 문화 정착, 팀 스터디 운영
- [버블탭] MVC → ReactorKit 전환 주도 중 (현재 35% 진행), Async/Await 기반 네트워크 모듈 병행 구축 중

**임팩트**
- 비주얼
    - QA 중 버그 티켓 발생 비율 **30% 감소**
    - 테스트 커버리지 **15%p 향상**
    - Analytics 작업 속도 타 플랫폼 대비 **40% 빠름**
    - 전체 페이지 60% 대체, Backend 병렬 작업 가능한 구조 확립

**기여도** — iOS 파트 리드 / 설계·개발 단독 주도

**아쉬운점**
- RxSwift에 강하게 묶이는 구조가 되어, 이후 Combine/Async-Await 전환 비용 발생
- 페이지 단위가 아닌 컴포넌트 단위로 분리했다면 이후 모듈화 속도가 더 빨랐을 것

--- 

### 앱 용량 개선
`비주얼` `2023~2024` `Tuist` `Design System`

**배경**
- 앱 용량 과다로 다운로드 허들 증가, 누적된 레거시 리소스·코드로 구조 개선 비용 상승

**세부 사항 / 기술 선택 이유**
- 다운로드가 지속 증가하는 시점에서 용량이 전환 허들이 될 것이라 판단해 시범적 제거 시작
- Tuist 기반 모듈화가 진행 중이었고, 미사용 코드가 모듈 분리 작업의 허들로 작용 — 코드 삭제 필요성 확인
- 사람이 직접 미사용 코드를 찾는 데 한계가 있어 자동화 도구 탐색 (Periphery 등 검토했으나 당시 지원 중단) → SwiftLint + 수동 탐지 방식 채택

**한 일**
- 미사용 폰트·이미지 정리, Design System 기반 리소스 통합
- Static/Dynamic 프레임워크 구조 재설계로 중복 메모리 제거
- SwiftLint 및 수동 탐지 방식으로 Dead Code 지속 제거
- 리소스·코드 정리를 1회성이 아닌 지속 관리 프로세스로 확립

**임팩트**
- 앱 설치 용량 **198MB → 53MB (73% 감소)** — 모듈화 초기 Static 프레임워크 중복 링킹으로 용량이 비정상적으로 증가한 상태였으며, Dynamic 전환 및 Swinject DI 구조 개선과 함께 해소
- Dead Code 제거로 이후 모듈 분리 난이도 감소

**기여도** — 분석·설계·개발 단독 주도

**아쉬운점**
- Dead Code 탐지 툴(Periphery 등)을 도입하려 했으나 당시 지원 중단으로 SwiftLint + 수동 방식으로 대체 — 자동화된 탐지 체계를 만들지 못한 아쉬움
- 용량 감소가 업데이트율 향상으로 이어질 것이라 예상했으나 유의미한 변화 없음 — 사용자 자동 업데이트 비율이 이미 높았기 때문으로 확인

---

## 워크플로우 개선

> 좋은 프로세스는 사람이 실수할 여지를 줄입니다.

### TBD + Feature Flag 도입
`비주얼` `2024` `Trunk Based Development` `Firebase RemoteConfig`

**배경**
- GitFlow의 복잡성, 잘못된 배포 후 핫픽스 비용 과다, 배포 주기 불규칙

**세부 사항 / 기술 선택 이유**
- GitFlow → GitHub Flow로 단순화하는 과정이었고, 자연스러운 다음 단계로 TBD 채택
- 국내 이커머스 팀의 TBD + Feature Flag 도입 사례를 참고해 도입 가능성 확인
- Feature Flag 플랫폼으로 Firebase RemoteConfig 선택: 무료, 높은 안정성, 개발팀만 접근하므로 실수 가능성 낮음

**한 일**
- Trunk Based Development 전환 주도, 팀 스터디 운영 (구글 엔지니어는 이렇게 일한다)
- Firebase RemoteConfig 기반 Feature Flag 시스템 구축
- 메인 브랜치 상시 배포 가능 상태 유지 체계 확립

**임팩트**
- 연간 배포 횟수 **30% 증가**
- 잘못된 배포 3회 모두 **추가 배포 없이** Feature Flag로 즉시 비활성화

**기여도** — 전략 수립·시스템 설계 주도 / iOS 개발 단독

**아쉬운점**
- App팀 외 타 파트 공통 적용을 제안했으나 받아들여지지 않아 App팀에만 적용
- Feature Flag를 기능 단위로 묶는 구조를 제안했으나 리소스 제약으로 Firebase 단순 구현에 그침

--- 

### 배포열차 도입
`비주얼` `2024` `Jira Automation` `Slack` `Xcode Cloud`

**배경**
- 업무 단위가 빨라지면서 주 단위 배포 관리 필요성 대두, 불규칙한 일정으로 QA·PO 혼선

**세부 사항 / 기술 선택 이유**
- 당근/뱅크샐러드 등의 CalVer(날짜 기반 버전 관리) 방식을 보고 주 단위 정기 배포가 충분히 가능하다고 판단
- 사람이 결정하던 배포 타이밍을 프로세스가 결정하도록 전환해 커뮤니케이션 비용 제거

**한 일**
- 주 1회 고정 배포 사이클 수립 (개발 → QA → 심사 → 배포)
- Feature Flag 완료 시 내부 자동 빌드 배포
- Jira 상태 자동화 (개발완료·배포완료 자동 전환)
- Slack 리마인더 자동화

**임팩트**
- 주당 배포 횟수 **21% 증가**
- 배포 관련 Slack 논의 **15% 감소**

**기여도** — 스쿼드 리더 / 전략·자동화 설계 주도, iOS 개발 참여

**아쉬운점**
- App Store 심사 제출까지 자동화하지 못함 — 다음 단계 과제로 남김
- 릴리즈 노트가 배포 직전에 확정되는 구조로 인해 Fastlane 기반 릴리즈 노트 자동 등록까지 이어지지 못함

---

### CI/CD 파이프라인 구축
`비주얼` `2023` `GitHub Actions` `Xcode Cloud`

**배경**
- 수동 배포로 심사 제출에 2시간 이상 소요, 브랜치 관리 체계 부재

**세부 사항 / 기술 선택 이유**
- Apple First Party로 인증서·프로비저닝·Xcode 버전 등 iOS 특화 환경을 별도 관리 없이 사용 가능
- 외부 CI 서비스 대비 설정 비용이 낮고, 추가 인프라 없이 바로 사용 가능

**한 일**
- GitHub Actions + Xcode Cloud 파이프라인 설계
- PR 시 자동 빌드/테스트, 브랜치 protection rule 설정
- 스킴 분리로 잘못된 심사 제출 방지

**임팩트**
- 심사 제출 시간 **2시간 → 30분 (75% 단축)**

**기여도** — 스쿼드 리드 / CI/CD 설계·개발 단독 주도

**아쉬운점**
- First Party임에도 빌드 속도가 느리고 간헐적 서비스 불안정 발생 — 기대 대비 안정성 부족
- Self-hosted runner 전환을 검토했으나 인프라 리소스 제약으로 보류

---

## 데이터 드리븐

> 데이터가 없으면 개선이 아니라 추측입니다.

### Analytics 모듈 구축 및 Funnel 개선
`비주얼` `2023~2024` `GA4` `Amplitude` `Braze` `Airbridge` `Modular Architecture`

**배경**
- 이벤트 체계 부재, SDK 버전 관리 불가, 플랫폼 간 데이터 불일치로 의사결정 신뢰도 낮음

**세부 사항 / 기술 선택 이유**
- 가장 범용적이고 무료로 지속 사용 가능한 표준 플랫폼
- AI 시대가 다가올수록 데이터 분석 기능이 추가될 것이라 판단 — 이후 AI 기반 데이터 분석 도구와의 연동으로 이 판단이 맞았음을 확인
- 타 SDK 대비 데이터 유실 가능성이 낮고, 이커머스 이벤트 스키마(GA4 e-commerce)가 표준화되어 있음

**한 일**
- GA4 기준 이벤트 표준화, Analytics Core 모듈 설계
- Braze/Amplitude/Airbridge SDK protocol 기반 캡슐화 (교체 가능 구조)
- 전자상거래 Funnel 이벤트 전 플랫폼 적용 주도 (view_item_list · select_item · purchase)
- 이벤트 목록 CSV 자동 추출 기능 구현

**임팩트**
- 전자상거래 데이터 신빙성 **100% 달성**
- 목록 전자상거래 이벤트 **97% 적용**
- SDK 교체 작업 **1시간 이내** 가능한 구조 확보
- Analytics 데이터가 KPI 근거 자료로 활용되기 시작

**기여도** — 스쿼드 리더 / 전략 설계 단독, iOS 개발 주도, 타 플랫폼 조율

**아쉬운점**
- 타 플랫폼(Android·Web) Analytics 모듈화를 지속 설득했으나 끝내 iOS만 적용
- 장바구니 구매 트래킹 고도화를 지속 요청했으나 우선순위에서 밀려 미완료


### 전시 개선 스크럼
`비주얼` `2021~2024` `A/B Test` `Modular Architecture` `Analytics`

**배경**
- 홈 화면 체류 시간 및 구매전환율 정체, 상품 노출 구조가 매출에 미치는 영향을 데이터로 검증할 필요

**세부 사항 / 기술 선택 이유**
- 홈 평균 체류 시간이 30초 남짓으로 지나치게 낮았음 — 에디터 콘텐츠 노력만으로는 한계
- 움직이는 화면이 있을 때 체류율이 높아진다는 데이터를 근거로 화려한 애니메이션을 전조 작업으로 진행
- 타임딜: 시간이 흐를수록 변하는 데이터(카운트다운) + 매일 접속 시 콘텐츠 변화를 체감하도록 구성 → 재방문 유도 및 긴박감 기반 구매 유도

**한 일**
- 홈 화면 구조 개선 — 배너 애니메이션 전환, 콘텐츠 배치 및 섹션 우선순위 재편
- 추천 아이템 영역 신설 및 A/B Test 검증, 타임딜·최근 본 아이템 섹션 추가
- 옵션 선택 Feature Component 모듈화 → 홈·좋아요·상품상세 공통 적용
- 장바구니 담기 후 스낵바 UX, 타임딜 초기 노출 전략 수립 (0~24시간 vs 24~48시간 구매율 비교)

**임팩트**
- 배너 애니메이션 개선으로 홈 **체류 시간 +5초**
- 추천 아이템 영역이 **전체 구매의 30%** 기여
- 타임딜 **0~24시간 구매율이 24~48시간 대비 유의미하게 높음** 확인 → 초기 노출 전략 수립 근거로 활용
- 최근 본 아이템 섹션에서 **전체 매출의 1.8%** 발생
- 장바구니 진입률 **+0.5%p**, 좋아요 화면 구매율 **+1%p**

**기여도** — 스쿼드 멤버 / iOS 개발 참여

**아쉬운점**
- 일부 작업 기간 중 전반적인 유저 이탈이 진행 중이어서 데이터 정확성에 한계
- A/B Test 수치가 예상보다 낮은 항목은 더 근본적인 UX 개선이 필요했음을 확인

---

## 리딩 경험

| 역할 | 기간 | 팀 규모 |
|---|---|---|
| Client팀 팀장 | 2024.10 ~ 2024.12 | Android 3 · iOS 3 · Web 4 (총 10명) |
| App팀 팀장 | 2023.09 ~ 2024.10 | Android 3 · iOS 3 (총 6명) |
| iOS 파트 매니저 | 2022.09 ~ 2023.09 | iOS 3명 |

**팀 운영**
- 개인별 KPI 설정 및 분기 평가 진행
- 주 1회 1:1 미팅 — 업무 진행 상황 및 개인 성장 방향 논의
- 월 1회 팀 식사 — 비공식 소통 문화 정착
- 데일리 스탠드업 미팅 운영, 스크럼 단위로 확장

**개발 문화**
- PR 리뷰 문화 개선으로 머지까지 평균 **10시간 → 4시간 단축**
- 팀장 이후에도 PR 리뷰 지속 참여 — 코드 품질 기준 유지
- 신규 입사자 온보딩 문서화 — 아키텍처·브랜치 전략·배포 프로세스 정리
- TIL(Today I Learned) 공유 문화 도입
- 스터디 주도 (ReactorKit · Clean Architecture · Clean Code · 구글 엔지니어는 이렇게 일한다)

---

## 그 외 프로젝트

| 프로젝트 | 회사 | 내용 |
|---|---|---|
| QuizLab (사이드 프로젝트) | 개인 (2025~) | SwiftUI · TCA · Async/Await · SwiftData · Firebase · App Store 출시 · 1소스 다앱(5개) 구조 · Claude Code(AI Agent) 활용 — SpecKit 기반 스펙/플랜 설계, 멀티에이전트 병렬 개발 |
| API Module 자동 생성 구축 | 버블탭 (2025) | Moya + Async/Await 기반 · OpenAPI spec → API 모듈 자동 생성 · 테스트코드 자동 구축 · 워크플로우 자동화 |
| 팅글챗 서비스 분리 | 버블탭 (2025) | 1소스 2앱 구조, xcconfig·Target 분리, CI/CD |
| 성능 모니터링 도입 | 비주얼 (2023) | Firebase Performance, 중복 API 80% 제거, Crash 공유 자동화 |
| 아몬즈 풀필먼트 출시 | 비주얼 (2021) | MAU 60만 돌파, 판매량 30% 증가 |
| 시상식 투표앱 (더서울어워즈·미스코리아·소리바다·KPMA·서울가요대전) | 하나모바일 | RxSwift MVVM, 인앱결제, 100만 건 접속 대응, 다국어(4개 언어) |
| FanPoint · 더티켓 · 흔들어대리운전 · 두줄운세 · 스마트이미지 외 | 하나모바일 | RxSwift MVVM, Socket.IO, Server-Driven UI, WebView + JavaScript Bridge |
| CJ One Card | 새움테크 | Objective-C, Server-Driven UI, 모바일 접근성(Voice Over) |
| 홈플러스 · 아주캐피탈 · 현대라이프 · 나눔로또 · 엘리시안 · thePay 외 | 새움테크 | Objective-C, WebView + JavaScript Bridge, 보안 모듈, 다수 금융·유통 SI |
