## 얕은복사(Shallow Copy) 와 깊은복사(Deep Copy)

### 얕은복사(Shallow Copy)
> 얕은 복사란 실제 값이 아닌, 값을 가리키는 주소만을 복사하는 방식이다. 원본 객체와 복사본 객체는 같은 객체를 가리키며, 내부 객체들은 복사되지 않는다. 그러므로 원본 또는 복사본 객체 중 하나가 내부 객체를 수정하면 다른 객체에도 영향을 미친다.

```java
public class ShallowCopyExample {
    public static void main(String[] args) {
        Student originalStudent = new Student("Alice", 25);
        Student shallowCopyStudent = originalStudent; // 얕은 복사

        // 두 객체는 같은 참조를 가리키므로 하나를 수정하면 다른 하나도 수정된다.
        shallowCopyStudent.setAge(26);

        System.out.println(originalStudent.getAge()); // 출력: 26
    }
}
```

### 깊은복사(Deep Copy)
> 깊은 복사란 주소값이 아닌 실제 값을 복사하는 방식이다. 따라서 원본 객체와 복사본 객체는 서로 독립적으로 존재하며, 내부 객체를 수정해도 다른 객체에는 영향을 미치지 않는다.

```java
public class DeepCopyExample {
    public static void main(String[] args) {
        Student originalStudent = new Student("Bob", 30);

        // 깊은 복사를 위해 직접 복사본을 생성
        Student deepCopyStudent = new Student(originalStudent.getName(), originalStudent.getAge());

        // 내부 객체를 수정해도 다른 객체에 영향을 미치지 않는다.
        deepCopyStudent.setAge(31);

        System.out.println(originalStudent.getAge()); // 출력: 30
    }
}
```

### 참고사항
- 얕은 복사는 객체의 주소만을 복사하기 때문에, 객체 내부의 내용이 변경될 경우 다른 객체에도 영향을 미친다.
- 깊은 복사는 내부 객체까지 복사하므로 객체의 복사에 시간과 메모리가 더 소요될 수 있다.
- 객체가 복잡한 구조를 가지거나 내부에 다른 객체를 포함하는 경우, 깊은 복사를 구현하는 것이 복잡해진다. Cloneble 인터페이스의 clone() 메서드를 구현하거나, 생성자/팩터리 메서드를 직접 구현하여 사용할 수 있다.

![Additional Image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FBHMmS%2Fbtq7SLCFzf3%2FwDY82NjsXrkUf0vOfocj2k%2Fimg.png)


이미지출처 : https://developer-talk.tistory.com/86
