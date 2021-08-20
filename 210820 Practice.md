# :boom: Practice

---

​																												

### 길찾기

---

```python
 # 인접 리스트
for _ in range(1,11):
    tc, N = map(int, input().split())
    road = list(map(int, input().split()))

    adj_list = [[] for _ in range(100)]
    for i in range(N):
        adj_list[road[2*i]].append(road[2*i+1])

    visited = [0] * 100
    ans = 0

    stack = [0]

    while stack:
        curr = stack.pop()

        if curr == 99:
            ans = 1
            break

        if visited[curr]:
            continue
        visited[curr] = 1

        for w in adj_list[curr]:
            if not visited[w]:
                stack.append(w)

    print("#{} {}".format(tc, ans))
```

---

```python
def DFS(v):
    global ans
    if v == 99:
        ans = 1
        return

    visited[v] = 1

    for w in range(100):
        if not visited[w] and adj_arr[v][w]:
            DFS(w)


for _ in range(10):
    tc, road = map(int, input().split())
    adj_arr = [[0] * 100 for _ in range(100)]
    edges = list(map(int, input().split()))
    for i in range(road):
        start, end = edges[i * 2], edges[i * 2 + 1]
        adj_arr[start][end] = 1
    visited = [0] * 100
    ans = 0

    DFS(0)
    print("#{} {}".format(tc, ans))
```

---

​																	

### 삼성시의 버스노선

```python

#1. 모든 노선 체크

def bus_count(bus_stop):
    cnt = 0

    for i in range(N):
        if bus_route[i][0] <= bus_stop <= bus_route[i][1]:
            cnt += 1
    return cnt


T = int(input())
for tc in range(1, T+1):
    N = int(input())   # 버스 노선 수

    bus_route = []     # 버스의 노선들을 저장해 놓을 리스트

    for i in range(N):
        A, B = map(int, input().split())
        bus_route.append([A, B])

    P = int(input())  # 내가 확인하고 싶은 정류장의 개수
    ans = []          # 버스 수를 저장해 놓을 리스트
    for i in range(P):
        C = int(input())
        ans.append(bus_count(C))

    print("#{}".format(tc), end=" ")
    print(' '.join(map(str, ans)))
```

---

```python

#2. 정류장 계산

T = int(input())
for tc in range(1, T+1):
    N = int(input())   # 버스 노선 수

    start = [0] * 5001 # 출발 정류장 표시
    end = [0] * 5001   # 도착 정류장 표시
    bus_stop = [0] * 5001  # 계산 정류장 버스 표시

    for i in range(N):
        A, B = map(int, input().split())
        start[A] += 1
        end[B] += 1

    # 버스 계산
    for i in range(len(bus_stop)-1):
        bus_stop[i+1] = bus_stop[i] - end[i] + start[i+1]   # 이전 버스계산 - 이전 도착버스 + 새롭게 출발한 버스
    P = int(input())
    print("#{}".format(tc), end=' ')
    for i in range(P):
        C = int(input()) # 확인하고 싶은 정류장 번호
        print(bus_stop[C], end=" ")
    print()          # 줄바꿈해주는거 잊으면 안됨. 주의 중요!!
```

---

​																		

### 백만장자

```python

T = int(input())
for tc in range(1, T+1):
    N = int(input())
    cost = list(map(int, input().split()))

    ans = 0

    for i in range(N-1):  # 어차피 마지막날은 사도 그만 안사도 그만이니.
        max_cost = cost[i]
        for j in range(i+1, N):
            if max_cost < cost[j]:
                max_cost = cost[j]

        if max_cost > cost[i]:
            ans += max_cost - cost[i]  # 이익을 구하자.

    print("#{} {}".format(tc, ans))   # 너무 오래걸림
```

---

```python

T = int(input())
for tc in range(1, T+1):
    N = int(input())
    cost = list(map(int, input().split()))

    ans = 0

    max_cost = cost[-1]
    
    for i in range(N-2, -1, -1):  # 마지막 값은 의미가 없어요
        if max_cost > cost[i]:
            ans += max_cost - cost[i]
        else:
            max_cost = cost[i]
            
    print("#{} {}".format(tc, ans)) 
```

---

​																

### 자기방으로 돌아가기

```python
def div(num):
    return (int(num)+1) // 2

T = int(input())
for tc in range(1, T+1):
    N = int(input())   # 돌아갈 사람의 수

    students = [list(map(div, input().split())) for _ in range(N)]

    road = [0] * 201

    for i in range(N):
        if students[i][0] > students[i][1]:
            students[i][0], students[i][1] = students[i][1], students[i][0]

        for j in range(students[i][0], students[i][1]+1):
            road[j] += 1

    print("#{} {}".format(tc, max(road)))

```

---

```python

T = int(input())
for tc in range(1, T+1):
    n = int(input())
    room = [list(map(int, input().split())) for _ in range(n)]
    corridors = [0] * 200                     # 위아래 room 사이의 복도를 0번부터 199까지 번호를 매김

    for i, j in room:                         # room 번호 입력값에 대해서
        move_i = (i-1) // 2                   # 방이 1번부터 시작하므로
        move_j = (j-1) // 2                   # 1을 빼서 맨 앞 복도가 0번부터 시작하게 만듬
        if move_i >= move_j:                  # 두 변수 중에서 큰 값에서 작은 값으로 이동
            for k in range(move_j, move_i+1):
                corridors[k] += 1             # 이동하면서 지나는 복도번호에 1씩 추가하며 카운팅
        else:
            for k in range(move_i, move_j+1):
                corridors[k] += 1

    max_time = 0
    for corridor in corridors:                # 카운팅 된 복도 값에 대하여 최댓값 구하기
        if corridor > max_time:
            max_time = corridor

    print(f'#{tc} {max_time}')
```

---

​											

### 어디에 들어갈 수 있을까

```python

T = int(input())
for tc in range(1, T+1):
    # N: 2차원 리스트의 크기  K: 찾고 싶은 길이
    N, K = map(int, input().split())

    puzzle = [list(map(int, input().split())) for _ in range(N)]
    ans = 0

    for i in range(N):
        # 행 검사
        cnt_r = 0
        for j in range(N):
            if puzzle[i][j] == 1:
                cnt_r += 1
            else:
                # 벽이라면
                if cnt_r == K:
                    ans += 1
                cnt_r = 0
        # 끝까지 가서야 완성이 된 경우
        if cnt_r == K:
            ans += 1

        cnt_c = 0
        for j in range(N):
            if puzzle[j][i] == 1:
                cnt_c += 1
            else:
                if cnt_c == K:
                    ans += 1
                cnt_c = 0
        if cnt_c == K:
            ans += 1

    print("#{} {}".format(tc, ans))
```

---

```python

T = int(input())
for tc in range(1, T+1):
    N, K = map(int, input().split())
    arr = [list(map(int, input().split())) for _ in range(N)]
    ans = 0

    for i in range(N):                 # 가로행에 대한 검사
        check = 0
        for j in range(N):  
            if arr[i][j] == 1:         # 해당 인덱스 행렬 값이 1이면
                check += 1             # 카운팅
                if j == N-1:           # 마지막 열인 경우
                    if check == K:     # 카운팅이 단어 길이와 같으면
                        ans += 1       # 답 +1
            else:                      # 해당 인덱스 행렬 값이 0이면
                if check == K:         # 이전까지 카운팅한 값이 K인 경우
                    ans += 1           # 답 +1
                check = 0              # 카운팅 값 0 으로 초기화

    for i in range(N):                 # 세로행에 대한 검사, 가로와 방식 같음
        check = 0
        for j in range(N):
            if arr[j][i] == 1:
                check += 1
                if j == N-1:
                    if check == K:
                        ans += 1
            else:
                if check == K:
                    ans += 1
                check = 0

    print(f'#{tc} {ans}')

```

---

​											

### 의석이의 세로로 말해요

```python

T = int(input())

for tc in range(1, T+1):
    word = [0] * 5

    max_len = 0

    for i in range(5):
        word[i] = list(input())
        if len(word[i]) > max_len:
            max_len = len(word[i])

    print("#{}".format(tc), end=" ")

    for i in range(max_len):
        for j in range(5):
            if len(word[j]) > i:
                print(word[j][i], end="")
    print()

```

---

```python

T = int(input())
for tc in range(1, T+1):
    arr = [input() for _ in range(5)]
    word = ''
    for i in range(15):            # 최대 길이가 15이하인 문자열이 주어지므로 범위는 15
        for j in range(5):         # 행이 계속 5개로 돈다.
            if len(arr[j]) > i:    # 열 인덱스 값 i가 입력 문자열들의 길이를 벗어나지 않는 범위안에 있으면
                word += arr[j][i]  # 문자열 읽기

    print(f'#{tc} {word}')
```

---

​																	

### 쇠막대기 자르기

```python

T = int(input())
for tc in range(1, T+1):
    iron = input()
    cnt = 0
    stack = []                      # 쇠막대기 시작할때마다 stack에 넣고, 막대기가 끝나면 빼줌
    for i in range(len(iron)):
        x = iron[i]
        if x == "(":                # "(" 쇠막대기가 시작하므로 stack에 넣기
            stack.append(x)
        else:                       # ")" 인 경우
            if iron[i-1] == "(":    # 직전 원소가 "("이면 레이저
                stack.pop(-1)       # stack에서 하나 제거하고
                cnt += len(stack)   # 남아 있던 쇠막대기만큼 조각이 잘려서 개수 추가
            else:                   # 직전 원소가 ")"이면 쇠막대기가 끝났다는 의미이므로
                cnt += 1            # 전에 잘린 레이저 부분부터 막대기 끝까지의 조각이 하나 추가됨
                stack.pop()         # 막대기가 끝났으므로 stack에서 제거

    print(f'#{tc} {cnt}')
```

---

```python


T = int(input())

for tc in range(1, T+1):
    iron_bar = input()

    stack = []
    ans = 0

    for i in range(len(iron_bar)):
        if iron_bar[i] == "(":
            stack.append("(")
        else:
            stack.pop()
            if iron_bar[i-1] == '(':
                ans += len(stack)
            else:
                ans += 1
    print("#{} {}".format(tc, ans))
```

---

​											

### 스도쿠 검증

```python
T = int(input())

for tc in range(1, T+1):
    sdoku = [list(map(int, input().split())) for _ in range(9)]
    square = [0, 3, 6]                 # 사각형 검사를 위한 리스트
    ans = 1

    for i in range(9):                 # 가로행 검사
        x = [0] * 10                   # 카운팅을 위한 리스트 생성
        for j in range(9):
            x[sdoku[i][j]] += 1
        for k in range(1, 10):
            if x[k] != 1:              # 카운팅했을 때 1이 아니면
                ans = 0                # 답은 0이고 break 로 그만
                break
    if ans == 1:                       # 세로행 검사 (가로행 검사 통과했을 경우)
        for i in range(9):
            y = [0] * 10
            for j in range(9):
                y[sdoku[j][i]] += 1
            for k in range(1, 10):
                if y[k] != 1:
                    ans = 0
                    break
    if ans == 1:                        # 사각형 검사 (가로행과 세로행 모두 통과했을 경우)
        for i in square:
            for j in square:
                z = [0] * 10
                for k in range(3):
                    for q in range(3):
                        z[sdoku[i+k][j+q]] += 1
                for l in range(1, 10):
                    if z[l] != 1:
                        ans = 0
                        break

    print(f'#{tc} {ans}')
```

---

```python


def check():
    for i in range(9):
        # 체크를 위한
        row = [0] * 10
        col = [0] * 10

        for j in range(9):
            num_row = sudoku[i][j]  # 행 검사
            num_col = sudoku[j][i]  # 열 검사

            # 이미 사용한 숫자라면 너 멈춰
            if row[num_row]:
                return 0
            else:
                row[num_row] = 1
            if col[num_col]:
                return 0
            else:
                col[num_col] = 1


             # 3x3 검사도 해버리자
            if i % 3 == 0 and j % 3 == 0:
                square = [0] * 10
                for r in range(i,i+3):
                    for c in range(j, j+3):
                        num = sudoku[r][c]
                        if square[num]:
                            return 0
                        else:
                            square[num] = 1

    return 1

T = int(input())

for tc in range(1, T+1):
    sudoku = [list(map(int, input().split())) for _ in range(9)]

    print("#{} {}".format(tc, check()))


```

---

​													

### 숫자 배열 회전

```python
T = int(input())

for tc in range(1, T+1):
    sdoku = [list(map(int, input().split())) for _ in range(9)]
    square = [0, 3, 6]                 # 사각형 검사를 위한 리스트
    ans = 1

    for i in range(9):                 # 가로행 검사
        x = [0] * 10                   # 카운팅을 위한 리스트 생성
        for j in range(9):
            x[sdoku[i][j]] += 1
        for k in range(1, 10):
            if x[k] != 1:              # 카운팅했을 때 1이 아니면
                ans = 0                # 답은 0이고 break 로 그만
                break
    if ans == 1:                       # 세로행 검사 (가로행 검사 통과했을 경우)
        for i in range(9):
            y = [0] * 10
            for j in range(9):
                y[sdoku[j][i]] += 1
            for k in range(1, 10):
                if y[k] != 1:
                    ans = 0
                    break
    if ans == 1:                        # 사각형 검사 (가로행과 세로행 모두 통과했을 경우)
        for i in square:
            for j in square:
                z = [0] * 10
                for k in range(3):
                    for q in range(3):
                        z[sdoku[i+k][j+q]] += 1
                for l in range(1, 10):
                    if z[l] != 1:
                        ans = 0
                        break

    print(f'#{tc} {ans}')
```

---

```python

def check():
    for i in range(9):
        # 체크를 위한
        row = [0] * 10
        col = [0] * 10

        for j in range(9):
            num_row = sudoku[i][j]  # 행 검사
            num_col = sudoku[j][i]  # 열 검사

            # 이미 사용한 숫자라면 너 멈춰
            if row[num_row]:
                return 0
            else:
                row[num_row] = 1
            if col[num_col]:
                return 0
            else:
                col[num_col] = 1


             # 3x3 검사도 해버리자
            if i % 3 == 0 and j % 3 == 0:
                square = [0] * 10
                for r in range(i,i+3):
                    for c in range(j, j+3):
                        num = sudoku[r][c]
                        if square[num]:
                            return 0
                        else:
                            square[num] = 1

    return 1

T = int(input())

for tc in range(1, T+1):
    sudoku = [list(map(int, input().split())) for _ in range(9)]

    print("#{} {}".format(tc, check()))


```

---



