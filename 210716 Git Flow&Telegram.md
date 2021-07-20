## :boom:	텔레그램 챗봇 만들기

​			  

### 텔레그램 봇 API 활용하기

---

​		  

​		텔레그램에서 Botfather 검색

​		START

​		/new bot

​		Bot name 입력

​		Bot username (반드시 Bot으로 끝나야 함)

​		Bot token 기록

- ​	**getMe 메서드** 
  https://api.telegram.org/bot<token>/getMe

- ​	**getUpdates 메서드** 
  https://api.telegram.org/bot<token>/getUpdates

- ​	**sendMessage 메서드** 
  https://api.telegram.org/bot<token>/sendMessage?chat id=<id>&text=<채팅내용>

  ​	  



---

### :smile:	Python으로 텔레그램 메세지 보내기

---

​		  

- **텔레그램 메세지 보내기**

```python
import requests
from requests.models import Response
# 기본 설정
TOKEN = "1801797013:AAGr5nX8oj3NXJw7zGn6YmJfH0d0VRSIxuA"
APP_URL = f"https://api.telegram.org/bot{TOKEN}"

#chat_id 가져오기
#https://api.telegram.org/bot1801797013:AAGr5nX8oj3NXJw7zGn6YmJfH0d0VRSIxuA/getUpdates

UPDATES_URL = f"{APP_URL}/getupdates"
Response = requests.get(UPDATES_URL).json()

chat_id = Response.get("result")[0].get("message").get("chat").get("id")
print(chat_id)

text = "파이썬으로 보낸 메세지입니다."

message_url = f"{APP_URL}/sendMessage?chat_id={chat_id}&text={text}"
requests.get(message_url)
```



​		   

- **네이버 최저가 검색 코딩**

```python
import requests

# naver 요청 보낼 때 필요한 것들, 네이버 API 등록사이트에서 저장
naver_client_id = "fxd2iXN9vvhr1LFkQ0_P"
naver_client_secret = "zy3Sa4nNTz"
URL = "https://openapi.naver.com/v1/search/shop.json?query="

headers = {
        "X-Naver-Client-Id": naver_client_id,
        "X-Naver-Client-Secret": naver_client_secret}

query = "ps5"

product = requests.get(URL+query, headers=headers).json()["items"][0]
print(product)

product_name = product["title"]
print(product_name)
product_price = product["lprice"]
print(product_price)
product_link = product["link"]
print(product_link)
#\n 은 줄바꿈해줌
message = f"{product_name}\n{product_price}\n{product_link}"
print(message)
```

​		  

- **네이버 최저가 검색 + 텔레그램 메세지 보내기**

```python
import requests
from requests.models import Response

# 기본 설정  
# 1801797013:AAGr5nX8oj3NXJw7zGn6YmJfH0d0VRSIxuA 내 토큰 번호
TOKEN = "1883623049:AAFvgetUZYEM6Zi4hb_inUH_hB7OaEfjMcw"
APP_URL = f"https://api.telegram.org/bot{TOKEN}"

#chat_id 가져오기
#f = 변화값이 있는 변수 지정할때, format
#https://api.telegram.org/bot1801797013:AAGr5nX8oj3NXJw7zGn6YmJfH0d0VRSIxuA/getUpdates

UPDATES_URL = f"{APP_URL}/getupdates"
Response = requests.get(UPDATES_URL).json()

chat_id = Response.get("result")[0].get("message").get("chat").get("id")
print(chat_id)

need_to_search = Response.get("result")[-1].get("message").get("text")
print(need_to_search)

# naver 요청 보낼 때 필요한 것들, 네이버 API 등록사이트에서 저장
naver_client_id = "fxd2iXN9vvhr1LFkQ0_P"
naver_client_secret = "zy3Sa4nNTz"
URL = "https://openapi.naver.com/v1/search/shop.json?query="

headers = {
        "X-Naver-Client-Id": naver_client_id,
        "X-Naver-Client-Secret": naver_client_secret}

query = need_to_search

product = requests.get(URL+query, headers=headers).json()["items"][0]
print(product)

product_name = product["title"]
print(product_name)
product_price = product["lprice"]
print(product_price)
product_link = product["link"]
print(product_link)
#\n 은 줄바꿈해줌
message = f"{product_name}\n{product_price}\n{product_link}"
print(message)

text = message

message_url = f"{APP_URL}/sendMessage?chat_id={chat_id}&text={text}"

requests.get(message_url)

```



---

## :boom: 	Git flow

---



### **Git flow**

> git을 활용하여 협업하는 흐름으로 branch를 활용하는 전략



### **branch** 

> 작업공간, 버전 같은 느낌

- Master = 배포 가능한 상태의 코드

- Develop = 신기능 개발,

- feature branches = 기능별 개발 브랜치

- release branches = bug fix 같이 수정



​		  

### **Branch basic commands**

​		 

- 생성 - git branch {branch name}
- 이동 - git checkout {branch name}
- 목록 - git branch
- 삭제 - gir branch -d {branch name}



​		  

### Branch merge

>각 branch에서 작업을 한 이후 이력을 합치기 위해 merge 사용
>
>충돌(conflict)이 발생할 경우 직접 수정해야 함

​		  

### Merge의 3가지 경우

​		  

- **fast-forward**

  -  특정 branch로 이동 후 commit, master 별도 변경 없이 빠르게 병합 가능
  - 버스, 혼자 다 하는 경우

- **섞어서 일하는 경우 (평화)**

  - 각 branch가 합쳐지면서 history(기록)이 남는다. 
  - esc , :wq하면 합쳐짐

- **소통이 전혀 안되는 경우**

  ​	       

    **`git merge {branch name}`**

  ### 	**fast-forward**

```
git branch hyun
git checkout hyun
git add .
git commit -m "update"
git log --oneline    #commit과 branch 확인
git choeckout master
git merge hyun
git branch -d hyun  # 무쓸모 branch 삭제
```



### 	  나누어서 일한 경우 Merge

```
git branch login
git checkout login  
touch login.txt
git add .
git commit -m "login개발"
git log --oneline
git checkout master
touch master.txt
git add .
git commit -m "master개발"
git merge login 
ESC + :WQ
git log --oneline
```

###  	소통이 안되어 중복 작업한 경우

```
#master에서 login.txt 수정
git add .
git commit -m "master에서 login수정"
git checkout login
#login에서 login.txt 수정
git add .
git commit -m "login에서 login수정"
git checkout master
git merge login
#중복 수정된 부분 conflict 발생, 직접 수정해야 함.
git add .
git commit 
```

​		  



​		합쳐서 쓸모없는 브랜치는 작업 후 삭제하기.

​		HEAD가 가르키는 commit에 따라서 Git이 변한다.

​		HEAD란 포인터 가르키는 존재.  

​		HEAD가  MASTER branch를 가르키면 마스터 브랜치가 나옴

​		rebase 는 권장하지 않음



### :smile:	Github Flow 기본원칙

​		  

1. master branch는 반드시 배포 가능한 상태여야 한다.

2. feature branch는 각 기능의 의도를 알 수 있도록 작성한다.

3. Commit message는 매우 중요하며, 명확하게 작성한다.

4. Pull Request를 통해 협업을 진행한다.

5. 변경사항을 반영하고 싶다면, master branch에 병합한다.

   ​	  				   



---

## :boom:	Github flow models 협업

---



- ### Shared Repositoty Model

  - 공동창업

- ### Fork & Pull Model 

  -  오픈소스 주인이 있음(모든권한)

       

    ### :heart:	Shared Repositoty Model

팀장:  repository owner

팀원:  collaborator

팀장이 팀원초대 collaborator에 등록되야 push 권한이 부여된다.

  		  

### 	작업흐름  

 1. **팀장이 Repositoty 생성**

 2. ```python
    git init
    touch word_game.txt
    git add .
    git commit -m "1번"
    git remote add origin https://github.com/Code-hyunwoo/word-game-2.git
    git push
    git push --set-upstream origin master
    ```

 3. **초대받은 팀원이 클론하면서 시작**

            ```
            #빈폴더에서
            git clone https://github.com/Hyeonssss/word_game.git .
            #내용 수정후
            git add .
            git commit -m "2번"
            git push
            ```

4. **다시 팀장이 수정후 팀원이 pull하여 수정**

   ```
   #master에서
   git pull https://github.com/hyeonsss/word_game.git     #clone할땐 띄고 .인데 pull은 .안씀
   git branch game_upgrade
   git checkout game_upgrade
   #수정 후
   git add .
   git commit -m "4번"
   git push
   git push --set-upstream origin game_upgrade
   ```





​		   



---

## :boom:	Git reset

---



> 타임머신을 타고 우리가 원하는 버전(시점)으로 이동

​		  

- ### --soft 

  거의 안변하고 git status만 변한다..
  돌아가려는 커밋으로 되돌아가고, 
  이후의 commit된 파일들을 **staging area**로 돌려놓음	

    

- ### --mixed 

  git reset 하고 아무것도 안붙이면 기본적으로 mixed

  돌아가려는 커밋으로 되돌아가고, 
  이후의 commit된 파일들을 working directory로 돌려놓음 (add 하기전 상태)

    

- ### --hard  

  돌아가려는 커밋으로 되돌아가고,
  이후의 commit된 파일들은 모두 working directory에서 삭제

  ​	   



​		  

### :smile: 	Reset 예시

​		  

### 		soft

``` 
git log --oneline
a48c71b (HEAD - master) day3
80e09d0 day2
8af9cd7 day1

git reset --soft 80e0
git status  # day3.txt이 statging area로 감 new file: day3.txt
```

​		  		

### 		hard

``` 
git log --oneline
26df834 (HEAD -> master) day4
0c3f902 day3
80e09d0 day2
8af9cd7 day1

git reset --hard 80e0
git log --oneline  
80e09d0 (HEAD -> master) day2
8af9cd7 day1
git reset --hard 26df
git log --oneline
26df834 (HEAD -> master) day4
0c3f902 day3
80e09d0 day2
8af9cd7 day1
```

​		  

### 		mixed

``` 
git log --oneline
39c02b7 (HEAD -> master) day5
26df834 day4
0c3f902 day3
80e09d0 day2
8af9cd7 day1

git reset --mixed 0c3f902
git status
# day3.txt는 add하기 전 상태(수정된상태)
  day4,day5는 untracked 파일로 인식
git add . 
git commit -m "day4"
```

​		  

### Git reflog 

> 지금까지 HEAD가 가르켰던 commit 아이디가 모두 나온다.

​		  

### Git revert

> 다른 사람과 공유하는 브랜치에서 이전 커밋을 수정하고 싶을 때 사용
>
> 커밋 히스토리가 바뀌지 않기 때문에 충돌이 발생하지 않음
>
> git reset을 사용하여 remote 레포지토리에 push 할 수 없을 때 사용



**cf)  git push -f    << 강제로 push밀어내는 방법**

​		  

### :smile:	잘못된 브랜치에서 잘못된 작업을 한 경우 

​		  

1. git stash    임시 저장소에 잠시 저장
2. git checkout login  브랜치를 옮겨서 
3. git stash apply   저장했던거 다시 붙이기~!



