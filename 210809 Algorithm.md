# :boom:Algorithm_List1

---

​																			

## 알고리즘 

유한한 단계를 통해 문제를 해결하기 위한 절차나 방법

**어떠한 문제를 해결하기 위한 절차**



#### 	무엇이 좋은 알고리즘인가?

1.  정확성 : 얼마나 정확하게 동작하는가
2. 작업량 : 얼마나 적은 연산으로 원하는 결과를 얻어내는가
3. 메모리 사용량 : 얼마나 적은 메모리를 사용하는가
4. 단순성 : 얼마나 단순한가
5. 최적성 : 더 이상 개선할 여지없이 최적화 되었는가



#### 	시간 복잡도 = 빅 - 오(O) 표기법

- 시간 복잡도 함수 중에서 가장 큰 영향력을 주는 n에 대한 항만을 표시
- 계수는 생략하여 표시





A = [0] + list(1,2,3,4,5,)

A = [0, 1, 2, 3, 4, 5]

- 0을 추가함으로써 인덱스를 사용하기 쉬워짐



### :smile: 정렬

​																	

- #### 버블 정렬

인접한 두개의 원소를 비교하며 자리를 계속 교환하는 방식

```python
def BubbleSort(a) : #정렬할 List
    for i in range(len(a)-1,0,-1) : # 범위의 끝 위치
        for j in range(0, i) :
            if a[j] > a[j+1] :
                a[j], a[j+1] = a[j+1], a[j]
```

​																

- #### 숫자를 정렬하자.			

**[제약 사항]**

N 은 5 이상 50 이하이다.


**[입력]**

가장 첫 줄에는 테스트 케이스의 개수 T가 주어지고, 그 아래로 각 테스트 케이스가 주어진다.

각 테스트 케이스의 첫 번째 줄에 N 이 주어지고, 다음 줄에 N 개의 숫자가 주어진다.


**[출력]**

출력의 각 줄은 '#t'로 시작하고, 공백을 한 칸 둔 다음 정답을 출력한다.

(t는 테스트 케이스의 번호를 의미하며 1부터 시작한다.)		

```python
T = int(input())
for tc in range(1, T+1):
    N = int(input())
    A = list(map(int, input().split()))

    for i in range(N-1, 0, -1):
        for j in range(0, i):
            if A[j] > A[j+1]:
                A[j], A[j+1] = A[j + 1], A[j]
    print(f'#{tc}', end=' ')
    for x in A:
        print(x, end=' ')
    print()
```

##### 																					

- #### 카운팅 정렬

항목들의 순서를 결정하기 위해 집합에 각 항목이 몇 개씩 있는지 세는 작업을 하여, 

선형 시간에 정렬하는 효율적인 알고리즘

```python
def Counting_sort(A, B, k)
# A [] -- 입력 배열 (1 to k)
# B [] -- 정렬된 배열.
# C [] -- 카운트 배열.

C = [0]*(K + 1)

for i in range(0, len(B)):
    C[A[i]] += 1
for i in range(1, len(c)):
    C[i] += C[i-1]
for i in range(len(B)-1, -1, -1):
    B[C[A[i]]-1] = A[i]
    C[A[i]] -= 1
    
# C[A[i]] -= 1
# B[C[A[i]]] = A[i]
```



### 	Baby-gin Game

0~9 사이의 숫자 카드에서 임의의 카드 6장을 뽑았을 때, 

3장의 카드가 연속적인 번호를 갖는 경우를 run 이라고 하고, 

3장의 카드가 동일한 번호를 갖는 경우를 triplet 이라고 한다.

그리고 6장의 카드가 run과 triplet으로만 구성된 경우를 baby-gin이라고 부른다.

baby-gin 여부를 판단하는 프로그램을 작성하라.



```python
num = 456789
c = [0] * 10

for i in range(6):
    c[num % 10] += 1
    num //= 10
    
i = 0
tri = run = 0
while i < 10 :
    if c[i] >= 3 : # 트리플 조사 후 데이터 삭제
        c[i] -= 3
        tri += 1
        continue;
    if c[i] >= 1 and c[i+1] >=1 and c[i+2] >= 1 : #run 조사 후 데이터 삭제
        c[i] -= 1
        c[i+1] -= 1
        c[i+2] -= 1
        run += 1
        continue
    i += 1
    
if run + tri == 2 : print("Baby Gin")
    else: print("Lose")
```





### 	Gravity

방이 오른쪽으로 90도 회전하여 상자들이 중력의 영향을 받아 낙하한다고 할 때, 

낙차가 가장 큰 상자를 구하여 그 낙차를 리턴하는 프로그램을 작성하시오.

- 방의 가로, 세로 길이는 항상 100이다.



```python
T = int(input())

for tc in range(1, T+1):
    num = int(input())
    boxes = list(map(int, input().split()))

    # 가장 큰 낙차 설정, 맨 처음 박스부터 순차적으로 낙차 확인.
    max_drop = 0
    for i in range(num-1):
        box_number = boxes[i]
        box_drop = 0

        # 다음 상자보다 클 경우 낙차가 1씩 증가.
        for j in range(i+1, num):
            if box_number > boxes[j]:
                box_drop += 1

        # 해당 낙차가 기존의 max_drop 보다 클 경우 낙차 값 교체
        if box_drop > max_drop:
            max_drop = box_drop

    print(f'#{tc} {max_drop}')
```







### 	View

강변에 빌딩들이 옆으로 빽빽하게 밀집한 지역이 있다.

이곳에서는 빌딩들이 너무 좌우로 밀집하여, 강에 대한 조망은 모든 세대에서 좋지만 

왼쪽 또는 오른쪽 창문을 열었을 때 바로 앞에 옆 건물이 보이는 경우가 허다하였다.

그래서 이 지역에서는 왼쪽과 오른쪽으로 창문을 열었을 때, 

양쪽 모두 거리 2 이상의 공간이 확보될 때 조망권이 확보된다고 말한다.

빌딩들에 대한 정보가 주어질 때, 조망권이 확보된 세대의 수를 반환하는 프로그램을 작성하시오.

아래와 같이 강변에 8채의 빌딩이 있을 때, 연두색으로 색칠된 여섯 세대에서는 

좌우로 2칸 이상의 공백이 존재하므로 조망권이 확보된다. 따라서 답은 6이 된다.



```python
for tc in range(1, 11):
    number = tc
    apart_len = int(input())
    apart = list(map(int, input().split()))
    cnt = 0

    for i in range(2, apart_len - 2):
        a = apart[i] - apart[i - 2]
        b = apart[i] - apart[i - 1]
        c = apart[i] - apart[i + 1]
        d = apart[i] - apart[i + 2]

        if a > 0 and b > 0 and c > 0 and d > 0:
            cnt += 1 * min(a, b, c, d)

    print(f'#{number} {cnt}')
```

