
# HelloPet 🐾
<img width="825" height="461" alt="image" src="https://github.com/user-attachments/assets/798d9b76-1b47-4dea-b53c-72b46c82b669" /><br /> 


<p align="center">
  <img src="https://github.com/user-attachments/assets/ca40ef11-9097-4ed7-838a-b7c5b5da620e"
       alt="핫 데이터 In-Memory 캐시"
       width="49%" 
      height="240px"/>
  <img src="https://github.com/user-attachments/assets/785121dc-89bf-45dc-aa5a-0e407e52e7f7"
       alt="DTO·@Modifying 최적화"
       width="49%" 
      height="240px"/>
</p>

SESAC 7기 B팀이 개발한 **유기동물 입양 서비스 플랫폼**입니다.<br /> 
반려동물 인구 증가에 따라 높아진 유기동물 문제를 해결하고, 입양 정보 접근성을 향상시키기 위해 만들어졌습니다.<br />
유기동물 자연사·안락사 비율이 증가하는 현황을 해결하고자 합니다. <br />

## 목차
1. 기능  
2. 기술 스택  
3. 아키텍처
4. 워크플로우  
5. 시연  
6. 테스트  
7. 성능 최적화  
8. 로드맵  
9. 팀  

---

## 1. 기능  

| 모듈 | 주요 기능 |
|------|-----------|
| **사용자 관리** | 회원가입(관리자·보호소·입양자), 프로필 수정(닉네임·비밀번호·주소·이미지), <br />계정 비활성화 기능, 인증/인가 기능 제공|
| **입양 동물 등록** | 보호소가 동물 정보(품종·나이·건강·사진 등) 등록, 상태 변경(보호중 ↔ 입양완료), 공고 삭제 |
| **입양 신청 관리** | 입양자가 신청서 작성·조회, 보호소가 공고별 신청서 승인/상태 관리, 신청서 삭제 |
| **자유 게시판** | Q&A/커뮤니티 글·댓글 CRUD, 페이지네이션·카테고리·정렬 지원, 마이페이지 글/댓글 관리 |  

## 2. 기술 스택 
### Frontend
- **Next.js** (SSR/CSR)  
- Axios  
- Zustand (상태관리)  
- Tailwind CSS  
### Backend
- **Spring Boot** / Spring Security  
- JPA (Hibernate)  
- PostgreSQL  
- Docker (컨테이너 배포)

## 3. 아키텍처

<details>
<summary><strong>📁 프론트 구조</strong></summary>

```
.
├── (site)
│   ├── 401
│   ├── 403
│   ├── announcements
│   │   ├── [id]
│   │   │   ├── applications
│   │   │   ├── apply
│   │   │   └── form
│   │   ├── create
│   │   └── edit
│   │       └── [id]
│   ├── applications
│   │   └── [id]
│   ├── boards
│   │   ├── [id]
│   │   │   └── update
│   │   └── new
│   └── me
├── auth
│   ├── edit
│   ├── login
│   ├── signup
│   └── withdraw
├── components
│   ├── announcementApplications
│   ├── application
│   │   └── form
│   │       └── section
│   └── boards
├── lib
├── store
└── types
```

</details>
<details>
<summary><strong>📁 백엔드 구조</strong></summary>

```
.
├── common
│   ├── aspect
│   ├── store
│   └── utils
│       └── security
├── domain
│   ├── announcement
│   │   ├── controller
│   │   ├── dto
│   │   │   ├── request
│   │   │   └── response
│   │   ├── entity
│   │   ├── repository
│   │   └── service
│   ├── application
│   │   ├── controller
│   │   ├── dto
│   │   │   ├── request
│   │   │   └── response
│   │   │       └── detail
│   │   ├── entity
│   │   │   └── info
│   │   │       ├── agreement
│   │   │       ├── care
│   │   │       ├── experience
│   │   │       ├── family
│   │   │       ├── financial
│   │   │       ├── housing
│   │   │       └── plan
│   │   ├── repository
│   │   ├── service
│   │   └── validation
│   ├── auth
│   │   ├── authController
│   │   ├── authService
│   │   ├── dto
│   │   │   ├── request
│   │   │   └── response
│   │   ├── entity
│   │   └── repository
│   ├── board
│   │   ├── controller
│   │   ├── dto
│   │   │   ├── request
│   │   │   └── response
│   │   ├── entity
│   │   ├── repository
│   │   └── service
│   ├── comment
│   │   ├── controller
│   │   ├── dto
│   │   │   ├── request
│   │   │   └── response
│   │   ├── entity
│   │   ├── repository
│   │   └── service
│   └── user
│       ├── controller
│       ├── dto
│       │   ├── request
│       │   └── response
│       ├── entity
│       ├── repository
│       └── service
└── global
    ├── annotation
    ├── config
    ├── exception
    │   ├── custom
    │   ├── dto
    │   │   └── response
    │   └── handler
    └── filter
```

</details>

## 4. 워크플로우  
#### **GitHub Flow** 전략: 기능 단위 브랜치 → PR → main 병합.  
#### 칸반 보드와 브랜치/커밋 ID 연동으로 추적성 확보.<br /><br /><br />
<details>
  <summary>Notion을 활용한 프로젝트 관리</summary>
<img width="638" height="403" alt="image" src="https://github.com/user-attachments/assets/25256957-d5af-456e-824d-878141cb81c9" />
  <br />아키텍처, 커뮤니케이션, 칸반을 한 보드에 통합해 “단일 소스 오브 트루스(SSoT)” 확보
</details><details>
  <summary>sprint 회의와 마일스톤 설정</summary>
<img width="839" height="326" alt="image" src="https://github.com/user-attachments/assets/280552da-faba-47b4-ac19-2f8a577b8ebc" />
  <br />분기·주간 마일스톤을 타임라인에 시각화하여 목표·기한을 명확화


</details><details>
  <summary>엔티티 설정</summary>
<img width="562" height="443" alt="image" src="https://github.com/user-attachments/assets/12f34284-2b1c-4b00-b024-c6db3d903752" />
  <br />Board, Announcement 등 핵심 도메인 클래스를 초기에 명세해 팀 전체의 데이터 모델 이해 통일
</details><details>
  <summary>요구 사항 설정</summary>
<img width="704" height="440" alt="image" src="https://github.com/user-attachments/assets/802d121d-65db-42fb-88e9-5baf20bb1fa1" />
  <br />역할·데이터·예외 흐름까지 한눈에 보여 개발·테스트 범위 오해 최소화
</details><details>
  <summary>데이터 설정</summary>
<img width="879" height="401" alt="image" src="https://github.com/user-attachments/assets/ce5da51f-762f-45f9-9727-dc483da9dba9" />
  <br />기능 명세서를 이어받아 엔드포인트·HTTP 메서드·Status Code를 체계화

예제 Request/Response 포함 → 프론트·백 간 계약(Contract) 안정화
</details>

<details>
  <summary>와이어프레임 설정</summary>
<img width="828" height="405" alt="image" src="https://github.com/user-attachments/assets/0c111384-8898-4266-94d8-78d3a9e5122e" />
  <br />카드 그리드, 작성 폼, 리스트 뷰 등 주요 화면 흐름을 저 충실도(Lo-Fi) 로 빠르게 시각화
</details><details>
  <summary>작업 내용의 문서화</summary>
<img width="806" height="386" alt="image" src="https://github.com/user-attachments/assets/464859e5-3300-4499-bb11-14a6151dc9f1" />
  <br />회의 결과·액션 아이템을 실시간 기록해 책임 소재·일정 투명성 확보

매일 아침 짧은 회의로 TO-DO 확정 → 작업 착수 지연 Zero
</details><details>
  <summary>애자일 루프(Plan → Build → Review)</summary>

<img width="534" height="388" alt="image" src="https://github.com/user-attachments/assets/20db8623-6677-48de-9e36-c128822098ee" />
  <br />Sprint, 구현·재고(Refactor), 피드백 반영을 순환 구조로 시각화

“작게 만들고, 빨리 검증” 문화를 강조해 지속적 개선(Continuous Improvement) 정착
</details>



##  5. 시연  

<details>
  <summary>메인페이지</summary>

  <img width="950" height="745" alt="image" src="https://github.com/user-attachments/assets/a32f4919-e158-4898-af4d-df26ce00af44" />
  HelloPet 메인페이지 입니다.
  
  <br />네비게이션에서 입양게시판, 자유게시판, 로그인 기능을 이용할 수 있습니다.
  
</details>


<details>
  <summary>로그인 페이지</summary>

  <img width="491" height="418" alt="image" src="https://github.com/user-attachments/assets/14674346-fed5-4ce4-ae93-8df0d002252c" />
  <br />로그인이 가능합니다.
  <br />회원가입 페이지로 이동할 수 있습니다.
</details>

<details>
  <summary>회원가입 페이지</summary>

  <img width="435" height="804" alt="image" src="https://github.com/user-attachments/assets/1f37c905-94ea-4ccb-a316-388233d65860" />
  <br />유저의 정보에 따라 HelloPet 회원가입을 할 수 있습니다.
  <br />유저, 보호소, 관리자의 역할을 선택할 수 있습니다. 
  <br />정규식에 따라서 가입버튼이 활성화 됩니다. 
</details>

<details>
  <summary>입양게시판</summary>

  <img width="941" height="836" alt="image" src="https://github.com/user-attachments/assets/26588b7d-51d9-430c-a19d-c0ecfe5d8188" />
  <br />유기동물 리스트를 조회할 수 있습니다.
  <br />동물의 이름, 입양 상태, 등록일, 보호소 등을 확인할 수 있으면 클릭 시 상세정보로 이동합니다.
  <br />페이지네이션이 구현되어있습니다. 
</details>

<details>
  <summary>입양 상세 정보 페이지</summary>

  <img width="500" height="847" alt="image" src="https://github.com/user-attachments/assets/9f671409-2f62-4fe2-adff-22663cdaa942" />
  <br />유기동물 리스트 보다 상세한 정보를 확인할 수 있습니다.
  <br />입양 신청 하기 및 입양게시판으로 돌아가는 버튼이 활성화 되어있습니다.
</details>

<details>
  <summary>입양신청서</summary>

  <img width="461" height="848" alt="image" src="https://github.com/user-attachments/assets/7880a232-dadf-4756-a778-d91f4507ca4a" />
   <img width="455" height="391" alt="image" src="https://github.com/user-attachments/assets/34d4da78-884c-4090-a912-a08e40c041ee" />
  <br />원하는 동물로 입양을 신청할 수 있습니다.
  <br />유저의 정보에 따라 폼을 작성합니다.
</details>

<details>
  <summary>자유게시판</summary>

  <img width="940" height="847" alt="image" src="https://github.com/user-attachments/assets/85464aa6-bbeb-4b35-b2cd-a7e4649bd443" />
  <br />유저들이 자율적으로 글을 쓸 수 있는 게시판입니다.
  <br />전체, 커뮤니티, Q&A 카테고리 설정이 가능해 원하는 게시판으로 이동할 수 있습니다.
  <br />검색, 정렬, 새 글쓰기가 가능합니다.
  <br />페이지네이션이 구현되어있습니다.
</details>

<details>
  <summary>게시물 상세</summary>

  <img width="802" height="815" alt="image" src="https://github.com/user-attachments/assets/7ec467f5-3903-4c1a-b7f6-06aa1f6c08ab" />
  <br />지정했던 카테고리로 글을 조회할 수 있습니다.
  <br />조회 시 조회 수, 날짜, 유저닉네임을 조회할 수 있습니다.
  <br />게시글 제목, 내용, 사진을 조회할 수 있으며 다른 유저들의 댓글을 확인할 수 있습니다.

</details>

<details>
  <summary>마이페이지</summary>

  <img width="911" height="575" alt="image" src="https://github.com/user-attachments/assets/e7f646aa-6984-406a-8745-8e282eb335cf" />
 <br />개인정보수정, 내가 쓴 게시글, 내가 쓴 댓글 버튼으로 이동이 가능합니다.
 <br />유저의 역할에 따라 입양신청내역, 내가 쓴 입양공고, 유저리스트로 버튼이 활성화 됩니다.
 <br />각각의 유저의 역할에 맞는 작업을 진행할 수 있습니다.
</details>

## 6. 테스트  

* **Postman**으로 단위/통합 API 테스트 진행.&#x20;
* FE·BE 통합 후 **E2E 시나리오** 확인 및 회귀 테스트.&#x20;

## 7. 성능 최적화 

| # | 최적화 대상                  | 직면한 문제                                                  | 핵심 솔루션                                                                                                         | Before                    | After                     | 달성 효과                                     |
| - | ----------------------- | ------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- | ------------------------- | ------------------------- | ----------------------------------------- |
| 1 | **실시간 접속자 조회 캐싱**       | 로그인 사용자 수(Hot Data)를 요청마다 RDB에서 조회 → TPS 증가 시 DB I/O 병목 | `ConcurrentHashMap<userId, UserDTO>` + `DelayQueue` TTL(5 min) 캐시<br>– 캐시 Hit 시 즉시 응답, Miss 일 때만 DB 조회 후 캐시 갱신 | 18 ms(평균 응답)              | **1 ms**                  | DB QPS 90 %↓, API P95 Latency ≈ 3 ms      |
| 2 | **Landing Page SSR 전환** | CSR 초기 로딩 공백으로 FCP 지연, SEO 크롤러 인덱싱 실패                   | Next.js `getServerSideProps`로 첫 페이지만 SSR → 하위 페이지는 CSR 유지<br>+ 60 s Edge Cache로 오버헤드 최소화                       | 17 ms(서버 렌더링) / 1.8 s FCP | **15 ms** / **1.2 s FCP** | Bounce Rate 42 %→25 % , Page Visit Rate ↑ |
| 3 | **입양공고 N+1 제거**         | 리스트 1페이지(≒ 37 행) 요청당 37 + 1 SQL 실행                      | QueryDSL DTO Projection(`select new …`)으로 필요한 컬럼만 Join 1회 조회                                                   | 37 SQL                    | **1 SQL**                 | 응답 120 ms→68 ms, DB CPU 30 %↓             |
| 4 | **대량 엔티티 수정 최적화**       | 필드 변경마다 엔티티 영속 → dirty checking → 트래픽 피크 시 메모리 사용 증가    | JPQL `update …` + `@Modifying` 즉시 반영, 1쿼리식 배치                                                                  | 37 Entity Load            | **1 SQL Update**          | Heap Usage ≈ -40 %, 처리량 20 %↑             |


## 8. 로드맵  

* 보호소 ↔ 입양자 **실시간 채팅**
* **유기견 봉사활동** 매칭
* 반려견 **중고 용품 마켓**
* **위탁/임시보호** 기능
* **외부 OAuth** 인증/인가 연동&#x20;

## 9. 팀 

| 역할                    | 이름      | 담당                          |
| --------------------- | ------- | --------------------------- |
| **PM / Auth**, 사용자 관리 | **유경우** | 회원 CRUD, 보안, 인증·인가, 프로젝트 관리 |
| 입양 신청                 | **지민주** | 신청 로직, 승인                   |
| 입양 등록                 | **박우정** | 동물 공고, 상태 관리                |
| 자유 게시판                | **이미래** | 커뮤니티 모듈                     |

