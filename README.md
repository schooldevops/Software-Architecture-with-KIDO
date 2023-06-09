# Software-Architecture-with-KIDO

- 1. 소프트웨어 설계원칙
  - 1.1 SRP: [단일책임원칙](/01-Software-Design-Principle/software-design-principle.md#srpsingle-responsibility-principle)
  - 1.2 OCP: [개방-폐쇄 원칙](/01-Software-Design-Principle/software-design-principle.md#ocpopen-close-principle)
  - 1.3 LSP: [리스코프 치환원칙](/01-Software-Design-Principle/software-design-principle.md#lspliskov-substitution-principle)
  - 1.4 ISP: [인터페이스 분리 원칙](/01-Software-Design-Principle/software-design-principle.md#ispinterface-segregation-principle)
  - 1.5 DIP: [의존성 역전 원칙](/01-Software-Design-Principle/software-design-principle.md#dipdependency-inversion-principle)

<br/>

- 2. Software Architecture
  - 2.1 Monolithic Architecture
  - 2.2 SOA(Service Oriented Architecture)
  - 2.3 MSA(Micro Service Architecture)
  - 2.4 Domain Driven Architecture
  - 2.4 Port-Adapter Architecture
  - 2.5 Event Driven Architecture
  - 2.6 Shared Data Architecture
  - 2.7 Multi Tier Architecture

- 3. 아키텍처 설계 패턴
  - 3.1 확장성 패턴
    - LoadBalancing Pattern
    - Pipes and Filters Pattern
    - Scatter Gather Pattern
    - Orchestrator pattern
    - Choreography Pattern
  - 3.2 데이터 집약 시스템을 위한 성능패턴
    - MapReduce Pattern
    - Saga Pattern
    - Transactional Outbox pattern
    - Materialized View Pattern
    - CQRS Pattern
    - Event Sorcing Pattern
  - 3.3 소프트웨어 기능확장성 패턴
    - SideCar and Ambassador Pattern
    - Anti-Corruption Adapter Pattern
    - Backends for Frontends Pattern
  - 3.4 신뢰성, 오류처리 및 복구 패턴
    - Throttling and Rate Limiting Pattern
    - Retry Pattern
    - Circuit Breaker Pattern
    - Dead Letter Queue Pattern (DLQ)
  - 3.5 배포 및 프로덕 테스트 패턴
    - Rolling Deploy Pattern
    - Blue-Green Deploy Pattern
    - Canary Release Pattern
    - A/B Test Deploy Pattern

- 4. Event Storming 이해
  - Event Storming 소개
  - Event Storming 예제 이해
