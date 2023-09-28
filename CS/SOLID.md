## SOLID 원칙
> SOLID는 객체 지향 프로그래밍의 5대 기본 원칙으로, SRP(단일 책임 원칙), OCP(개방-폐쇄 원칙), LSP(리스코프 치환 원칙), DIP(의존 역전 원칙), ISP(인터페이스 분리 원칙)의 앞글자를 딴 약어이다.
> 이러한 원칙은 소프트웨어 설계에서 코드의 유연성, 확장성, 유지 보수성을 향상시키는 데 도움을 주며, 더 좋은 소프트웨어 아키텍처를 구축하는 데 도움을 준다.

---
### 단일 책임 원칙(Single Responsibility Principle - SRP)
- 하나의 클래스는 하나의 책임만 가져야 한다. 즉, 클래스는 변경되어야 하는 이유가 하나여야 한다.
- 이를 통해 클래스가 간결하고 논리적으로 분리되며, 변경 시 다른 클래스에 미치는 영향을 최소화 할 수 있다.

**예시**
```java
class Employee {
    String name;
    int employeeId;

    public Employee(String name, int employeeId) {
        this.name = name;
        this.employeeId = employeeId;
    }

    public double calculateSalary(double hoursWorked, double hourlyRate) {
        return hoursWorked * hourlyRate;
    }
    
    public void generateReport() {
        // 보고서 생성 로직
    }
}
```
위의 코드에서 Employee 클래스는 직원의 정보를 관리함과 동히에 급여 계산과, 보고서 생성의 두가지 책임을 갖고있으므로 SRP에 위배된다.

```java
class Employee {
    String name;
    int employeeId;

    public Employee(String name, int employeeId) {
        this.name = name;
        this.employeeId = employeeId;
    }
}

class PayrollSystem {
    public double calculateSalary(Employee employee, double hoursWorked, double hourlyRate) {
        return hoursWorked * hourlyRate;
    }
}

class ReportGenerator {
    public void generateReport(Employee employee) {
        // 보고서 생성 로직
    }
}
```
단일 책임 원칙에 따라 Employee 클래스의 책임을 분리하여 코드를 개선시킬 수 있다. 

---



### 개방-폐쇄 원칙(Open/Closed Principle - OCP)
- 엔티티(클래스,모듈,함수 등) 는 확장에 대해 열려있어야 하고 수정에 대해서는 닫혀 있어야 한다.
- 다형성과 추상화를 활용하여 구현하며, 이를 통해 새로운 기능을 추가할 때 기존 코드를 수정하지 않고 확장할 수 있다.

**예시**
```java
class Rectangle {
    double width;
    double height;
    
    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }
}

class AreaCalculator {
    public double calculateArea(Rectangle rectangle) {
        return rectangle.width * rectangle.height;
    }
}
```
위의 코드에서 AreaCalculator 클래스는 사각형의 넓이를 계산하는 기능만을 제공하며, 다른 도형을 추가하기 위해서는 클래스를 수정해야 한다.

```java
interface Shape {
    double calculateArea();
}

class Rectangle implements Shape {
    double width;
    double height;
    
    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }

    @Override
    public double calculateArea() {
        return width * height;
    }
}

class Circle implements Shape {
    double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    @Override
    public double calculateArea() {
        return Math.PI * radius * radius;
    }
}

class AreaCalculator {
    public double calculateArea(Shape shape) {
        return shape.calculateArea();
    }
}
```
개방-폐쇄 원칙에 따라 Shape 인터페이스를 도입하여 다양한 도형을 나타내는 클래스가 넓이를 계산할 수 있도록 하였고, AreaCalculator 클래스는 Shape 인터페이스를 사용하여 어떤 도형이든 넓이를 계산할 수 있다. 이로써 새로운 도형을 추가할 때 기존 코드를 수정하지 않고도 확장할 수 있다.

---

### 리스코프 치환 원칙(Liskov Substitution Principle - LSP)
- 자식 클래스는 부모 클래스를 대체할 수 있어야 한다. 즉, 상속 관계에서 하위 클래스가 상위 클래스의 모든 기능을 제공해야함을 의미한다.
- 이를 통해 다형성을 지원하고 코드의 안정성을 유지할 수 있다.

**예시**
```java
class Bird {
    void fly() {
        // 새가 날아감
    }
}

class Ostrich extends Bird {
    void fly() {
        throw new UnsupportedOperationException("타조는 날지 못함");
    }
}
```
위의 코드에서 Ostrich 클래스가 Bird 클래스를 상속받으면서 fly() 메서드를 재정의하여 예외를 던지고 있다. 이렇게 하면 Ostrich 객체를 Bird 객체처럼 대체할 수 없으며, LSP가 위반된다.

```java
interface Bird {
    void fly();
}

class Sparrow implements Bird {
    void fly() {
        // 참새가 날아감
    }
}

class Ostrich implements Bird {
    void fly() {
        // 타조는 날지 못하지만 인터페이스 구현은 필요
    }
}
```
개선된 코드에서는 Bird 인터페이스를 도입하여 모든 새 종류가 fly() 메서드를 구현할 수 있도록 변경되었다. 이로써 Ostrich 클래스도 인터페이스를 구현하므로 대체 가능성이 확보되며, LSP를 준수한다.

---

### 인터페이스 분리 원칙(Interface Segregation Principle - ISP)
- 클라이언트는 자신이 사용하지 않는 인터페이스에 의존해서는 안된다.
- 이를 통해 인터페이스를 작고 관련성 높은 단위로 분리하여 클라이언트가 필요한 기능만 사용할 수 있도록 한다.

**예시**
```java
interface Worker {
    void work();
    void eat();
}

class Engineer implements Worker {
    void work() {
        // 엔지니어의 작업 로직
    }

    void eat() {
        // 엔지니어의 식사 로직
    }
}

class Waiter implements Worker {
    void work() {
        // 웨이터의 작업 로직
    }

    void eat() {
        // 웨이터의 식사 로직
    }
}
```
위의 코드에서 Worker 인터페이스는 work()와 eat() 메서드를 가지고 있다. 그러나 Engineer와 Waiter 클래스에서는 모든 메서드를 구현해야 하기 때문에 ISP가 위반된다.

```java
interface Workable {
    void work();
}

interface Eatable {
    void eat();
}

class Engineer implements Workable, Eatable {
    void work() {
        // 엔지니어의 작업 로직
    }

    void eat() {
        // 엔지니어의 식사 로직
    }
}

class Waiter implements Workable, Eatable {
    void work() {
        // 웨이터의 작업 로직
    }

    void eat() {
        // 웨이터의 식사 로직
    }
}
```
개선된 코드에서는 Worker 인터페이스를 Workable과 Eatable로 분리하여 각각의 인터페이스는 해당하는 동작만을 갖는다. 이렇게 하면 클래스는 필요한 인터페이스를 구현하도록 선택할 수 있으므로 ISP를 준수한다.

---


### 의존 역전 원칙(Dependency Inversion Principle -DIP)
- 고수준 모듈은 저수준 모듈에 의존해서는 안되며 모든 모듈은 추상화에 의존해야 한다.
- 의존성 주입을 통해 구현하며, 이를 통해 코드의 유연성을 높이고 결합도를 낮춘다.

**예시**
```java
class LightBulb {
    void turnOn() {
        // 전구를 켬
    }

    void turnOff() {
        // 전구를 끔
    }
}

class Switch {
    private LightBulb bulb;

    public Switch() {
        bulb = new LightBulb();
    }

    void operate() {
        bulb.turnOn();
    }
}
```
위의 코드에서 Switch 클래스는 LightBulb 객체를 직접 생성하고 의존하고 있으며, 이로 인해 DIP가 위반된다.

```java
interface Switchable {
    void turnOn();
    void turnOff();
}

class LightBulb implements Switchable {
    void turnOn() {
        // 전구를 켬
    }

    void turnOff() {
        // 전구를 끔
    }
}

class Switch {
    private Switchable device;

    public Switch(Switchable device) {
        this.device = device;
    }

    void operate() {
        device.turnOn();
    }
}
```
개선된 코드에서는 Switch 클래스가 Switchable 인터페이스에 의존한다. 이렇게 하면 Switch 클래스는 다양한 Switchable 구현체를 사용할 수 있으므로 DIP를 준수한다.