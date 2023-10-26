## 오버로딩(Overloading)
- 오버로딩은 자바의 한 클래스 내에 `같은이름`의 메서드나 생성자가 있더라도, `매개변수의 유형`,`개수`,`순서`가 다르다면 같은 이름을 사용해서 정의할 수 있음을 의미한다.
- 따라서 오버로딩을 통해 동일한 이름으로 다양한 동작을 수행할 수 있다.
- *주의 : 리턴값 유형은 오버로딩시 고려되지 않는다. 즉, 오버로딩의 조건은 메서드의 이름이 같고, 매개변수의 타입이나 개수가 달라야한다. 리턴값만 다른경우 오버로딩 할 수 없다.
```java
public class OverloadingTest {
    public int add(int a, int b) {
        return a + b;
    }

    public double add(double a, double b) {
        return a + b;
    }

    public int add(int a, int b, int c) {
        return a + b + c;
    }
}

public class Main {
    public static void main(String[] args) {
        Calculator calculator = new Calculator();
        System.out.println(OverloadingTest.add(5, 7));          // int add
        System.out.println(OverloadingTest.add(3.5, 2.2));     // double add
        System.out.println(OverloadingTest.add(2, 3, 4));      // int add
    }
}
```
```text
// 출력결과
12
5.7
9
```

## 오버라이딩(Overriding)
- 오버라이딩은 상속 관계에서 `부모 클래스에 정의된 메서드를 자식 클래스에서 재정의하는 것`을 의미한다.
- 부모 클래스의 메서드를 재정의 하는 것이므로, 자식 클래스에서는 오버라이딩 하고자 하는 메서드의 이름, 매개변수, 리턴값이 모두 같아야한다.

```java
class Shape {
    public void draw() {
        System.out.println("Drawing a shape");
    }
}

class Circle extends Shape {
    @Override
    public void draw() {
        System.out.println("Drawing a circle");
    }
}

public class Main {
    public static void main(String[] args) {
        Shape shape = new Circle();
        shape.draw();
    }
}
```
```text
// 출력결과
Drawing a circle
```

## 정리
- 오버라이딩 : 상속 받은 메소드를 재정의 하는 것
- 오버로딩 : 이름만 같은 새로운 메서드를 생성하는 것

|            | Overriding                            | Overloading                          |
|------------|--------------------------------------|-------------------------------------|
| 접근 제어자 | 자식 클래스에서 부모 클래스 메소드의 접근 제어자를 확장 가능 | 모든 접근 제어자를 사용 가능 |
| 리턴형     | 동일해야 함                             | 다를 수 있음 |
| 메소드명   | 동일해야 함                             | 동일해야 함 |
| 매개변수   | 동일해야 함                             | 달라야 함 |
| 적용 범위 | 상속 관계에서 적용됨                 | 같은 클래스 내에서 적용됨 |
