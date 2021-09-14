# :boom: Database

---



### 데이터베이스(DB)

- 체계화된 데이터의 모임
- 몇 개의 자료 파일을 조직적으로 통합하여 자료 항목의 중복을 없애고 자료를 구조화하여 기억시켜 놓은 자료의 집합체



#### ★ 데이터베이스로 얻는 장점들

- 데이터 중복 최소화
- 데이터 무결성
- 데이터 일관성
- 데이터 독릭성(물리적/논리적)
- 데이터 표준화
- 데이터 보안 유지





#### SQL (Structured Query Language)

관계형 데이터베이스 관리시스템의 데이터 관리를 위해 설계된 특수 목적으로 프로그래밍 언어



#### ★ SQL 분류 

CREATE // INSERT, SELECT, UPDATE, DELETE 구분 문제 나오는듯..?

DDL - 데이터 정의 언어

DML - 데이터 조작 언어

DCL - 데이터 제어 언어 



**★ CREATE TABLE**

**★ DROP TABLE classmates;**

.tables  테이블 확인



**★ Storage 자료형** 들어갈 수 있는 속성..

**NULL**

**INTEGER**

**REAL - floating number(?)** 

**TEXT**

**BLOB - 영상이나 파일**

​																				

## CRUD

---

VALUES, VALUE 이런 S 구분 잘해야 함.

**★ INSERT INTO classmates (name, age) VALUES ('홍길동', 23);**

**★ INSERT INTO classmates VALUES('홍길동', 30, '서울');**

**★ LIKE**

​																

ORDER BY age ASC, balance DESC

age로 오름차순한 다음, balance로 내림차순

★ **ALTER TABLE ERROR가 나는 이유와 해결방안**

​	테이블에 있던 기존 레코드들에는 새로 추가할 필드에 대한 정보가 없다.

그렇기 때문에 NOT NULL 형태의 컬럼은 추가가 불가능하다. 

해결방법은 2가지이다. NOT NULL 설정없이 추가하기, 또는 기본값(DEFAULT) 설정하기.





## ORM 

ORM의 단점은 느리다는 것.



**★sql 과 orm 서로 변환**

**★ 레코드 생성 실패예시 +1 다음 중 옳은것은**

orm은 limit쓰려면 슬라이스 [:5] 이런식으로 사용.

but [-1] 음수는 지원안됨



__gte 같거나 큰거

__gt 큰거

__lte 같거나 작은거

__lt 작은거



ORM 활용하기 

**★OR 사용 Q**



검색할 때 필요한 구문

Entry.objects.get(title_contains='search')

SELECT .. WHERE headline LIKE '%search%'

**★ 나이가 많은 사람 순으로 10명 - ORM**



잔액이 적고 나이가 많은 순으로 10명

ORDER BY balance'ASC, age DESC    정답 잘못됨



#### ★ 시험문제 정리

**.tables  는 SQL 문법이 아니다. 점붙이는거.**

Primary key :각 행의 고유값 id아니다. database는 pk다. 

SQL 분류표 (특히, DML에 무엇이 있는지 예시)

인서트 각 문법의 차이점 해보기 리미트, 디스팃트, ★오프셋(OFFSET)

삭제하는거 REMOVE아니고 **DELETE**임

UPDATE SET~~ 

SQLITE functions(aggregate)

LIKE 패턴

ORDER BY

GROUP BY conut sum 이런거.

ORM OR쓸 때 Q쓰는거

