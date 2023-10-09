## Join의 개념과 종류
## Join이란
>"Join"은 데이터베이스 관리 시스템 (DBMS)에서 사용되는 용어로, 여러 테이블에서 데이터를 결합하거나 연결하는 작업을 의미한다.
데이터베이스에서는 관련된 정보를 여러 테이블에 나눠 저장하는 것이 일반적이며, 이러한 테이블 간에 관련성을 설정하고 필요한 정보를 가져오기 위해 Join 연산을 사용한다.

## Join의 종류

| 구분         | 내용                                                           |
|------------|----------------------------------------------------------------|
| Inner Join | 두 테이블을 조인할 때 두 테이블에 모두 지정한 열의 데이터가 존재해야 하는 경우 |
| Outer Join | 두 테이블을 조인할 때 한 개의 테이블에만 데이터가 있어도 결과가 도출되는 경우 |
| Cross Join | 한 쪽 테이블의 모든 행과 다른 쪽 테이블의 모든 행을 조인시키는 경우 |
| Self Join  | 한 개의 테이블 안에서 자신이 자기 자신과 조인되는 경우 |


### Inner Join (내부 조인)
- Inner Join은 두 개 이상의 테이블에서 공통된 값을 가지고 있는 행을 결과로 반환한다. 두 개 이상의 테이블을 연결할 때 가장 많이사용한다.
- Inner Join을 사용하면 두 테이블 사이의 교집합을 반환한다.
```mysql
[Inner Join 의 형식]

SELECT 열 목록
FROM 첫 번째 테이블
  INNER JOIN 두 번째 테이블
  ON 조인할 조건
WHERE 검색 조건
```
---
### Outer Join (외부 조인)
- Outer Join은 Inner Join의 반대 개념으로, 두 테이블 사이에서 일치하지 않는 행을 포함하여 모든 행을 결과로 반환한다. 즉, 한쪽에만 데이터가 있어도 결과를 반환한다.
- Outer Join에는 Left Outer Join, Right Outer Join 및 Full Outer Join이 포함된다.

#### Left Join (또는 Left Outer Join)
- Left Join은 왼쪽 테이블의 모든 행을 가져오고, 오른쪽 테이블에서 일치하는 행이 있는 경우 그 행도 가져온다. 일치하지 않는 경우 NULL 값을 채운다.
- 주로 왼쪽 테이블의 모든 정보를 유지하면서 연결된 정보가 있는 경우에 사용된다.
```mysql
[Left Join 의 형식]
SELECT 열 목록
FROM 첫 번째 테이블
  LEFT OUTER JOIN 두 번째 테이블
ON 조인할 조건
WHERE 검색 조건
```
#### Right Join (또는 Right Outer Join)
- Right Join은 Left Join의 반대로 동작하며, 오른쪽 테이블의 모든 행을 가져오고, 왼쪽 테이블에서 일치하는 행이 있는 경우 그 행도 가져온다. 일치하지 않는 경우 NULL 값을 채운다.
```mysql
[Right Join 의 형식]
SELECT 열 목록
FROM 첫 번째 테이블
  RIGHT OUTER JOIN 두 번째 테이블
ON 조인할 조건
WHERE 검색 조건
```
#### Full Outer Join
- Full Outer Join은 두 테이블 사이의 모든 행을 가져온다. 일치하는 행과 일치하지 않는 행 모두를 포함하며, 일치하지 않는 경우 NULL 값을 채운다.
```mysql
[Full Outer Join 의 형식]
SELECT 열 목록
FROM 첫 번째 테이블
  FULL OUTER JOIN 두 번째 테이블
  ON 조인할 조건
WHERE 검색 조건
```
---
### Cross Join (상호 조인)
- Cross Join은 한쪽 테이블의 모든 행과 다른쪽 테이블의 모든 행을 서로 조인시켜 두 개의 테이블 간에 모든 가능한 조합을 만들어 낸다. 
- Cross Join은 두 테이블 간의 관계나 조건을 고려하지 않고, 한 테이블의 각 행을 다른 테이블의 각 행과 결합하여 Cartesian 곱을 생성합니다.
  - Cartesian 곱 이란? 두 테이블의 각 행의 갯수를 곱한 수 = 전체 행의 갯수
```mysql
[Cross Join 의 형식]

SELECT *
FROM 첫 번째 테이블
CROSS JOIN 두 번째 테이블
```
---
### Self Join (자체 조인)
- Self Join은 한 개의 테이블 안에서 자신의 다른 행과 조인하는 것을 의미한다. 
- 주로 동일한 테이블 내에서 부모-자식 관계나 계층 구조와 같은 관계를 표현하기 위해 사용된다.
```mysql
[Self Join 의 형식]

SELECT 열 목록
FROM 1개의 대상 테이블 별칭 A
  INNER JOIN 1개의 대상 테이블 별칭 B
  ON 조인할 조건
WHERE 검색 조건
```

Join 연산은 데이터베이스 쿼리에서 데이터를 조작하고 분석하는 데 필수적이다. 
올바른 Join 유형을 선택하고 조건을 정확하게 설정하는 것이 중요하며, 이를 통해 원하는 결과를 얻을 수 있다.


