
# HelloPet 🐾
SESAC 7기 B팀이 개발한 **유기동물 입양 서비스 플랫폼**입니다. 반려동물 인구 증가에 따라 높아진 유기동물 문제를 해결하고, 입양 정보 접근성을 향상시키기 위해 만들어졌습니다.
유기동물 자연사·안락사 비율이 증가하는 현황을 해결하고자 합니다. 

## Table of Contents
1. Features  
2. Tech Stack  
3. Architecture & Git Workflow  
4. Getting Started  
5. Tests  
6. Performance Optimizations  
7. Roadmap  
8. Team  
9. License  

---

## 1. Features
| 모듈 | 주요 기능 |
|------|-----------|
| **사용자 관리** | 회원가입(관리자·보호소·입양자), 프로필 수정(닉네임·비밀번호·주소·이미지), 계정 비활성화 기능 제공 |
| **입양 동물 등록** | 보호소가 동물 정보(품종·나이·건강·사진 등) 등록, 상태 변경(보호중 ↔ 입양완료), 공고 삭제 |
| **입양 신청 관리** | 입양자가 신청서 작성·조회, 보호소가 공고별 신청서 승인/상태 관리, 신청서 삭제 |
| **자유 게시판** | Q&A/커뮤니티 글·댓글 CRUD, 페이지네이션·카테고리·정렬 지원, 마이페이지 글/댓글 관리 |  

## 2. demonstration

<details>
  <summary>🖼️ Screenshot 1</summary>

  <img width="950" height="745" alt="image" src="https://github.com/user-attachments/assets/a32f4919-e158-4898-af4d-df26ce00af44" />

</details>

<details>
  <summary>🖼️ Screenshot 2</summary>

  <img width="491" height="418" alt="image" src="https://github.com/user-attachments/assets/14674346-fed5-4ce4-ae93-8df0d002252c" />

</details>

<details>
  <summary>🖼️ Screenshot 3</summary>

  <img width="435" height="804" alt="image" src="https://github.com/user-attachments/assets/1f37c905-94ea-4ccb-a316-388233d65860" />

</details>

<details>
  <summary>🖼️ Screenshot 4</summary>

  <img width="941" height="836" alt="image" src="https://github.com/user-attachments/assets/26588b7d-51d9-430c-a19d-c0ecfe5d8188" />

</details>

<details>
  <summary>🖼️ Screenshot 5</summary>

  <img width="500" height="847" alt="image" src="https://github.com/user-attachments/assets/9f671409-2f62-4fe2-adff-22663cdaa942" />

</details>

<details>
  <summary>🖼️ Screenshot 6</summary>

  <img width="461" height="848" alt="image" src="https://github.com/user-attachments/assets/7880a232-dadf-4756-a778-d91f4507ca4a" />

</details>

<details>
  <summary>🖼️ Screenshot 7</summary>

  <img width="455" height="391" alt="image" src="https://github.com/user-attachments/assets/34d4da78-884c-4090-a912-a08e40c041ee" />

</details>

<details>
  <summary>🖼️ Screenshot 8</summary>

  <img width="940" height="847" alt="image" src="https://github.com/user-attachments/assets/85464aa6-bbeb-4b35-b2cd-a7e4649bd443" />

</details>

<details>
  <summary>🖼️ Screenshot 9</summary>

  <img width="802" height="815" alt="image" src="https://github.com/user-attachments/assets/7ec467f5-3903-4c1a-b7f6-06aa1f6c08ab" />

</details>

<details>
  <summary>🖼️ Screenshot 10</summary>

  <img width="911" height="575" alt="image" src="https://github.com/user-attachments/assets/e7f646aa-6984-406a-8745-8e282eb335cf" />

</details>



## 2. Tech Stack
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

## 프로젝트 구조
## 개발 워크 플로우(브랜치 전략 칸반 했던거)
## 코드 컨벤션

## 3. Architecture & Git Workflow
- **GitHub Flow** 전략: 기능 단위 브랜치 → PR → main 병합.  
- 칸반 보드와 브랜치/커밋 ID 연동으로 추적성 확보.

## 4. Getting Started
### 1) Backend
cd backend
./mvnw clean package
docker compose up -d  # PostgreSQL + API

### 2) Frontend
cd ../frontend
pnpm install
pnpm dev

## 5. Tests

* **Postman**으로 단위/통합 API 테스트 진행.&#x20;
* FE·BE 통합 후 **E2E 시나리오** 확인 및 회귀 테스트.&#x20;

## 6. Performance Optimizations

| 개선 항목                                      | Before | After      |
| ------------------------------------------ | ------ | ---------- |
| 실시간 접속자 조회: DB → In‑Memory Map + TTL Queue | 18 ms  | **1 ms**   |
| 게시판 첫 페이지 SSR 전환 (SEO & FCP)               | 17 ms  | **15 ms**  |
| 입양공고 N+1 문제 → DTO Projection               | 37 SQL | **1 SQL**  |

## 7. Roadmap

* 보호소 ↔ 입양자 **실시간 채팅**
* **유기견 봉사활동** 매칭
* 반려견 **중고 용품 마켓**
* **위탁/임시보호** 기능
* **외부 OAuth** 인증/인가 연동&#x20;

## 8. Team

| 역할            | 이름      | 담당             |   |
| ------------- | ------- | -------------- | - |
| **PM / Auth**, 사용자 관리        | **유경우** | 회원 CRUD, 보안, 인증·인가, 프로젝트 관리    |   |
| 입양 신청         | **지민주** | 신청 로직, 승인      |   |
| 입양 등록         | **박우정** | 동물 공고, 상태 관리   |   |
| 자유 게시판        | **이미래** | 커뮤니티 모듈        |   |
