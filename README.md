<div align="center">

# 백엔드를 기반으로 풀스택 개발자로 성장하고 있는 남준구입니다.

비즈니스를 이해하고 기술로 문제를 해결하는 개발자입니다.
경영학을 전공했고 IT 업계 경험을 바탕으로 사용자와 비즈니스 가치를 함께 고민합니다.

현재는 Spring 기반 백엔드 개발 경험을 바탕으로 React와 TypeScript를 학습하며 프론트엔드 역량을 확장하고 있습니다.

</div>

---

##  About Me

- 경영학을 전공하고 IT 회사에서 근무하며 비즈니스 관점을 갖춘 개발자로 성장했습니다
- 기술과 비즈니스를 연결하여 실질적인 가치를 만드는 것에 관심이 많습니다
- 데이터 기반으로 문제를 분석하고, 효율적인 솔루션을 설계합니다
- 다양한 직군과 원활하게 소통하며 협업합니다
- 새로운 기술을 학습하고 적용하는 것을 즐깁니다
- 코드 리뷰와 문서화를 통해 팀의 코드 품질 향상에 기여합니다
- Spring Boot 기반 백엔드 경험을 바탕으로 React와 TypeScript를 학습하며 풀스택 역량을 키우고 있습니다

---

## 🛠 Tech Stack

### Frontend

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)
![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)

### Backend & Framework
![Java](https://img.shields.io/badge/Java%2017-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![Spring Security](https://img.shields.io/badge/Spring%20Security-6DB33F?style=flat-square&logo=springsecurity&logoColor=white)
![JPA](https://img.shields.io/badge/Spring%20Data%20JPA-6DB33F?style=flat-square&logo=spring&logoColor=white)
![QueryDSL](https://img.shields.io/badge/QueryDSL-0769AD?style=flat-square)
![C#](https://img.shields.io/badge/C%23-239120?style=flat-square&logo=csharp&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)

### Database & Cache
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)
![Redis Streams](https://img.shields.io/badge/Redis%20Streams-DC382D?style=flat-square&logo=redis&logoColor=white)

### DevOps & Tools
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonaws&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![Render](https://img.shields.io/badge/Render-46E3B7?style=flat-square&logo=render&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=github-actions&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white)
![k6](https://img.shields.io/badge/k6-7D64FF?style=flat-square&logo=k6&logoColor=white)

---

## 📌 주요 프로젝트

### <img src="images/documind-logo.png" width="32" height="32"/> [DocuMind - AI 기반 로그 분석 & 문서 검색 플랫폼](https://github.com/jk-Nam/Documind/tree/dev) (팀 프로젝트)

게임 서비스의 오류 로그를 실시간으로 수집·분석하고, 자동 이슈를 분류하고 패치노트까지 자동 생성하는 품질 관리 코파일럿

#### 🎯 내가 구현한 기능

**📡 실시간 로그 수집 파이프라인 (logprocessor 도메인)**
- Redis Streams + Consumer Group 기반 비동기 로그 수집
- JdbcTemplate Batch Insert로 대량 로그 일괄 저장 (단건 대비 **10배 성능 향상**)
- BackpressureManager: DB 응답 시간 기반 적응형 배치 처리 (100~1,000건)
- Circuit Breaker (Resilience4j) + DLQ + 5회 재시도 정책으로 안정성 확보
- 심각도 기반 샘플링 (DEBUG 5% ~ ERROR 100%)
- 3단계 계층형 스토리지 (Hot/Warm/Cold) - 주별 파티셔닝 + S3 Parquet

**🔍 자동 이슈 분류 & 심각도 평가 (issue 도메인)**
- SHA-256 핑거프린트 기반 이슈 그룹핑 (중복 완벽 방지)
- **전략 패턴(Strategy Pattern)** 기반 심각도 스코어링 (0~100점)
  - 5개의 독립적인 전략 클래스로 평가 로직 분리 (OCP 원칙)
  - FrequencyStrategy, UserImpactStrategy, BusinessImpactStrategy, BlockingLevelStrategy, CrashTypeStrategy
- Redis HyperLogLog로 영향받은 고유 사용자 수 추정
- 이슈 생명주기 관리 + JPA Auditing 기반 변경 이력 추적
- 멘션 기능 + SSE 실시간 알림 (Spring Events)

### 🏛️ Architecture Decisions & Technical Trade-offs

#### 1. 메시징 브로커 선정: Kafka vs Redis Streams
- **Context:** 대규모 로그 수집 파이프라인 구축 시 대용량 분산 환경의 표준인 Apache Kafka 도입을 검토했습니다.
- **Trade-off Analysis:** 
  - **Kafka 검토:** 실무 표준 아키텍처로 확장성이 뛰어나나, 학습 곡선과 인프라 구축 오버헤드 및 개발 기간의 제한을 고려했습니다.
  - **Redis Streams 선택:** 팀원의 낮은 학습 곡선, 별도의 무거운 인프라 구성 없이 Consumer Group 기반 비동기 메시징 처리가 가능합니다.
- **Decision:** 서비스 런칭 전 MVP 구현 목적과 개발 속도를 최우선으로 고려하여 Redis Streams를 채택했습니다. 결과적으로 불필요한 인프라 복잡도를 낮추면서도 PEL 관리를 통해 안정적으로 부하를 제어했습니다.

#### 2. 대량 로그 저장을 위한 Batch Insert 선제적 도입
- **Context:** 대규모 로그 수집 특성상 단건 INSERT 방식은 지속적인 DB Connection 생성과 Network I/O 오버헤드로 병목을 유발합니다.
- **Trade-off Analysis:** 시스템 초기 설계 단계부터 성능 최적화를 최우선 목표로 설정했습니다.
- **Decision:** 단건 저장 대신 `JdbcTemplate Batch Insert`를 적용하여 쿼리 전송 횟수를 대폭 줄이고 I/O 비용을 최소화하도록 구조화했습니다.
- **Result:** DB 쿼리 수 99.8% 감소 및 부하 환경 처리량(RPS) 유의미한 향상 달성.

#### 3. 서버 장애 및 예외 상황 대비를 위한 재시도(Retry) & DLQ 정책
   - **Context:** 로그 처리기(Consumer) 동작 중 일시적인 네트워크 장애나 DB 부하로 인해 메시지 처리에 실패할 경우 데이터 유실이나 무한 루프가 발생할 위험이 존재합니다.
   - **Trade-off Analysis:** 단발성 예외 발생 시 즉시 실패 처리하는 것은 시스템 신뢰성을 떨어뜨리며, 무한 재시도는 시스템 전체의 병목을 가중시킵니다.
   - **Decision:** Resilience4j 기반의 Circuit Breaker를 적용하고, 메시지 처리 실패 시 최대 5회의 재시도(Retry) 정책을 수행하도록 설계했습니다. 5회 초과 실패 시에는 별도의 DLQ(Dead Letter Queue)로 격리하여 시스템의 안정성과 데이터 무결성을 동시에 확보했습니다.
     
#### 4. 스토리지 비용 절감을 위한 계층형 스토리지 (Hot/Warm/Cold) & S3 도입
- **Context:** 모든 로그 데이터를 고성능 RDBMS에 영구 보관하는 것은 인프라 비용 급증과 검색 성능 저하를 초래합니다.
- **Trade-off Analysis:** 데이터의 시간 경과에 따른 조회 빈도 차이에 주목했습니다.
  - **Hot Tier:** 빠른 조회가 필요한 최신 데이터 (PostgreSQL)
  - **Warm Tier:** 주별 파티셔닝 기반 관리 (PostgreSQL)
  - **Cold Tier:** 장기 보관 및 분석용 데이터 (AWS S3 + Parquet)
- **Decision:** RDBMS의 용량 부담과 인프라 유지 비용을 절감하면서 장기 로그 데이터의 보관성을 확보했습니다.

#### 5. 실시간 알림을 위한 SSE (Server-Sent Events) 채널 선택
- **Context:** 이슈 발생 및 멘션 시 사용자에게 실시간 알림을 전달할 통신 프로토콜 선정이 필요했습니다.
- **Trade-off Analysis:**
  - **WebSocket:** 양방향 통신 지원, 핸드셰이크 오버헤드가 크고 복잡함.
  - **SSE:** 단방향(서버→클라이언트) 알림에 특화, HTTP 기반으로 동작하여 서버 리소스 소모가 적음.
- **Decision:** 양방향 소통이 불필요한 단방향 알림 구조에는 WebSocket보다 SSE가 효율적이라 판단하여 채택했습니다.
- **Result:** 불필요한 커넥션 오버헤드 없이 가볍고 안정적인 실시간 알림 체계 구축.

#### 🛠 기술 스택
- **Backend**: Spring Boot, Spring Security, JPA, QueryDSL, Python
- **Design Pattern**: Strategy Pattern (심각도 평가 알고리즘 분리)
- **Database**: PostgreSQL (pg_bigm, 주별 파티셔닝), Redis (Streams, HyperLogLog)
- **Infrastructure**: Docker, AWS S3, Parquet, Resilience4j, Prometheus, Grafana

#### 🛠 AI 연동 & 비정형 데이터 수집 파이프라인
- Python 기반 웹 크롤링: 외부 기술 문서 및 패치노트 수집·정제 파이프라인 구축
- LLM (Prompt Engineering) 기반 산출물 자동화: 수집된 비정형 데이터 및 이슈 로그 기반 API 명세서, 시스템 아키텍처, 패치노트, 매뉴얼 자동 생성
- AI 검증 체계 구축: AI 환각(Hallucination) 방지를 위한 로직 정합성 검증 및 PR 연동 AI 코드 리뷰(Greptile, Qodo) 체계 적용

#### 📊 성과
- Redis Streams 피크 시 PEL 크기: **10,000+ → 100 이하** 개선
- Batch Insert: 단건 대비 **10배 이상 처리 속도 향상**
- SHA-256 핑거프린트: 이슈 중복 **완벽 방지**
- 전략 패턴: **확장 가능한 심각도 평가 시스템** 구축 (신규 전략 추가 시 기존 코드 수정 불필요)
- AI 기반 기술 산출물(API 명세서, 패치노트 등) 자동 생성 파이프라인 구축으로 문서화 오버헤드 대폭 축소
- Python 크롤링 및 LLM 연동을 통해 산재된 비정형 데이터를 정형화된 기술 자산으로 변환

#### 🐛 주요 트러블슈팅
- **로그 TTL 정책 수립과 스토리지 Tier 결정**
  - 파티션 단위(일별/주별/월별) 비교 분석 후 주별 파티셔닝 선택
  - 3-Tier 스토리지 정책 수립 (게임사의 패치 주기 고려)

- **FrequencyStrategy 장기 지속 이슈 계산 범위 제한**
  - Redis TTL(7일)과 PostgreSQL 영구 저장소 간 생명주기 불일치 해결
  - 계산 범위를 최근 7일로 제한하여 정합성 보장

- **로그 처리 성능 병목 해결 (k6 부하 테스트)**
  - 문제: 단건 INSERT로 인한 에러율 31.8%, RPS 100 (목표의 33%)
  - 해결: Batch Insert + Backpressure 구현, constant-arrival-rate 방식으로 정확한 측정
  - 결과: RPS 3배 향상 (100 → 300), 에러율 완전 해소 (31.8% → 0%), p95 latency 690배 개선 (9,997ms → 14ms)
  - DB 쿼리 수 99.8% 감소 (54,000회 → 116회)
---

### <img src="images/eolmago-logo.png" width="32" height="32"/> [얼마고 - 중고 물품 경매 플랫폼](https://github.com/jk-Nam/eolmago) (팀 프로젝트)

실시간 경매와 안전한 거래를 제공하는 중고 물품 플랫폼

#### 🎯 내가 구현한 기능
**인증/인가 시스템**
- Spring Security + OAuth2 소셜 로그인 (Google, Kakao, Naver)
- JWT 기반 토큰 인증 (AccessToken / RefreshToken)
- Redis를 활용한 RefreshToken 저장 및 Rotation
- 환경별 Cookie 보안 설정 (dev: secure=false, prod: secure=true)

**SMS 인증 시스템**
- CoolSMS API 연동
- Redis 기반 인증코드 임시 저장 및 TTL 만료 처리
- SecureRandom을 사용한 암호학적 안전한 인증코드 생성

**유저 관리 & 제재 시스템**
- Supabase Storage 연동 프로필 이미지 업로드
- 캐시 버스팅으로 이미지 실시간 반영
- 사용자 제재 이력 관리 + SecurityContext 실시간 갱신

**관리자 페이지**
- QueryDSL 기반 동적 쿼리 (사용자/신고/제재 이력 필터링)
- @PreAuthorize 기반 ADMIN 권한 검증

### 🏛️ Architecture Decisions & Technical Trade-offs

#### 1. OAuth2 전용 소셜 로그인 채널 채택 (자체 회원가입 미지원)
- **Context:** 사용자 회원가입 및 인증 체계 구축 시 자체 ID/PW 로그인 기능 지원 여부를 검토했습니다.
- **Trade-off Analysis:**
  - **자체 회원가입:** 직접적인 비밀번호 및 개인정보 보관으로 인한 데이터 유출 위험과 관리 오버헤드가 발생합니다.
  - **OAuth2 소셜 로그인:** 사용자 진입 장벽을 낮추는 최신 UX 트렌드이며, 민감 개인정보 직접 보유에 따른 보안 리스크를 외부 인증 제공자(Google, Kakao, Naver)로 이관할 수 있습니다.
- **Decision:** 데이터 보안 리스크 예방과 UX 편의성을 최우선으로 고려하여 자체 회원가입 대신 Spring Security + OAuth2 기반 소셜 로그인 단일 체계를 채택했습니다.

#### 2. 서버 확장성(Scale-out)을 고려한 Stateless 분산 인증 구조 (JWT)
- **Context:** 향후 트래픽 증가에 따른 서버 확장 시 전통적인 Stateful 세션 방식은 서버 간 세션 불일치 문제를 유발합니다.
- **Trade-off Analysis:**
  - **Stateful Session:** 서버 메모리에 세션을 보관하여 무효화가 용이하나, 다중 서버 환경에서 Redis Session Clustering 등 추가적인 인프라 구성이 필요합니다.
  - **Stateless JWT:** 서버에 상태를 저장하지 않아 Scale-out에 용이하지만, 발급된 토큰의 즉시 무효화가 어렵고 탈취 위험이 존재합니다.
- **Decision:** 서버 확장성을 보장하기 위해 Stateless 기반 JWT(AccessToken / RefreshToken) 체계를 채택하고, 탈취 리스크 보완을 위해 RTR(Refresh Token Rotation) 방식을 결합했습니다.

#### 3. Redis 기반 Refresh Token 관리 및 Rotation
- **Context:** JWT 탈취 위험에 대응하고, 만료된 토큰의 자동 정리를 위한 영속성 스토리지 선정이 필요했습니다.
- **Trade-off Analysis:** RDBMS 조회 방식은 토큰 검증 시마다 DB I/O 부담을 유발합니다.
- **Decision:** Redis의 TTL 기능을 활용해 토큰 만료 주기를 자동으로 관리하고, Refresh Token 재발급 시 기존 토큰을 무효화하는 RTR 정책을 구현하여 보안성과 인프라 효율성을 동시에 확보했습니다.

#### 4. 프론트엔드-백엔드 이중 권한 검증 (Defense in Depth)
- **Context:** 페이지 접근 및 주요 기능 수행 시 인가 누수로 인한 무단 접근 위험이 존재했습니다.
- **Trade-off Analysis:** 프론트엔드 단독 검증은 클라이언트 측 스크립트 변조에 취약하며, 백엔드 단독 검증은 불필요한 API 요청을 프론트엔드에서 1차 차단하지 못합니다.
- **Decision:** 프론트엔드(유저 등급/권한별 렌더링 차단)와 백엔드(Spring Security @PreAuthorize 및 Role 기반 검증) 모두에서 이중 인가 검증 체계를 구현하여 보안 수준을 향상시켰습니다.

#### 🛠 기술 스택
- **Backend**: Spring Boot, Spring Security, JPA, QueryDSL
- **Authentication**: JWT, OAuth2, CoolSMS
- **Database**: PostgreSQL, Redis
- **Storage**: Supabase Storage

#### 🐛 주요 트러블슈팅
- **로그인 세션 이탈 문제**: Thymeleaf 렌더링 실패 시 쿠키 손실 → SecurityContext 갱신 로직 개선
- **프로필 이미지 캐싱 문제**: 브라우저 캐시로 인한 미반영 → 타임스탬프 쿼리 파라미터 적용

---

<div align="center">

### 💬 Contact

궁금한 점이 있으시다면 언제든 연락주세요!

[![Email](https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:skawnsrn94@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/jk-Nam)

</div>
