# :boom: Review Study

---



````python
## 1.1 Doggy

> 개의 속성과 행위를 정의하는 Doggy 클래스 만들기

**구성 요소**

1. 초기화 메서드는 인자로 개의 이름과 견종을 받아서 인스턴스 변수에 할당한다.
2. 클래스 변수는 태어난 개의 숫자와 현재 있는 개의 숫자를 기록하는 변수로 구성한다.
   - 개가 태어나면 `num_of_dogs`와 `birth_of_dogs`의 값이 각 1씩 증가한다.
   - 개가 죽으면 `num_of_dogs`의 값이 1 감소한다.
3. 개는 각자의 이름과 나이가 있다.
4. `bark()` 메서드를 호출하면 개는 짖을 수 있다.
5. `get_status()` 메서드를 호출하면 `birth_of_dogs`와 `num_of_dogs`의 수를 출력할 수 있다.

------

예시)

```python
d1 = Doggy('초코', '푸들')
d2 = Doggy('꽁이', '말티즈')
d3 = Doggy('별이', '시츄')

d1.bark() #=> 왈왈!
d2.bark() #=> 왈왈!
d3.bark() #=> 왈왈!

Doggy.get_status() #=> Birth: 3, Current: 3
```



```python
class Doggy:
    pass
    num_of_dogs = 0
    birth_of_dogs = 0
    
    def __init__(self, name ,species):
        self.name = name
        self.age = 0
        self.species = species
        Doggy.birth_of_dogs += 1
        Doggy.num_of_dogs += 1
    
    def __del__(self):
        Doggy.num_of_dogs -= 1
        
    def bark(self):
        print('왈왈멍멍')
    
    @classmethod
    def get_status(cls):
        print('num_of_dogs: ', cls.num_of_dogs)
        print('birth_of_dogs: ', cls.birth_of_dogs)
    
d1 = Doggy('초코', '푸들')
d2 = Doggy('꽁이', '말티즈')
d3 = Doggy('별이', '시츄')

d1.bark() #=> 왈왈!
d2.bark() #=> 왈왈!
d3.bark() #=> 왈왈!

Doggy.get_status()									
```
````

​																			



​																				

## 1.1 Pair Matching Program

> 페어 프로그래밍은 하나의 컴퓨터에서 두 사람의 프로그래머가 작업하는 방식을 의미한다.
>
> SSAFY 1학기 정규 과정에서 프로젝트는 페어 프로그래밍을 통해 진행한다. 진정한 프로그래머가 되기 위해 김싸피는 페어를 매칭하기 위한 프로그램을 작성하려고 한다. 클래스를 활용해 작성하며 포함되는 메서드는 아래와 같다.

**구성 요소**

1. 초기화 메서드는 인자로 학생 이름으로 구성된 리스트를 받아서 인스턴스 변수에 할당한다.
2. `pick(n)` 메서드는 학생들 명단에서 인자 n명 만큼 랜덤으로 추출하여 return한다.
3. `match_pair()` 메서드는 학생들 명단을 랜덤으로 2명씩 매칭해 준다. 이때, 학생들 명단의 수가 홀수명이면 단 한팀만 3명으로 구성한다.

예시)

```python
ch = ClassHelper(['김싸피', '이싸피', '조싸피', '박싸피', '정싸피'])

ch.pick(1) #=> ['이싸피']
ch.pick(1) #=> ['김싸피']
ch.pick(2) #=> ['김싸피', '박싸피']
ch.pick(3) #=> ['김싸피', '조싸피', '정싸피']
ch.pick(4) #=> ['박싸피', '이싸피', '김싸피', '정싸피']

ch.match_pair() #=> [['조싸피', '이싸피'], ['김싸피', '정싸피', '박싸피']]
```



```python
import random

class ClassHelper:
    def __init__(self, students):
        self.students = students
        
    def pick(self, number):
        return random.sample(self.students, number)
    
    def match_pair(self):
        random.shuffle(self.students)
        pairs = []
        pair_count = len(self.students) // 2
        
        for idx in range(pair_count):
            if idx == pair_count - 1:
                pair = self.students[idx*2:]
                pairs.append(pair)
                return pairs
            
            pair = self.students[idx*2:idx*2+2]
            pairs.append(pair)
```



```python
# 해당 코드를 통해 올바른 결과가 나오는지 확인하시오.
ch = ClassHelper(['김싸피', '이싸피', '조싸피', '박싸피', '정싸피'])
```



```python
ch.pick(1) #=> ['이싸피']
ch.pick(1) #=> ['김싸피']
ch.pick(2) #=> ['김싸피', '박싸피']
ch.pick(3) #=> ['김싸피', '조싸피', '정싸피']
ch.pick(4) #=> ['박싸피', '이싸피', '김싸피', '정싸피']

ch.match_pair() #=> [['조싸피', '이싸피'], ['김싸피', '정싸피', '박싸피']]
```

