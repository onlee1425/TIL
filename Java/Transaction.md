## 트랜잭션(Transaction)

트랜잭션(Transaction)은 데이터베이스 또는 다른 데이터 저장 및 처리 시스템에서 수행되는 작업의 단위를 나타낸다. 트랜잭션을 통해 서비스에서 데이터를 처리하는 과정에서 데이터의 일관성을 유지하고, 오류등의 다양한 상황에서 안정성을 확보할 수 있다. 

## 트랜잭션 ACID

1. **원자성 (Atomicity):** 트랜잭션의 가장 중요한 특징으로, 모든 작업은 완전히 성공하거나 실패로 처리해야 한다.

2. **일관성 (Consistency):** 트랜잭션이 실행 전과 후에 데이터베이스는 일관된 상태여야 한다. 즉 트랜잭션은 데이터베이스의 무결성을 유지해야 한다.

3. **독립성 (Isolation):** 동시에 여러 트랜잭션이 실행 중일 때, 각 트랜잭션은 다른 트랜잭션의 작업을 볼 수 없고, 서로 간섭하지 않아야 한다. 이로 인해 데이터베이스의 일관성이 유지된다.

4. **영속성 (Durability):** 트랜잭션이 성공적으로 커밋되면 그 결과는 영구적으로 저장되어야 한다. 시스템 장애 또는 비정상 종료에도 데이터는 유지되어야 한다.

## Spring에서의 트랜잭션 관리 방법

스프링은 트랜잭션 관리를 더욱 쉽게 만들어주는 다양한 방법을 제공한다.
### **선언적 트랜잭션 관리 (Declarative Transaction Management)**
- 스프링에서 제공하는 가장 일반적인 방법 중 하나이다. `@Transactional` 어노테이션을 사용하여 트랜잭션을 선언하고, XML 또는 Java 기반 설정으로 활성화할 수 있다. 이를 통해 개발자는 코드에서 트랜잭션 관리 로직을 분리할 수 있다.
    - @Transactional 의 동작 구조 : 스프링의 트랜잭션 AOP는 @Transactional을 인식하여 트랜잭션 프록시를 적용한다.
      프록시는 '대리인'이라는 뜻으로 Aspect와 @Transactional을 적용한 클래스 또는 메서드인 Target을 연결해주는 역할을 한다.
      1. Client의 API 호출
      2. 프록시 실행
      3. 트랜잭션 코드 실행
      4. 비즈니스 로직 실행
      5. 트랜잭션 코드 실행 (commit / rollback)
      ![Additional Image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FUBhml%2FbtrBrq3S6HP%2FQ3DK0X4Zwo39cKh7IKWeGk%2Fimg.png)

      <br>
      
### **프로그래밍 방식 트랜잭션 관리 (Programmatic Transaction Management)**
- 개발자가 직접 트랜잭션을 시작, 커밋 및 롤백하는 방식이다. `PlatformTransactionManager` 인터페이스를 사용하여 트랜잭션을 제어한다.

## Spring 트랜잭션 속성

| 속성                | 설명                                                                   |
|---------------------|----------------------------------------------------------------------|
| propagation         | 이미 트랜잭션이 진행중일 때 추가 트랜잭션 진행을 어떻게 할지 결정하는 전파 행위에 관한 속성                                            |
| isolation           | 트랜잭션 격리 레벨에 관한 속성으로 기본값은 Default 레벨이며, 실제 사용하는 데이터베이스(JDBC) 등의 기본값을 따른다 |
| readOnly            | 트랜잭션을 읽기 전용으로 지정하는 속성이다. 최적화 관점에서 지원되는 프로퍼티이므로 현재 트랜잭션 상태에 따라 다르게 동작할 수 있다 |
| timeout             | 트랜잭션의 타임아웃(초 단위)을 지정하는 속성으로 지정하지 않을 경우 사용하는 트랜잭션 시스템의 타임아웃을 따른다      |
| rollbackFor         | Checked 예외 발생 시에 롤백을 수행할 예외를 지정하는 속성                                 |
| rollbackForClassName| rollbackFor와 동일하지만 문자열로 클래스명을 지정하는 속성                                |
| noRollbackFor       | Spring의 트랜잭션은 기본적으로 Runtime 예외만 롤백 처리를 수행하지만, Runtime 예외 중 특정 예외는 롤백을 수행하지 않아야 할 경우 사용하는 속성 |
| noRollbackForClassName| noRollbackFor와 동일하지만 문자열로 클래스명을 지정하는 속성                              |