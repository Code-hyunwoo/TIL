# :boom: Python Review 2

---



**문자열**

- 순서가 있고
- 수정불가능하고
- 순회할 수 있고.



**.index(x)**

x의 첫번째 위치를 반환 없으면 valueError 뜸



**.replace(old, new[,count])**

바꿀 대상 글자를 새로운 글자로 바꿔서 반환



**.strip()**

특정한 문자들을 지정하면,

양쪽을 제거하거나 왼쪽을 제거하거나 오른쪽을 제거

문자열을 지정하지 않으면 공백을 제거함.



**.split()**

문자열을 특정한 단위로 나눠 리스트로 반환

'a,b,c'.split('_')

['a,b,c']

'a b c'.split()

['a', 'b', 'c']



**'separator'.join(iterable)**

반복가능한 컨테이너 요소들을 sperator로 합쳐 문자열 반환

'!'.join('ssafy')

's!s!a!f!y'

capitalize() : 앞글자를 대문자로

title() : '나 공백 이후를 대문자로

swapcase() : 대 <>소문자로 변경하여



**.insert(i,x)**

정해진 위치 i에 값을 추가함

리스트 길이보다 큰 경우 맨 뒤



**.remove(x)**

리스트에서 값이 x인 것 삭제 없는 경우 ValueError



**.pop(i)**  이건 리스트 pop

정해진 위치 i에 있는 값을 삭제하고 그 항목을 반환함

지정되지 않으면 마지막 항목을 삭제하고 반환함



**.clear()**

모든 항목을 삭제함



**.sort()**

원본 리스트를 정렬함. None 반환

**sorted** 

정렬된 리스트를 반환. 원본 변경 없음



**.reverse()**

순서를 반대로 뒤집음 정렬하는 것이 아님



**얕은 복사**

a = [1, 2, 3]

**b= a[:]**

Slice 연산자 활용하여 같은 원소를 가진 리스트지만 연산된 결과를 복사

**b=list(a)**

list()활용하여 같은 원소를 가진 리스트지만 연산된 결과를 복사



**깊은 복사**

copy.deepcopy(a)



**map(function, iterable)**

**filter(function, iterable)**

결과가 True인 것들을 반환



### 세트

- 변경 가능하고
- 순서가 없고
- 순회가 가능함



.add

.update(여러값)

.remove()   **없으면 KeyError**

.discard() **없어도 에러가 발생하지 않음**

.pop() 임의의 원소를 제거해 반환 이건 세트 pop



#### 딕셔너리 



.get(key[,default])

key를 통해 value를 가져옴. **KeyError가 발생하지 않으며**, default값을 설정할 수 있음 기본 None

.pop(key[,default])

key가 딕셔너리에 있으면 제거하고 해당값을 반환

**그렇지 않으면 default를 반환, default 값이 없으면 KeyError**



가상환경 생성 

python -m venv <폴더명>



**isinstance(object, classinfo)**

classinfo가 tuple 인 경우 하나라도 일치하면 True

isinstance(0, (bool, int, complex))

True

ininstance(0, (bool, 'hi', complex))

TypeError classinfo가 type으로 구성되야함



**인스턴스 메서드**

**클래스 메서드**

**스태틱 메서드** - 호출 시, 어떠한 인자도 전달되지 않음

- 스태틱 메서드는 메서드 내부에서 어떠한 객체의 정보도 활용하지 않으며, 클래스가 호출하여 활용함
- 클래스 메서드는 메서드 내부에서 클래스 정보(cls를 활용, 클래스가 호출하여 활용함)
- 인스턴스 메서드는 메서드 내부에서 인스턴스 정보를 활용, 인스턴스가 호출하여 활용함
- 인스턴스는 모든 메서드를 호출 할 수 있음. 하지만 인스턴스의 동작은 반드시 인스턴스 메서드로 정의





issubclass(class, classinfo)

issubclass(bool, int)

True

issubclass(professor,(person, student))

True  하나라도 맞으면 맞나봐. 모든항목 검사한다.



**super()**

자식클래스에서 부모클래스를 사용하고 싶은 경우

```python
super().__init__(name, age, numberm, email)
```



