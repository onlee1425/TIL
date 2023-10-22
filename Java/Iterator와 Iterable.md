## Iterator(반복자)
- Iterator는 Collection에 저장된 요소를 읽어오는 것을 표준화한 인터페이스로, 원소를 순회하기 위한 인터페이스이다.
- `hasNext()` 메서드로 다음 원소의 존재 여부를 확인하고, `next()`메서드로 다음 원소를 반환한다.
- `remove()` 메서드로 반환된 요소를 제거하고, `forEachRemaining()` 메서드로 모든 요소가 처리되거나 예외가 던져질때까지 지정된 작업을 수행할수 있다.
- Iterator를 사용하여 Iterable의 원소를 순차적으로 접근할 수 있다.

## Iterable(반복 가능한 객체)
![AdditionalImage](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbgbJkF%2FbtrSCLQz8Qd%2Fe94GtwAHsKuND48KMFhEf1%2Fimg.jpg)
- Iterable은 자바에서 반복 가능한 객체를 나타내는 인터페이스이며, Iterator 구현체를 반환하는 iterator() 메서드가 선언되어있다.
- Iterable은 하나 이상의 원소를 가진 Collection을 나타낸다. (Iterable은 Collection의 상위 인터페이스이다)
- Iterable을 상속받는 클래스는 Iterator를 사용하여 for-each 루프를 사용할 수 있다.


```java
//일반적인 for문
for (int i=0; i<length; i++) {
    …
}

//for each문
for (String str : list) {
    System.out.println(str);
}

//for each문이 실제 동작되는 코드 (iterator가 사용됨)
Iterator<String> iterator = list.iterator();
while(iterator.hasNext()) {
    System.out.println(iterator.next());
}
```

- 즉, Iterable 인터페이스는 하위 클래스에서 iterator()의 생성을 강제하는 역할을 한다.
- 따라서 Iterable을 상속받은 Collection의 하위 클래스들은 모두 iterator() 메서드를 가지고 있게 되며, Iterator 인터페이스를 구현한 클래스는 hasNext(), next() 등을 구현하고 있기 때문에 이를 활용하여 반복 기능을 사용할 수 있다.