## reflection 이란?
> 리플렉션은 구체적인 클래스 타입을 알지 못하더라도 그 클래스의 메서드, 타입, 변수들에 접근할 수 있도록 해주는 자바 API 를 말하며, 컴파일 시간이 아닌 실행 시간에 동적으로 특정 클래스의 정보를 추출할 수 있는 프로그래밍 기법이라 할 수 있다.

### 리플렉션을 사용하여 가져올 수 있는 정보
- Class
- Constructor
- Method
- Field

### 리플렉션을 사용하는 시점 
- 작성 시점에는 어떠한 클래스를 사용해야 할 지 모르지만 런타임 시점에서 가져와서 실행해야 하는 경우 사용한다.
- 즉, 동적으로 클래스를 사용해야할 때 사용한다.
- 프레임워크, IDE 에서는 이러한 동적 바인딩을 이용한 기능을 제공한다
  - ex : IntelliJ의 자동완성 기능, 스프링 어노테이션 등

### 리플렉션을 사용하는 작업에 대한 예시
1. **클래스 로드 및 인스턴스 생성** :
   Class.forName() 메소드를 사용하여 동적으로 클래스를 로드하고, newInstance() 메소드를 호출하여 클래스의 인스턴스를 생성할 수 있다.
    ```java
   try {
    // 클래스 이름 동적으로 로드
    Class<?> clazz = Class.forName("com.example.MyClass");
    
    // 클래스의 기본 생성자를 사용하여 인스턴스 생성
    Object obj = clazz.newInstance();
    
    // obj를 MyClass 타입으로 캐스팅
    MyClass myObject = (MyClass) obj;
    } catch (ClassNotFoundException | InstantiationException | IllegalAccessException e) {
    e.printStackTrace();
    }
   ```
   
2. **클래스의 메소드 접근 및 호출** : getMethods() 메소드를 사용하여 클래스의 메소드 정보에 접근할 수 있다. 메소드 외에도 getFields(), getConstructors() 등을 사용하여 필드, 생성자 정보에도 접근 가능하다.
    ```java
    try {
    // 클래스 이름 동적으로 로드
    Class<?> clazz = Class.forName("com.example.MyClass");
    
    // 메소드 이름과 매개변수 타입으로 메소드 가져오기
    Method method = clazz.getMethod("myMethod", String.class, int.class);
    
    // 메소드 호출 (인스턴스, 매개변수)
    Object result = method.invoke(obj, "Hello, World!", 42);
    } catch (ClassNotFoundException | NoSuchMethodException | IllegalAccessException | InvocationTargetException e) {
    e.printStackTrace();
    }
    ```
   
3. **클래스의 필드접근 및 값 설정,조회** : getFields(), getDeclaredField()등의 메서드를 이용하여 필드 접근이 가능하다. 이 때, **getFields()** 메소드는 **public 접근 지정자를 가진 필드만 반환**하며, **getDeclaredField()** 메소드는 **접근 지정자와 관계없이 해당 클래스에서 선언된 모든 필드에 접근**할 수 있다.
    ```java
    try {
    // 클래스 이름 동적으로 로드
    Class<?> clazz = Class.forName("com.example.MyClass");
    
    // 필드 이름으로 필드 가져오기
    Field field = clazz.getDeclaredField("myField");
    
    // 필드의 접근성 수정 (private 필드에 접근하기 위해)
    field.setAccessible(true);
    
    // 필드 값 설정
    field.set(obj, "New Value");
    
    // 필드 값 읽기
    Object fieldValue = field.get(obj);
    } catch (ClassNotFoundException | NoSuchFieldException | IllegalAccessException e) {
    e.printStackTrace();
    }
    ```