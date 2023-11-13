# 1. 서비스 소개
<br>
<br>
<br>
<br>

# 2. 개발가이드
<br>

## Git 규칙
### Git Flow 
- master : 배포 버전
- develop : 개발 버전
- feature : 로컬 버전

### PR(Pull Request) 규칙
- 커밋은 개인 feature로만 올린다
- 깃허브에서 PR 생성 시, **개인 feature -> develop** 으로만 한다
- 팀원이 코드 리뷰 후, approve를 누르면 develop에 merge
- master는 배포시에 merge
 
## 커밋 컨벤션
### 커밋메시지
- ✨Feat(페이지 경로 또는 컴포넌트): 새로운 기능 추가 또는 기능 업데이트
- 🔨Fix(페이지 경로 또는 컴포넌트): 버그 또는 에러 수정
- ⭐️Style(페이지 경로 또는 컴포넌트): 코드 포맷팅, 코드 오타, 함수명 수정 등 스타일 수정
- 🧠Refactor(페이지 경로 또는 컴포넌트): 코드 리팩토링(똑같은 기능인데 코드만 개선)
- 📁File(페이지 경로 또는 컴포넌트): 파일 이동 또는 제거, 파일명 변경
- 🎨Design(페이지 경로 또는 컴포넌트): 디자인, 문장 수정
- 🏷Comment(페이지 경로 또는 컴포넌트): 주석 수정 및 삭제
- 🍎Chore: 빌드 수정, 패키지 추가, 환경변수 설정
- 📝Docs: 문서 수정, 블로그 포스트 추가
- 🔥Hotfix: 핫픽스 수정

### 좋은 주석을 적는 방법
1. 코드 내용을 그대로 반복하는 (추가 정보가 없는) 주석은 적지 말라.
2. 좋은 주석은 불명확한 코드를 변명하지 않는다.
    - 주석으로 코드를 설명하지 말고 코드를 다시 써라.
3. 명확한 주석을 적을 수 없다면 코드에 문제가 있을 수 있다.
    - 코드가 어렵다고 주석으로 경고하지 말고 코드를 다시 써라.
4. 주석은 혼란을 야기하는 것이 아니라 해소해야 한다.
    - 주석을 보고 더 헷갈린다면 그 주석은 지워라.
5. 관용적이지 않은(unidiomatic) 코드는 주석으로 설명하라.
    - 불필요하거나 중복된다고 생각할 수 있는 코드, 이로 인해 다른 누군가가 "단순화"할 수도 있다고 생각되는 코드에는 주석을 달아 설명하는 것이 좋다.
6. 복사한 코드라면 원본 출처 링크를 주석에 포함하라.
    - 향후 코드를 읽을 동료가 전체 컨텍스트(어떤 문제, 해당 솔루션이 권장되는 이유 등)를 파악하는 데 도움이 될 수 있음.
7. 도움이 될만한 외부 참조 링크를 포함하라.
8. 코드를 수정할 때, 특히 버그를 수정할 때 주석을 추가하라.
9. 주석을 사용해 불완전한 구현을 표시하라.
    - 기술 부채를 측정하고 해결하는 데 도움이 됨.
>https://careerly.co.kr/comments/84315?utm_campaign=user-share

## 프론트엔드 SPEC
### 프론트엔드(Flutter) 상태관리
- Provider 프레임워크 채택
- 참고글 
    >https://kkangsnote.tistory.com/247<Br>
    >https://monocsp.dev/32<br>
    >https://taej0127.medium.com/flutter-1%EB%85%84-%EB%B0%98-%EB%8F%99%EC%95%88-%EC%8D%A8%EB%B3%B4%EA%B3%A0-%EB%8A%90%EB%82%80-riverpod-%EC%9D%98-%EB%8B%A8%EC%A0%90-c4cc6f251746

### 프론트엔드 패키지 구조
- UI <-> Controller (<-> Service) <-> Repository <-> Provider

## 백엔드 SPEC
### 백엔드 패키지 구조

---

# 3. 클라이밍 앱 정리

## Tool
---
**App 기준** 
BE: Nest.js<br/>
FE: Flutter + 관리자 웹 (Vue.js)<br/>
DB: MySql<br/>
형상 관리 툴 : Git<br/>
Tool: Docker / VisualStudio Code<br/>

## 기능 및 DB
---
### 1. 회원 (JWT Token 형식으로 개발)
- 회원 가입
- 게스트 회원
---

**dbo.Member - 회원**
| MemberNo | bigint | 회원 번호 |
| --- | --- | --- |
| MemID | varchar(20) | 회원명 |
| Birth | varchar(20) | 생년월일 |
| Email | varchar(50) | 이메일 |
| Phone | varchar(12) | 휴대폰번호 |
| RegDate | datetime | 등록일 |

---

**dbo.MemberProfile - 회원 프로필**
| MemberNo | bigint |  |
| --- | --- | --- |
| MemID | varchar(20) |  |
| ProfileText | varchar(300) | 대화명 |
| Img | varchar(500) | 프로필 이미지 |

---

**dbo.GuestMember - 게스트 회원 // 추가 논의 필요**
| GuestNo | bigint | 게스트 번호 |
| --- | --- | --- |
|  |  |  |
|  |  |  |

---

**dbo.Message - 프로필 통해 연락 처리 기능**
| MessageNo | bigint |  |
| --- | --- | --- |
| FromMemNo | bigint | 메시지 발송자 |
| FromMemID | varchar(20) | // 데이터 많아질 것 우려하여 따로 아이디는 그냥 저장 |
| ToMemNo | bigint | 메시지 수신자 |
| ToMemID | varchar(20) | 메신지 수신자 아이디 |
| Text | varchar(200) |  |
| RegDate | datetime |  |

### 2. 횟수권

- 횟수권 DB

### 3. 암장 난이도

- 

### 4. 암장 지도

- 암장 DB

dbo.Climb - 암장 

| ClimbNo | int |
| --- | --- |
| ClimbName | varchar(50) |
| Phone | varchar(20) |
| LocationCode | int |
| RegDate | datetime |
|  |  |

dbo.Region - 지역 저장용 

| LocationCode | int |  |
| --- | --- | --- |
| Region | varchar(20) | 지역(경기/충북/…) |
| RegDate | datetime |  |
| AdminID | varchar(20) |  |

### 5. 예약 프로필
- 클라이밍장 예약 방문 프로필 거는 기능

**dbo.ReceptionProfile - 예약방문 프로필 DB**
| ClimbNo | bigint |  |
| --- | --- | --- |
| MemNo | bigint |  |
| ReceptYear | int | 예약할 년도 |
| ReceptMonth | int | 예약할 월 |
| ReceptDay | int | 예약할 일 |
| ReceptHour | int | 예약할 시간 |
| ReceptMin | int | 예약할 분 |
| RegDate | datetime |  |

### 6. 게시판
