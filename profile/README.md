# SPARTA Logistics ( team. 꾸럭2 )

> **"MSA 기반 B2B 물류 플랫폼을 설계하며, 서비스 간 신뢰성과 데이터 일관성을 끝까지 고민한 팀입니다."**

---

### 프로젝트 상세

아키텍처 설계, 핵심 비즈니스 로직, 트러블슈팅 과정은 아래에서 확인하실 수 있습니다.

👉 **[SPARTA Logistics 발표 자료 바로가기](https://github.com/B2B-team2/.github/blob/main/README.md)**

---

### 기술적 도전

**SPARTA Logistics** 프로젝트를 통해 다음과 같은 문제들을 해결했습니다:

- **MSA 설계**: Spring Cloud(Eureka, Gateway, FeignClient) 기반 마이크로서비스 아키텍처
- **분산 트랜잭션**: Saga 오케스트레이션 패턴으로 주문 → 재고 예약 → 배송 생성 일관성 확보
- **보안**: Keycloak + JWT 인증, Gateway Secret 헤더 기반 직접 접근 차단
- **성능**: Redis Cache-Aside 전략을 통한 허브·경로 정보 캐싱, 낙관적 락 기반 재고 동시성 제어
- **AI 연동**: Google Gemini API를 활용한 최적 발송 시한 자동 산출 및 Slack 알림

### 팀원

- **Leader**: 도경민 (Order Service)
- **Members**:
    - **노동완**: Operations Service, Company Service
    - **김민우**: Delivery Service, Operations Service (AI/Slack)
    - **서동원**: User Service
    - **이선진**: Hub Service

### 기술 스택

- **Language & Framework**: Java 17, Spring Boot 3.3.5, Spring Security, Spring Data JPA
- **MSA**: Spring Cloud Gateway, Netflix Eureka, OpenFeign
- **Auth**: Keycloak, JWT
- **Database**: PostgreSQL, PostGIS, Redis
- **Message**: Apache Kafka
- **DevOps**: Docker, Docker Compose, Vultr, GitHub Actions
- **Monitoring**: Zipkin
- **AI/알림**: Google Gemini API, Slack Webhook

---

### 주요 설계 결정

- 인프라(`docker-compose.infra.yml`)와 앱 서비스(`docker-compose.yml`)를 분리하여 배포 시 DB 데이터 안전성 확보
- 모든 엔티티 Soft Delete 처리(`deleted_at`, `deleted_by`)로 데이터 추적성 유지
- Gateway Secret 헤더 검증으로 마이크로서비스 직접 접근 차단
