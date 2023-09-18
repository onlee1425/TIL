## List, Set, Map의 차이점

>List, Set, Map은 모두 데이터를 저장하고 관리하기 위한 자료 구조(data structure)이다. 

### List (목록)

- List는 순서가 있는 데이터를 저장하는 자료 구조이다. 각 요소는 고유한 위치(인덱스)를 가지며, 요소의 순서가 중요하다. 일반적으로 0부터 시작하는 인덱스를 사용한다.
- List는 요소의 중복을 허용한다. 즉, 동일한 값을 여러 번 저장할 수 있다.
- List는 배열(array) 또는 동적 배열(dynamic array)로 구현된다. 요소를 추가하거나 삭제할 때 크기를 조절할 수 있다.

### Set (집합)

- Set은 중복되지 않는 고유한 요소들을 저장하는 자료 구조이다. 요소의 순서는 중요하지 않다. 즉, 집합 내에서 각 요소는 단 한 번만 나타난다.
- Set은 주로 중복된 값을 제거하거나 고유한 값을 유지하기 위해 사용된다. 예를 들어, 중복 제거 작업에 유용하다.
- Set은 해시 집합(hash set) 또는 트리 집합(tree set)과 같은 구현을 가질 수 있다.

### Map (맵 또는 딕셔너리)

- Map은 키-값 쌍(key-value pair)을 저장하는 자료 구조이다. 각 키는 고유하며, 각 키에 해당하는 값에 접근하기 위해 사용된다.
- Map은 검색, 삽입, 삭제 작업에 효율적이다. 특히, 특정 키로 값을 빠르게 찾을 때 유용하다.
- Map은 해시 맵(hash map), 트리 맵(tree map), 연결 리스트 맵(linked list map) 등 다양한 구현이 있다.

### 요약 
- List: 순서가 있고 중복을 허용하는 자료 구조.
- Set: 중복을 허용하지 않고 고유한 값을 저장하는 자료 구조.
- Map: 키-값 쌍을 저장하며, 각 키는 고유하며 값에 접근하는 데 사용하는 자료 구조.


![Additional Image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Ftdpf5%2Fbtq127JQCI8%2FLSdj32IFJg2bsAinWk5bBK%2Fimg.png)
