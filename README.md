<div align="center">

# 👋 안녕하세요! 백엔드 개발자 남준구입니다.

**안정적이고 확장 가능한 시스템을 설계하고, 사용자 경험을 개선하는 것에 집중하는 개발자입니다.**

</div>

---

## 👨‍💻 About Me

- 🔐 **인증/인가 시스템 구축** — Spring Security, JWT, OAuth2를 활용한 보안 시스템 설계
- 🤖 **AI/ML 파이프라인 구축** — RAG 기반 문서 검색, 벡터 DB, 실시간 로그 분석
- 📊 **대용량 데이터 처리** — Redis Streams, Batch Insert, 파티셔닝으로 처리 성능 10배 향상
- 🛠 **시스템 안정성 확보** — Circuit Breaker, DLQ, 적응형 Backpressure로 장애 전파 차단
- 🎨 **설계 패턴 활용** — Strategy Pattern으로 확장 가능한 아키텍처 설계
- 💬 **협업과 코드 품질** — 코드 리뷰, 트러블슈팅 문서화, 팀 컨벤션 준수

---

## 🛠 Tech Stack

### Backend & Framework
![Java](https://img.shields.io/badge/Java%2017-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![Spring Security](https://img.shields.io/badge/Spring%20Security-6DB33F?style=flat-square&logo=springsecurity&logoColor=white)
![JPA](https://img.shields.io/badge/Spring%20Data%20JPA-6DB33F?style=flat-square&logo=spring&logoColor=white)
![QueryDSL](https://img.shields.io/badge/QueryDSL-0769AD?style=flat-square)
![C#](https://img.shields.io/badge/C%23-239120?style=flat-square&logo=csharp&logoColor=white)

### Database & Cache
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)
![Redis Streams](https://img.shields.io/badge/Redis%20Streams-DC382D?style=flat-square&logo=redis&logoColor=white)

### AI & ML
![OpenAI](https://img.shields.io/badge/OpenAI%20GPT--4-412991?style=flat-square&logo=openai&logoColor=white)
![Gemini](https://img.shields.io/badge/Google%20Gemini-4285F4?style=flat-square&logo=googlegemini&logoColor=white)

### Game Development
![Unity](https://img.shields.io/badge/Unity-000000?style=flat-square&logo=unity&logoColor=white)

### DevOps & Tools
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonaws&logoColor=white)
![Render](https://img.shields.io/badge/Render-46E3B7?style=flat-square&logo=render&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=github-actions&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white)

---

## 📌 주요 프로젝트

### 🤖 [DocuMind - AI 기반 로그 분석 & 문서 검색 플랫폼](https://github.com/jk-Nam/Documind) (팀 프로젝트)

게임 서비스의 오류 로그를 실시간으로 수집·분석하고, AI가 이슈를 분류하고 패치노트까지 자동 생성하는 품질 관리 코파일럿

> **담당 도메인**: logprocessor, issue

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

#### 🛠 기술 스택
- **Backend**: Spring Boot, Spring Security, JPA, QueryDSL
- **Design Pattern**: Strategy Pattern (심각도 평가 알고리즘 분리)
- **AI/ML**: OpenAI GPT-4, Google Gemini (팀원 구현)
- **Database**: PostgreSQL (pg_bigm, 주별 파티셔닝), Redis (Streams, HyperLogLog)
- **Infrastructure**: Docker, AWS S3, Parquet, Resilience4j, Prometheus, Grafana

#### 📊 성과
- Redis Streams 피크 시 PEL 크기: **10,000+ → 100 이하** 개선
- Batch Insert: 단건 대비 **10배 이상 처리 속도 향상**
- SHA-256 핑거프린트: 이슈 중복 **완벽 방지**
- 전략 패턴: **확장 가능한 심각도 평가 시스템** 구축 (신규 전략 추가 시 기존 코드 수정 불필요)

#### 🐛 주요 트러블슈팅
- **로그 TTL 정책 수립과 스토리지 Tier 결정**
  - 파티션 단위(일별/주별/월별) 비교 분석 후 주별 파티셔닝 선택
  - 3-Tier 스토리지 정책 수립 (게임 패치 주기와 일치)

- **FrequencyStrategy 장기 지속 이슈 계산 범위 제한**
  - Redis TTL(7일)과 PostgreSQL 영구 저장소 간 생명주기 불일치 해결
  - 계산 범위를 최근 7일로 제한하여 정합성 보장

---

### 🛒 [얼마고 - 중고 물품 경매 플랫폼](https://github.com/jk-Nam/eolmago)

실시간 경매와 안전한 거래를 제공하는 중고 물품 플랫폼 (팀 프로젝트)

#### 🎯 주요 구현
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

#### 🛠 기술 스택
- **Backend**: Spring Boot, Spring Security, JPA, QueryDSL
- **Authentication**: JWT, OAuth2, CoolSMS
- **Database**: PostgreSQL, Redis
- **Storage**: Supabase Storage

#### 🐛 주요 트러블슈팅
- **로그인 세션 이탈 문제**: Thymeleaf 렌더링 실패 시 쿠키 손실 → SecurityContext 갱신 로직 개선
- **프로필 이미지 캐싱 문제**: 브라우저 캐시로 인한 미반영 → 타임스탬프 쿼리 파라미터 적용
- **보안 취약점 11건 수정**: AI 코드 리뷰(Greptile) 기반 인증 우회, 쿠키 보안, null 체크 등 개선

---

<div align="center">

### 💬 Contact

궁금한 점이 있으시다면 언제든 연락주세요!

[![Email](https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:skawnsrn94@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/jk-Nam)

</div>
