## `Iterator`란
=====================

자바에서 `Iterator`는 컬렉션(Collection) 요소를 순회하고 접근하기 위한 인터페이스이다. 
이 인터페이스는 Java 컬렉션 프레임워크의 일부로 제공되며, 다양한 컬렉션 타입(ArrayList, HashSet, LinkedList 등)에서 사용할 수 있다. 
Iterator를 사용하면 컬렉션의 요소를 순서대로 검색하고 제거할 수 있다.

Iterator 인터페이스는 다음과 같이 선언되어 있다

```java
public interface Iterator<E> {
    boolean hasNext();    // 다음 요소가 존재하는지 확인
    E next();             // 다음 요소를 반환
    void remove();        // 현재 요소를 제거 (optional)
}
```
### 주요 메서드 설명

hasNext(): 다음 요소가 있는지 여부를 확인하는 메서드로, boolean 값을 반환한다. 만약 다음 요소가 있으면 true를 반환하고, 없으면 false를 반환한다.

next(): 다음 요소를 반환하는 메서드로, E 형식의 요소를 반환한다. 이 메서드를 호출하기 전에 hasNext() 메서드로 다음 요소가 있는지 확인해야 한다. 그렇지 않으면 NoSuchElementException 예외가 발생할 수 있다.

remove(): 현재 요소를 제거하는 메서드로, 컬렉션을 수정하는 기능을 제공하는 메서드이다. 이 메서드는 모든 컬렉션에서 지원되지는 않고, 제공하지 않는 컬렉션에서는 UnsupportedOperationException 예외가 발생한다.

Iterator를 사용하면 컬렉션의 요소를 순회하고, 요소를 제거할 수 있다. 예를 들어, 다음과 같이 Iterator를 사용하여 ArrayList의 요소를 순회할 수 있다:

```java
ArrayList<String> list = new ArrayList<>();
list.add("Java");
list.add("Python");
list.add("C++");

Iterator<String> iterator = list.iterator();
while (iterator.hasNext()) {
    String element = iterator.next();
    System.out.println(element);
}
```
위 코드에서는 hasNext()로 다음 요소의 존재 여부를 확인하고, next()로 요소를 가져와 출력한다. 필요한 경우 remove()를 사용하여 요소를 제거할 수 있다.

