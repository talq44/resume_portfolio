# 포트폴리오
## 기술 스택

``` mermaid
gantt
  dateFormat  YYYY-MM
  section Language
  Swift :i3, 2018-03, 2025-01
  typeScript :a1, 2024-10, 2024-12
  typeScript :a1, 2019-04, 2020-01
  Objective-c :l5, 2015-08, 2018-06
  Android(Java) :l4, 2015-05, 2016-06
  MFC(c++) :l3, 2014-07, 2015-04
  SQL :l2, 2012-09, 2013-01
  Android(Java) :l1, 2011-09, 2014-02

  section Architecture
  MVVM :a1, 2020-05, 2025-01
  TMA: a5, 2024-01, 2025-01
  MVI :a2, 2022-07, 2025-01
  Clean Architecture :a1, 2022-06, 2025-01
  VIPER: a4, 2022-01, 2022-06
  Ribs: a4, 2022-03, 2022-09
  VIPER: a4, 2020-06, 2021-06
  Ribs: a4, 2020-06, 2021-06
  MVC : a3, 2015-05, 2020-12

  section UI
  SwiftUI : c1, 2023-07, 2024-12
  PinLayout/FlexLayout : u3, 2022-03, 2022-07
  SnapKit : c3, 2020-01, 2025-01
  AutoLayout : c2, 2016-07, 2025-01
  Autoresizing Mask : u2, 2015-09, 2017-03
  StoryBoard : u1, 2015-09, 2023-01

  section Asynchronous
  Async/Await: r3, 2022-07, 2025-01
  Combine: r2, 2022-02, 2025-01
  RxSwift: r1, 2020-07, 2025-01

  section Analytics/Ad
  AirBridge : s3, 2023-01, 2024-12
  Ampltude : s2, 2022-03, 2024-12
  Braze : s2, 2021-07, 2024-12
  Google Ads: aa2, 2019-11, 2021-06
  IGAWorks : aa1, 2018-01, 2021-06
  FireBase(GoogleAnayltics) : s2, 2016-12, 2025-01
```
## 경력 사항

``` mermaid
gantt
  dateFormat  YYYY-MM
  비주얼 :i3, 2021-07, 2024-12
  하나모바일 :i2, 2018-01, 2021-06
  새움테크 :i1, 2015-05, 2018-01
  유니텍 : c1, 2014-07, 2015-04
  강원대학교 :a2, 2011-09, 2013-03
```

## 비주얼 (21.07 ~ 24.12)

### 아몬즈 아키텍처 개선 Tuist 적용 및 TMA 구조 확립 (24.04 ~ 24.12)

<table style="width: 100%;">
<tr>
<td style="width: 150px;"> 역할 </td>
<td>
iOS 개발 및 리딩 (참여인원: iOS 3)
</td>
</tr>
<td> 주요 기술 </td>
<td>
Tuist, Swinject  

</td>
</tr>

<td> 도전 과제 및 해결 방법 </td>
<td>
Application / Feature / Domain / Core / Shared 계층 분리<br>
모듈별 구조 확립 및 테스트 코드 작성 유도<br>
모듈생성시 스크립트를 통해 동일한 구조로 자동 생성

```mermaid
flowchart TD
  FeatureExample --> Feature
  FeatureExample --> FeatureTesting
  Feature --> FeatureInterface
  FeatureTests --> Feature
  FeatureTests --> FeatureTesting
  FeatureTesting --> FeatureInterface
  
```

</td>
</tr>
<td> 성과/지표 </td>
<td>

CI 빌드테스트 속도 50% 감소(12분 -> 5분)<br>
개발속도 10% 증가(모듈별 빌드)<br>
테스트 커버리지 13% 증가<br>
머지 컨플릭 비율 감소(.xcodeproj/* ignore)<br>
[관련 블로그](https://medium.com/@talq44/github-action과-self-hosted-runner로-ios-build-test를-돌리는-거기에-tuist를-곁들인-ea4af8ace455)

</td>
</tr>
<td> 배운점 </td>
<td>
명확한 계층정의로 협업 맴버 공통된 형태의 모듈 개발<br>
모듈별 테스트가 추가되어 안정성 향상<br>
project 파일이 더이상 추가되지 않아 코드 형상 관리가 간편해짐

</td>
</tr>
</table>

### App팀 배포열차 도입 (24.07 ~ 24.12)

<table style="width: 100%;">
<tr>
<td style="width: 150px;"> 역할 </td>
<td>
스쿼드 리더 (참여 인원 : Android 1, iOS 1, PO 1, QA 1)
</td>
</tr>
<td> 주요 기술 </td>
<td>
Trunk Based Develpment(TBD), Feature Flag, Jira Automation, Slack
</td>
</tr>
<td> 도전 과제 및 해결 방법 </td>
<td>
배포 관련 일정 논의 및 결정(매주 1회, 검수 프로세스 월~목, 심사 제출 금, 실 배포 화)
</td>
</tr>
<td> 성과/지표 </td>
<td>
주마다 배포 횟수 21% 증가  / 슬랙 배포 관련 논의 15% 감소

</td>
</tr>
<td> 배운점 </td>
<td>
유연한 CI/CD를 정해둬 어렵지 않게 적용.

</td>
</tr>
</table>

### Swagger -> Swift 파일 전환 자동화 (23.05 ~ 23.06)
| **항목**              | **내용**                                                       |
|----------------------|---------------------------------------------------------------|
| **주요 기술**           | OpenAPISpec 3.0, RestfulAPI, Moya, Alamofire, yaml   |
| **도전 과제 및 해결 방법** | 배포 관련 일정 논의 및 결정(매주 1회, 검수 프로세스 월~목, 심사 제출 금, 실 배포 화) |
| **성과/지표**           | API관련 이슈 90% 감소, 디코딩 에러 파악율 100% 달성, 작업속도 10% 이상 증가, 관련 블로그 작성 |
| **배운 점**            | 사람은 실수를 할 수 있어도, 기계는 실수하지 않는다. 자동화된 테스트코드 생성이 안정성 증가에 큰 도움을 줌   |

### Clean Architecture 도입 및 개선(23.02 ~ 23.12)
| **항목**              | **내용**                                                       |
|----------------------|---------------------------------------------------------------|
| **역할**               | 팀 스터디 리딩 및 iOS 메인 개발 (참여 인원: Android 2, iOS 3, QA 1)          |
| **주요 기술**           | Clean Architecture, Present/Domain/Data Layer   |
| **도전 과제 및 해결 방법** | DTO의 view에서 사용하는 비율 축소, Domain의 분리, API 모듈 분리 |
| **성과/지표**           | 관련 블로그 작성, Android <-> iOS 통일성 향상(도메인 30% 로직 통일), 버그율 13% 감소 |
| **배운 점**            | 참여인원 모두 공부가 필요, 비개발자도 이해할 수 있는 설명 진행, 계층을 나누기 위해서도 그안에 명확한 정의 필요               |

### ReactorKit을 활용한 ViewModel 마이그레이션 (22.03 ~ 22.12)

| **항목**              | **내용**                                           |
|----------------------|---------------------------------------------------|
| **역할**               | 스터디 주최 및 iOS 개발                                           |
| **주요 기술**           | ReactorKit, MVVM, Action/State, RxSwift                                    |
| **도전 과제 및 해결 방법** | viewDelegate선언 및 viewModel에 viewDelegate 주입,                             |
| **성과/지표**           | 전체 화면 중 30% 적용, Crash율 0.5% 상승, 버그율 10% 상승                                             |
| **배운 점**             | 업무 파악 전 무리한 적용으로 안정성 하락, 명확한 아키텍처 통일 필요, 테스트 코드 필요성 확인, 팀원간 협업 및 내용 공유 부족함을 실감  |

<div style="text-align: center;">
  <img src="https://cloud.githubusercontent.com/assets/931655/25098066/2de21a28-23e2-11e7-8a41-d33d199dd951.png" alt="description" width="500">
</div>

### MVC -> MVVM 개선 (21.10 ~ 22.01)

| **항목**              | **내용**                                           |
|----------------------|---------------------------------------------------|
| **역할**               | iOS 개발                                           |
| **주요 기술**           | MVVM, input/output 패턴         |
| **도전 과제 및 해결 방법** | viewDelegate선언 및 viewModel에 viewDelegate 주입<br> 하락                             |
| **성과/지표**           | 전체 화면 중 30% 적용, Crash율 0.5% 상승, 버그율 10% 상승                                             |
| **배운 점**             | 업무 파악 전 무리한 적용으로 안정성 하락, 명확한 아키텍처 통일 필요, 테스트 코드 필요성 확인, 팀원간 협업 및 내용 공유 부족함을 실감  |


## 하나모바일 (18.01 ~ 21.06)
### 다다
### 더티켓
### 흔들어대리운전
### 두줄운세
### 위피캠
### Pickmecam
### BizID

### 더스타 온라인 iOS/Web

### Enjoy J Tour

### 2018 KPMA

### 2018 서울가요대상

### 2018 더서울어워즈

### 스마트이미지

### 미스코리아(투표)

### FanPoint

## 새움테크 (15.05 ~ 18.01)
### 마이홈플러스포인트

### 와인그래프

### 나눔로또

### 우리캐피탈

### 현대라이프 상담사용

### CJ One Card

### 아주캐피탈 

### 99Pay

### thePay

### 엘리시안

<table>
  <tr>
    <td> 이미지 </td>
    <td> <img src="asset/elysian/image_01.png" alt="이미지1" /> </td>
    <td> <img src="asset/elysian/image_02.png" alt="이미지1" /> </td>
    <td> <img src="asset/elysian/image_03.png" alt="이미지1" /> </td>
    <td> <img src="asset/elysian/image_04.png" alt="이미지1" /> </td>
  </tr>
  <tr>
    <td>사용기술</td>
    <td colspan="4"> 내용 입력</td>
  </tr>
  <tr>
    <td>설명</td>
    <td colspan="4"> 내용 입력</td>
  </tr>
</table>


## 유니텍 (14.07 ~ 15.04)
### MFCC 

## 강원대학교 전산원 (11.07 ~ 13.02)
### 강원대학교 App
