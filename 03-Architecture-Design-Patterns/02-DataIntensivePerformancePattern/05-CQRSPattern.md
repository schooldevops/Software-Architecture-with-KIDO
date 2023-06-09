# CQRS Pattern

## 개요 

- CQRS (Command Query Responsibility Segregation) 패턴은 명령과 조회를 분리하는 패턴으로, 데이터의 업데이트와 조회가 서로 다른 모델에서 처리되도록 하는 아키텍처 패턴이다.
- 일반적인 CRUD 기반의 데이터베이스에서는 조회와 업데이트가 하나의 모델에서 동시에 처리된다. 
- 명령 모델(Command Model)은 데이터를 작성, 수정 또는 삭제한다. 이 모델은 일반적으로 쓰기 작업이 더 많고 트랜잭션을 사용하여 데이터 일관성을 유지한다.
- 조회 모델(Query Model)은 데이터를 읽기 위해 사용된다. 이 모델은 일반적으로 데이터를 미리 계산하고 캐시하여 쿼리의 응답 시간을 최적화한다.
- 이렇게 분리하여 성능 및 확장성 과 보안강화 효과를 얻을 수 있다. 

## 배경

- 과거 CRUD 기반 모델은 작은 서비스 개발 및 운영에 크게 무리 없이 수행가능하다. 

![old-model](imgs/command-and-query-responsibility-segregation-cqrs-tradition-crud.png)

image from: https://learn.microsoft.com/en-us/azure/architecture/patterns/cqrs

- 시스템이 복잡하고, 거대해지면서 다음 2가지 부분에서 어려움을 겪게 된다. 
  - 읽기 영역:
    - 읽기 측면에서 어플리케이션은 많은 다른 쿼리들을 수행해야한다. 
    - 또한 읽은 결과를 DTO(Data Transfer Objects) 의 다양한 형태로 제공 될 필요가 있다. 
    - 이때 객체 매핑은 매우 복잡해진다. 
  - 쓰기 영역:
    - 쓰기 영역은 다양하고 복잡한 검증과 비즈니스 로직이 필요로 해진다. 
- 위 2가지 영역에서 하나의 데이터베이스 처리 영역에서 모두 처리한다면, 시스템의 복잡도는 증가하고, 운영유지에 어려움을 겪게 된다. 

![cqrs](imgs/command-and-query-responsibility-segregation-cqrs-basic.png)

- 즉, 읽기 쓰기 영역은 종종 서로 비대칭 적이며, 서로다른 성능과 확장성을 요구하게 되므로 이 두 영역을 분리관리하는 방안이 고려된 결과이다. 
- 커맨드는 데이터 중심이 아닌 태스크 기반으로 작성된다. 또한 동기식이 아닌 비동기 방식으로 처리할 수 있다. 
- 쿼리는 데이터베이스를 절대 변경하지 않는다. 

### 쓰기/읽기 데이터 동기화 및 읽기 성능 강화 

![cqrs-integrate](imgs/command-and-query-responsibility-segregation-cqrs-separate-stores.png)

- 읽기는 쓰기보다 더 많은 트래픽을 가질 수 있다. 위 그림과 같이 쓰기와 읽기 데이터 영역을 물리적으로 분리하여 읽기 성능을 극대화 하기 위한 다양한 방안을 사용할 수 있다. 
  - MaterializedView 이용한 성능 강화 
  - 읽기 저장소의 수평 클러스터링 (멀티 복제) 를 통한 읽기 성능 향상 
- 쓰기 이벤트가 발생하면, 변경 사항에 대한 동기화를 읽기 저장소로 수행하여 동기화를 수행한다. 
- 이벤트 소싱 등을 통해 쓰기에 수행된 데이터를 읽기로 동기화 하는 방법도 있음 

![cqrs](imgs/cqrs.webp)

image form : https://medium.com/design-microservices-architecture-with-patterns/event-sourcing-pattern-in-microservices-architectures-e72bf0fc9274
## 베스트 프랙티스 

- Command 모델과 Query 모델을 명확하게 분리
- 각각의 모델은 최적화된 데이터 구조를 사용하여 처리
- Command와 Query의 데이터 소스는 분리하여 사용
- 업데이트와 조회가 각각의 트랜잭션으로 분리될 수 있도록 구현
- Query 결과를 캐싱하여 성능을 개선

## 장점/단점

- 장점 
  - 명령 모델과 조회 모델의 분리로 인해 서로 독립적으로 확장 가능하다.
  - 쓰기 작업과 읽기 작업을 분리하여 각 작업에 대한 최적화가 가능하다.
  - 캐싱 및 성능 최적화가 용이하다.
  - 높은 확장성과 유연성을 제공한다.
  - 읽기/쓰기 각 작업을 개발하는 팀을 분리하여 개발이 가능하다. 
- 단점
  - 쓰기데이터와 읽기 데이터사이의 동기화가 쉽지 않다. 
  - 시스템이 복잡하다. 즉, 간단한 시스템에 사용하는 것은 좋지 않다.

## WrapUp

- CQRS는 쓰기와 읽기를 각각 분리하여 저장하고, 각각의 영역에 맞게 구성하는 패턴이다. 
- 쓰기와 읽기는 서로 비대칭인 경우가 많으며, 이런 경우는 대개 시스템 규모가 크고 복잡한 경우이므로 사용을 고려해 볼 수 있다. 
- 간단한 시스템에 사용하지 않는것이 좋다. 
- 이벤트 소싱과 함께 사용되는 구조도 고려될 수 있다. 

- 참고:
  - https://learn.microsoft.com/en-us/azure/architecture/patterns/cqrs
  - https://medium.com/design-microservices-architecture-with-patterns/event-sourcing-pattern-in-microservices-architectures-e72bf0fc9274