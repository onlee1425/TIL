## final,finally,finalize

### final (키워드):

> **final**은 자바 프로그래밍 언어에서 키워드로 사용된다. 이를 변수, 메서드 또는 클래스 앞에 붙이면 해당 요소를 변경할 수 없게 만든다.
- **변수** 에서 final을 사용하면 **변수에 할당된 값을 변경할 수 없으며, 상수로 간주된다**.
- **메서드** 에서 final을 사용하면 **하위 클래스에서 해당 메서드를 오버라이드할 수 없다**.
- **클래스** 에서 final을 사용하면 **해당 클래스를 상속할 수 없다**.

예:
```java
final int x = 10; // x는 변경할 수 없는 상수이다.

class Parent {
final void display() {
// 이 메서드를 하위 클래스에서 오버라이드할 수 없다.
}
}
```


### finally (블록):

> **finally**는 자바의 예외 처리 구문인 try-catch-finally 블록에서 사용된다. finally 블록은 **예외가 발생하든 발생하지 않든 항상 실행**된다.
finally 블록은 리소스 정리 또는 마무리 작업을 수행하기 위해 유용하게 사용된다.


예:
```java
try {
// 예외가 발생할 수 있는 코드
} catch (Exception e) {
// 예외 처리 코드
} finally {
// 항상 실행되는 블록, 리소스 정리 등을 수행할 수 있음
}
```


### finalize (메서드):

> **finalize**는 자바의 Object 클래스에 정의된 메서드이다. 이 메서드는 객체가 **가비지 컬렉터에 의해 수거되기 전에 호출**된다. 객체의 마지막 정리 작업을 수행하는 데 사용된다.
하지만 주의해야 하며, Java 9부터는 finalize 메서드의 사용이 권장되지 않고, 대신 AutoCloseable 인터페이스와 try-with-resources 문을 사용하여 리소스 정리를 수행하는 것이 권장된다.


예:
```java
Copy code
class MyClass {
// finalize 메서드 오버라이드
protected void finalize() {
// 객체의 정리 작업 수행
// 주의: 이제는 권장되지 않는 방법
}
}
```

finalize 메서드의 문제 참고 : https://www.itworld.co.kr/news/224419
