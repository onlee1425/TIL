## DTO, DAO, VO의 차이점

## DTO (Data Transfer Object)
> DTO는 계층 간 데이터 교환을 하기 위해 사용하는 객체로, 데이터를 한 레이어에서 다른 레이어로 전송하는데 사용된다.

- 주로 데이터를 캡슐화하고 필요한 데이터만 전송하도록 돕는 역할을 한다.
- DB로부터 데이터를 얻어 Service나 Controller 등으로 보낼 때 사용한다.
- 비즈니스 로직을 포함하지 않는 순수 데이터 객체(Java Beans)이다.
- 즉, getter/setter 메서드만 가진 클래스를 의미한다.

```java
// user라는 엔티티를 DTO형태로 변환 후 사용한다.
public class UserDTO {
    private String username;
    private String email;

    public UserDTO(String username, String email) {
        this.username = username;
        this.email = email;
    }

    public String getUsername() {
        return username;
    }

    public String getEmail() {
        return email;
    }
}
```

## DAO (Data Access Object)
> DAO는 실제로 DB의 데이터에 접근하기 위한 객체이다.

- DB와 통신하고 데이터를 CRUD 하는데 사용한다.
- Service와 DB를 연결하는 역할을 한다.
- 스프링에서는 Repository 가 DAO에 해당된다.

```java
import org.springframework.data.repository.CrudRepository;

public interface UserRepository extends CrudRepository<User, Long> {
    User findByUsername(String username);
}
```

## VO (Value Object)
> VO는 읽기전용(Read-only) 속성을 가진 값 객체이다.

- getter 메서드만 갖고 있기 때문에 값의 불변성을 유지한다.
- 생성된 여러 VO가 실제로 다른 객체(객체의 주소값이 다른경우)이더라도 값이 같아면 동등한 객체로 판단한다.
  - 같은 값을 가지고 있는지를 판단하는 메서드를 만들거나, equals() 와 hashCode() 함수를 재정의 해야한다.
- VO에는 데이터만 저장되며 비즈니스 로직을 포함하지 않는다.

** VO가 필요한 이유
- primitive(원시값) 타입이 도메인 객체를 모델링하기 위해 충분하지 않기 때문이다.

```java
// 나이는 그 자체로 값을 가져야 하기때문에 primitive로 표현하는 것은 적절하지 않다.
public class AgeVO {
    private int age;

    public AgeVO(int age) {
        this.age = age;
    }

    public int getAge() {
        return age;
    }
}
```