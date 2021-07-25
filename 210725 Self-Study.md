# :boom: Self STUDY



### 가위바위보!!



```python

import random

choices = ["가위","바위","보"]
player = input("가위, 바위, 보 중에 선택하세요.")
while player != "quit":
    computer = random.choice(choices)
    print(computer)
    if player == computer:
        print("draw")
    elif player =="바위":
        if computer == "가위":
            print("win")
        else:
            print("lose")
    elif player =="보":
        if computer == "바위":
            print("win")
        else:
            print("lose")
    elif player =="가위":
        if computer =="보":
            print("win")
        else:
            print("lose")
    else:
        print("Error")
    print()
    player = input("다시 선택 or quit")

```

