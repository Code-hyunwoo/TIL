# :boom: 	Python 실전문제 연습

---

​		

### 	[응용] 한자리 씩 출력하기

> 사용자로부터 숫자 입력 받은 양의 정수의 각 자리 수를 1의 자리부터 차례대로 출력하는 코드를 작성해보세요.

------

**[입력 예시]**

185

**[출력 예시]**

5

8

1

```python
#
n = int(input())
while n > 0:
    print(n % 10)
    n = n // 10   
```



### 	[실습] for 문과 if 문 작성하기

> 반복문과 조건문만 활용하여 1~30까지 숫자 중에 홀수만 출력해보세요.

------

**[출력 예시]**

```
1
3
5
...
27
29
```

​		

```python
for i in range(1,31):
    if i%2:
        print(i)
```



### 	리스트(list) 순회에서 index의 활용하기



```python
lunch = ['짜장면', '초밥', '피자']
for i in range(len(lunch)):
    print(f'{i+1}번째 메뉴: {lunch[i]}')
    
1번째 메뉴: 짜장면
2번째 메뉴: 초밥
3번째 메뉴: 피자
```

​		

### 	[연습] `break` 활용하기

> 조건문과 반복문, `break`를 활용하여 리스트에서 쌀이 나왔을때 `for` 문을 멈추는 코드를 작성하세요.

------

**[출력 예시]**

​	보리

​	보리

​	쌀

​	잡았다!

​		

```python
for i in rice:
    print(i)
    if i == '쌀':
        print('잡았다!')
        break
```



### `continue`

```python
for i in range(6):
    if i % 2 == 0:
        continue
        # continue 이후의 코드는 실행되지 않습니다.
    print(f'{i}는 홀수다.')
```

```
1는 홀수다.
3는 홀수다.
5는 홀수다.
```



### 	[연습] `continue` 문 작성하기

> 나이가 입력된 리스트가 있을때, 조건문과 반복문, continue를 활용하여 20살 이상일때만 "성인입니다"라는 출력을 하는 코드를 작성하세요.

------

**[출력 예시]**

23 살은 성인입니다.

30 살은 성인입니다.

25 살은 성인입니다.

31 살은 성인입니다.

```python
for age in ages:
    if age < 20:
        continue
    print(f'{age} 살은 성인입니다.')
```

```
23살은 성인입니다.
30살은 성인입니다.
25살은 성인입니다.
31살은 성인입니다.
```



### 	[연습] `for-else` 활용하기

> 조건문과 반복문, break, else 를 통해서 아래의 코드와 동일한 코드를 작성하세요.

- numbers 리스트에 4가 있을 경우 `True`를 출력하고, 없을 경우 `False`를 출력한다.

------

​	**[출력 예시]**

```
False
```

​		

```python
numbers = [1, 3, 4, 9]

for i in numbers:
    if i == 4:
        print('True')
        break
else:    print('False')
```

```
True
```



​		

## 1.7 'a'가 싫어

> 입력으로 짧은 영단어 word가 주어질 때, 해당 단어에서 'a'를 모두 제거한 결과를 출력하시오.

------

```python
[입력 예시]
apple

[출력 예시]
pple
```

​		

```python
# 아래에 코드를 작성하시오.
for i in word:
    if i == 'a':
        continue
    print(i, end = '')
```



​		

## 	단어 뒤집기

> 입력으로 짧은 영어단어 word가 주어질 때, 해당 단어를 역순으로 뒤집은 결과를 출력하시오.

---
```
[입력 예시]
apple

[출력 예시]
elppa
```

​		

```python
word = input()
word[::-1]
```

```
'elppa'
```

