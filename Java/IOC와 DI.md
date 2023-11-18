## IOC(Inversion of Control)
- 스프링에서 IOC는 컨테이너(Container)에 제어의 역전을 위임하는 개념이다. 스프링은 빈(Bean)이라 불리는 객체들을 생성, 관리하고, 이들 빈 간의 의존성을 해결하는데 IOC를 활용한다. 
- `제어의 역전` 이라는 의미는 말 그대로 메소드나 객체의 호출작업을 개발자가 결정하는 것이 아닌, 외부에서 결정되는 것을 의미한다.
- IOC를 이용하여 스프링 컨테이너는 애플리케이션의 구성 요소들을 생성하고 관리하여 개발자가 직접 제어하지 않고도 객체의 생명 주기를 관리할 수 있다.

## DI(Dependency Injection)
- DI는 스프링과 타 프레임워크가 차별화 되어 제공하는 기법으로, `의존 관계 주입 기능`이다.
- `의존성 주입`은 객체를 직접 생성하는 것이 아닌 외부에서 생성한 후 주입 시켜주는 방식이다.
- 스프링에서는 주로 다음 세가지의 방법으로 의존성 주입을 할 수 있다.

### 생성자 주입(Constructor Injection)
- 가장 일반적으로 사용되는 방법으로, 빈의 생성자를 통해 의존성을 주입한다. 스프링은 자동으로 빈 간의 의존성을 해결하고, 개발자는 이를 선언적으로 설정할 수 있다.
```java
public class ProductService {
    private final ProductRepository repository;

    public ProductService(ProductRepository repository) {
        this.repository = repository;
    }
}
```

### 세터 주입(Setter Injection)
- setter 메서드를 통해 의존성을 주입하는 방식이다.
```java
public class ProductService {
    private ProductRepository repository;

    public void setRepository(ProductRepository repository) {
        this.repository = repository;
    }
}
```

### 필드 주입(Field Injection)
- 필드를 직접 주입하는 방식이다. 단일 책임(SRP)의 원칙 위반되는 방법으로 권장되지 않는다.
```java
public class ProductService {
    @Autowired
    private ProductRepository repository;
}
```

## IOC와 DI의 장점
- 높은 유연성
  -  IOC와 DI는 코드의 결합도를 낮추어 유연성을 향상시킨다. 또한, 런타임 시 의존성을 동적으로 변경할 수 있어 새로운 기능 추가나 기존 기능 수정이 용이하다.
- 테스트 용이성
  - DI를 통해 의존성을 주입받는 객체를 쉽게 테스트할 수 있다. Mock 객체를 사용하여 각각의 빈을 테스트하는 것이 가능하며, 단위 테스트와 통합 테스트를 쉽게 수행할 수 있다.
- 재사용성 증가
  - IOC와 DI를 활용하면 각각의 빈을 독립적으로 개발하고 유지할 수 있다. 이는 기존의 코드를 더 쉽게 재사용할 수 있도록 도움을 준다.