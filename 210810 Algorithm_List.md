# :boom: List

---

​																		

### view

```python
T = 10

for tc in range(1, T+1):
    num = int(input())
    height = list(map(int, input().split()))
    ans = 0
    
    for i in range(2, num-2):
        maxV = height[i-2]
        if maxV < height[i-1]:
            maxV = height[i-1]
        if maxV < height[i+1]:
            maxV = height[i+1]
        if maxV < height[i+2]:
            maxV = height[i+2]
        if H[i] > maxV:
            ans += H[i] - maxV
    print(f'#{tc} {ans}')
```

​																																	

---

### min max

N개의 양의 정수에서 가장 큰 수와 가장 작은 수의 차이를 출력하시오.


**[입력]**

첫 줄에 테스트 케이스의 수 T가 주어진다. ( 1 ≤ T ≤ 50 )

각 케이스의 첫 줄에 양수의 개수 N이 주어진다. ( 5 ≤ N ≤ 1000 )

다음 줄에 N개의 양수 ai가 주어진다. ( 1 ≤ ai≤ 1000000 )

**[출력]**

각 줄마다 "#T" (T는 테스트 케이스 번호)를 출력한 뒤, 답을 출력한다.

---

​																						

```python
T = int(input())

for tc in range(1, T+1):
    num = int(input())
    number_list = list(map(int, input().split()))
    # 가장 큰 수, 가장 작은 수 변수 및 기본값 설정
    number_max = number_list[0]
    number_min = number_list[0]

    for i in number_list:
        if i > number_max:
            number_max = i
        if i < number_min:
            number_min = i

    ans = number_max - number_min
    print(f'#{tc} {ans}')
```

​																		

---

### 구간합

N개의 정수가 들어있는 배열에서 이웃한 M개의 합을 계산하는 것은 디지털 필터링의 기초연산이다.

M개의 합이 가장 큰 경우와 가장 작은 경우의 차이를 출력하는 프로그램을 작성하시오.

**[입력]**
 

첫 줄에 테스트 케이스 개수 T가 주어진다. ( 1 ≤ T ≤ 50 )


다음 줄부터 테스트케이스의 첫 줄에 정수의 개수 N과 구간의 개수 M 주어진다. ( 10 ≤ N ≤ 100, 2 ≤ M ＜ N )


다음 줄에 N개의 정수 ai가 주어진다. ( 1 ≤ a ≤ 10000 )

 

**[출력]**
 

각 줄마다 "#T" (T는 테스트 케이스 번호)를 출력한 뒤, 답을 출력한다.

---

​																												

```python
T = int(input())

for tc in range(1, T+1):
    N, M = map(int, input().split())
    number_list = list(map(int, input().split()))
    new = []  # 부분합들의 리스트

    # 조건에 맞는 부분합들을 리스트에 추가
    for i in range(0, N-M+1):
        sum_part = 0
        for j in range(0, M):
            sum_part += number_list[i + j]
        new.append(sum_part)

    # 버블 정렬에 의한 부분합 리스트 정렬
    for k in range(len(new)-1, 0, -1):
        for y in range(0, k):
            if new[y] > new[y+1]:
                new[y], new[y+1] = new[y+1], new[y]

    # 최대값에서 최소값 차이 출력
    ans = new[-1] - new[0]
    print(f'#{tc} {ans} ')
    
    
    
    sum_max, sum_min = 0, n*10000
    for i in range(0, N-M+1):
        sum_part = 0
        for j in range(M):
            sum_part += number_list[i+j]
            
            if sum_part > sum_max:
                sum_max = sum_part
                
            if sum_part < sum _min:
                sum_min = sum_part
    print(f'#{tc} {sum_max - sum_min}')
```

​															

---

### 숫자 카드



0에서 9까지 숫자가 적힌 N장의 카드가 주어진다.

가장 많은 카드에 적힌 숫자와 카드가 몇 장인지 출력하는 프로그램을 만드시오. 카드 장수가 같을 때는 적힌 숫자가 큰 쪽을 출력한다.


 

**[입력]**
 

첫 줄에 테스트 케이스 개수 T가 주어진다. ( 1 ≤ T ≤ 50 )

다음 줄부터 테스트케이스의 첫 줄에 카드 장수 N이 주어진다. ( 5 ≤ N ≤ 100 )

다음 줄에 N개의 숫자 ai가 여백없이 주어진다. (0으로 시작할 수도 있다.) ( 0 ≤ ai ≤ 9 ) 

 

**[출력]**
 

각 줄마다 "#T" (T는 테스트 케이스 번호)를 출력한 뒤, 가장 많은 카드의 숫자와 장 수를 차례로 출력한다.

---

​																													

```python
T = int(input())

for tc in range(1, T+1):
    N = int(input())
    cards = input()
    cnt_list = [0]*10
    max_number = 0
    max_card = 0

    for i in cards:
        cnt_list[int(i)] += 1

    for j in range(len(cnt_list)):
        if cnt_list[j] >= max_card:
            max_card = cnt_list[j]
            max_number = j

    print(f'#{tc} {max_number} {max_card}')
```

​																						

---

### 전기버스



A도시는 전기버스를 운행하려고 한다. 전기버스는 한번 충전으로 이동할 수 있는 정류장 수가 정해져 있어서, 중간에 충전기가 설치된 정류장을 만들기로 했다.

버스는 0번에서 출발해 종점인 N번 정류장까지 이동하고, 한번 충전으로 최대한 이동할 수 있는 정류장 수 K가 정해져 있다.

충전기가 설치된 M개의 정류장 번호가 주어질 때, 최소한 몇 번의 충전을 해야 종점에 도착할 수 있는지 출력하는 프로그램을 만드시오.

만약 충전기 설치가 잘못되어 종점에 도착할 수 없는 경우는 0을 출력한다. 출발지에는 항상 충전기가 설치되어 있지만 충전횟수에는 포함하지 않는다.
 

**[입력]**
 

첫 줄에 노선 수 T가 주어진다. ( 1 ≤ T ≤ 50 )


각 노선별로 K, N, M이 주어지고, 다음줄에 M개의 정류장 번호가 주어진다. ( 1 ≤ K, N, M ≤ 100 )
 

**[출력]**


\#과 노선번호, 빈칸에 이어 최소 충전횟수 또는 0을 출력한다.

---

​																							

```python

T = int(input())
for tc in range(1, T+1):
    K, N, M = map(int, input().split())
    station = list(map(int, input().split()))
    station_lst = [0] * (N+1)

    # 충전기 설치된 정류장 카운트 리스트
    for i in range(len(station)):
        station_lst[station[i]] += 1

    start = 0
    end = K
    cnt = 0

    while True:
        # zero는 이동거리
        zero = 0
        for i in range(start+1, end+1):
            if station_lst[i] == 1:
                # 주유소에 도착하면 시작점을 주유소가 있는 위치 재설정
                start = i
            else:
                # 주유소가 없으므로 이동거리 1 증가
                zero += 1

        # 이동거리가 최대이동거리 K와 같아 졌으므로 종점도착 못함
        if zero == K:
            cnt = 0
            break
        # 충전 횟수 증가
        cnt += 1
        end = start + K

        # 종점 도착
        if end >= N:
            break

    print(f'#{tc} {cnt}')

    
    
T = int(input())

for tc in range(1, T+1):
    K, N, M = map(int, input().split())
    charge = [0] + list(map(int, input().split())) +[N]
    last = 0
    ans = 0

    for i in range(1, M+2):
        if charge[i] - charge[i-1] > K: # 운행 불가 간격인지 확인
            ans = 0
            break

        if charge[i] > last + K: # 마지막 충전 위치에서 현재 정류장에 올 수 없으면
            last = charge[i-1]
            ans += 1

    print(f'#{tc} {ans}')    
```

​																													

---

### 연속한 1의 개수



N개의 0과 1로 이루어진 수열에서 연속한 1의 개수 중 최대값을 출력하는 프로그램을 만드시오.

입력
첫 줄에 테스트케이스 개수 T, 다음 줄부터 테스트케이스별로 첫 줄에 수열의 길이 N, 다음 줄에 N개의 0과1로 구성된 수열이 공백없이 제공된다.
1<=T<=10, 10<=N<=1000

출력
\#과 테스트케이스 번호, 빈칸에 이어 답을 출력한다.

---

​																															

```python

T = int(input())

for tc in range(1, T+1):
    n = int(input())
    x = input()
    max_cnt = 0

    # for 문을 돌며 연속한 1이 있을 경우 카운트 추가, 0을 만나면 카운트 리셋
    for i in x:
        if i == '1':
            cnt += 1
        else:
            cnt = 0
        # 최대 카운트 값을 비교하여 값 기록
        if max_cnt < cnt:
            max_cnt = cnt

    print(f'#{tc} {max_cnt}')

```

​																																

---

### 당근의 개수

영준이의 당근밭은 N개의 구역으로 나뉘어 있다.  당근을 수확한 구역 순으로 당근의 개수 C가 주어질 때, 가장 많은 당근이 나온 구역은 몇 번 째 인지와 그 구역의 당근 개수를 출력하는 프로그램을 만드시오. 단, 당근의 수가 같은 구역이 있을 때는 먼저 수확한 구역의 순서를 출력한다.
5<=N<=1000, 1<=C<1000

입력
첫 줄에 테스트케이스 개수 T가 주어진다. 다음 줄 부터 각 테스트 케이스 첫 줄에 구역의 수 N이 주어지고, 다음 줄에 각 구역의 당근의 개수 C를 의미하는 N개의 수가 주어진다.

출력
\#테스트케이스번호, 구역의 순서와 당근의 개수를 빈칸을 두고 출력한다.

---

```python
T = int(input())

for tc in range(1, T+1):
    num = int(input())
    carrot = list(map(int, input().split()))
    # 최대 당근 수확의 갯수, 구역 변수 설정
    max_carrot = 0
    max_district = 0

    # 조건문을 통해 값 비교, 최대 값 변경
    for i in range(len(carrot)):
        if carrot[i] > max_carrot:
            max_carrot = carrot[i]
            max_district = i+1

    print(f'#{tc} {max_district} {max_carrot}')
```

---

​																										

### Flatten



한 쪽 벽면에 다음과 같이 노란색 상자들이 쌓여 있다.

높은 곳의 상자를 낮은 곳에 옮기는 방식으로 최고점과 최저점의 간격을 줄이는 작업을 평탄화라고 한다.

평탄화를 모두 수행하고 나면, 가장 높은 곳과 가장 낮은 곳의 차이가 최대 1 이내가 된다.

평탄화 작업을 위해서 상자를 옮기는 작업 횟수에 제한이 걸려있을 때, 제한된 횟수만큼 옮기는 작업을 한 후 최고점과 최저점의 차이를 반환하는 프로그램을 작성하시오.



가장 높은 곳에 있는 상자를 가장 낮은 곳으로 옮기는 작업을 덤프라고 정의한다.

**[제약 사항]**

가로 길이는 항상 100으로 주어진다.

모든 위치에서 상자의 높이는 1이상 100이하로 주어진다.

덤프 횟수는 1이상 1000이하로 주어진다.

주어진 덤프 횟수 이내에 평탄화가 완료되면 더 이상 덤프를 수행할 수 없으므로 그 때의 최고점과 최저점의 높이 차를 반환한다 (주어진 data에 따라 0 또는 1이 된다).

**[입력]**

총 10개의 테스트 케이스가 주어지며, 각 테스트 케이스의 첫 번째 줄에는 덤프 횟수가 주어진다. 그리고 다음 줄에 각 상자의 높이값이 주어진다.

**[출력]**

\#부호와 함께 테스트 케이스의 번호를 출력하고, 공백 문자 후 테스트 케이스의 최고점과 최저점의 높이 차를 출력한다.

---

​																																			

```python

for tc in range(1, 11):
    dump_max = int(input())
    boxes = list(map(int, input().split()))
    dump = 0

    # dump 값이 제한 덤프 횟수가 될 때까지 반복
    while dump < dump_max:
        # 버블 정렬을 통해 오름차순으로 줄 세우기
        for i in range(len(boxes)-1, 0, -1):
            for j in range(0, i):
                if boxes[j] > boxes[j+1]:
                    boxes[j], boxes[j+1] = boxes[j+1], boxes[j]
        # 최저점, 최고점인 첫항과 마지막항을 dump
        boxes[0] += 1
        boxes[-1] -= 1
        dump += 1
    # dump를 제한 횟수만큼 한 후, 마지막 오름차순 작업
    for i in range(len(boxes) - 1, 0, -1):
        for j in range(0, i):
            if boxes[j] > boxes[j + 1]:
                boxes[j], boxes[j + 1] = boxes[j + 1], boxes[j]
    # 최대값에서 최저값 빼기
    ans = boxes[-1] - boxes[0]
    print(f'#{tc} {ans}')

```

​																																				

