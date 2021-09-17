# :boom: Git branch

---

​										

### Git branch

​																																			

```python
touch README.md .gitignore

git init
# 바로 master branch가 생성됨

git add .

git commit -m"first_commit"
# first commit(root commit)은 중요하기 때문에 시작하면 무조건 해두는 게 좋다.
# 이게 있어야 branch든 뭐든 할 수 있음.

# branch 는 단순한 포인터(화살표)다.
# HEAD 도 단순한 포인터다. (포인터의 포인터인 경우가 많다.)
# HEAD 는 현재 내가 작업중인 커밋을 의미한다.
# HEAD 가 master에 있다. == 현재 master에서 작업 중이다.

```

#### 																											

#### master branch의 의미와 역할

- 통합 브랜치
  언제든지 배포할 수 있는 버전을 만들 수 있어야 하는 브랜치
  모든 기능이 정상적으로 동작하는 상태

  ​																				

```python
# git branch <name>
#branch b1 생성
git branch b1   
# master가 가리키고 있던 commit에서 branch가 생성됨

git log --oneline
# 확인해보기

git switch b1
# HEAD를 b1으로 이동
# 여기서 작업을 함 여기서, 작업은 commit이 기준
# commit이 중요하다.
touch secret.txt

git switch master
# 이러면 touch secret.txt가 b1에서 생성했어도, master에서 보인다.
# 왜냐하면 b1에서 생성했으나 commit하지 않았기 때문에 secret 파일은 현재 소속이 없음

git switch b1
git add .
git commit -m"new"

git switch master
#이러면 secret.txt는 보이지 않음.

#commit은 자신의 부모를 굉장히 잘 알고 있음.
```

​																														

#### Merge

```python
# 큰 개념, 큰 branch (보통 master)에서 작업
git merge b1
# master가 b1에 있는 내용을 다 흡수하겠다!
# fast-forward 병합의 첫 번째 시나리오. 단순하게 앞에 나있던 길을 그대로 가는 느낌

git branch
# 현재 있는 모든 branch 목록을 보여주는 명령어

git branch b2
git switch b2
touch b2.txt
git add .
git commit -m '6'

# b2.txt에서 추가 작업 후
git add .
git commit -m '7'

git switch master
#master에서 작업하는데 추가 작업을 하게되는 경우/ 양갈래로 나누어지기 시작
touch master.txt
git add .
git commit -m '8'

#master.txt 에서 작업 후
git add .
git commit -m '9'

# 양갈래에서 10번 커밋으로 합쳐야 할듯 master branch에서 !

git merge b2
# b2에서 실수로 한 경우, master를 b2로 이동 시키기
# commit이란 말을 안했는데 merge했는데 commit이 생김. 왜냐? 지금은 이 방법밖에 답이 없음 commit
# 이런 방법이 두 번째 병합 시나리오. Auto Merge

git log --oneline --graph

git switch -c b3
# 브랜치를 새로 만들면서 스위치까지 하는 명령어

touch b3.txt
git add .
git commit -m '11'
# b3.txt에서 작업하고
# secret.txt를 작업 b3 브랜치에서
git add .
git commit -m '12'

git switch master
# master.txt를 또 작업하고 
git add . 
git commit -m '13'

# secret.txt를 작업 master branch에서
git add .
git commit -m '14'

git merge b3
# 이러면 b3, master에서 각각 작업한 secret.txt가 충돌일어남. automatic merge failed
# master|MERGING  합쳐지는 중으로 나옴 아직 안끝났다. b3 사라지고..
# 이게 떴다는 건, 이것부터 해결하라는 의미 다른거 작업하지말고.
# 충돌난 secret.txt 파일로 가보면, 파일이 조금 수정되어있음. 직접 수정하고 저장해야됨.
# 또는 위에 뜬 거 클릭해서 수정도 가능.

git add .

git commit -m'15'
# 이게 세번째 시나리오 conflict 상황 (manual merge)


# master에 통합되었다는 건 그 이전 branch 작업들은 문제가 없다는 것을 의미.
# 즉, 합치기 직전이 중요. 확인 검사 작업 필요.
# 그래서 합치고 나면 이전의 branch들은 삭제해 주는 게 좋음

```

​																														

### 협업

```python
#같이 작업하게 되면 remote가 더 중요함.

새로운 remote repository를 생성  'collabo'
readme.md 나오게 체크하고 생성 - root commit 역할
# remote에서 첫번째 커밋이 발생.
# 설정 - 저장소 - Ptotected branches // master branch에 push를 특정한 사람만 할 수 있게 설정

# 팀원A, B가 클론을 각각 받음
git clone copy한 주소 내용~~ collabo_A
git clone copy 주소~ collabo_B # 폴더이름임

cd collabo_A
cd collabo_B

git switch -c dev-a
git switch -c dev-b

각각 브랜치에서 commit하면서 작업한 경우
git push origin dev-a
git push origin dev-b

# 협업에서 remote가 내용물이 가장 많음

머지리퀘스트 만들기
제목, 내용 작성.
병합해달라고 요청할 건데 누구한테 할 것인가. 설정하고
머지 리퀘스트 만들기 누름
최종적으로 merge 버튼을 누름


A, B는 어떻게 이어받아서 작업을 하는가.
A: git switch master
   git pull origin master
B: git switch master
   git pull origin master


# branch 지우는 법
git branch -d dev-a
git branch -d dev-b
```

