# :boom: JavaScript

---



### 변수와 식별자

- 변수는 반드시 문자, 달러$ 밑줄로 시작

- 대소문자를 구분하며, 클래스명 외에는 모두 소문자로 시작
- 예약어 사용 불가능



​	식별자 스타일

카멜 케이스 : 두 번째 단어의 첫글자부터 대문자

파스칼케이스: 모든 단어의 첫 번째 글자를 대문자로 작성

스네이크 케이스: 모든 단어 대문자 & 단어 사이에 언더 스코어 삽입



변수 선언 키워드

**const**: 재할당 할 수 없는 변수 선언 시 사용 / 변수 재선언 불가능(덮어쓰기가 안된다는 뜻)

**let**: 재할당 할 수 있는 변수 선언 시 사용/ 변수 재선언 불가능

* 크롬 80버전부터는 재할당이 가능하도록 만들었다. 크롬만 되는 것. 불편하니까!

**var**: 재선언 및 재할당 모두 가능 but 호이스팅 되는 특성으로 인해 예기치 못한 문제 발생 가능

**스코프 바깥에서 스코프 안에 접근 불가능**

​																																					

### 타입과 연산자

자바스크립트의 모든 값은 특정한 데이터 타입을 가짐

크게 원시타입(Primitive type)과 참조타입(Reference type)으로 분류됨



**원시 타입(Primitive type)**

- Number, String, Boolean, undefined,  null, Symbol
- 객체가 아닌 기본 타입
- 변수에 해당 타입의 값이 담김
- 다른 변수에 복사할 때 실제 값이 복사됨
- 연동이 안됨



**참조타입(Reference type)**

- Array, Function ...

- 객체 타입 자료형

- 변수에 해당 객체의 참조 값이 담김

- 다른 변수에 복사할 때 참조 값이 복사됨

  ​																									

  ​																													

### 조건문과 반복문

​																																			

**if** **문**

```javascript
const username = '이현우'

if (username =='admin') {
  console.log('관리자님 환영합니다 ')
} else if (username =='manager') {
  console.log('매니저님 환영합니다.')
} else {
  console.log(`${username}님 환영합니다.`)
}
```

​																										

**switch statement**

```javascript
const numOne = 10
const numTwo = 100
const operator = '*'

switch(operator) {
  case '+': {
    console.log(numOne + numTwo)
    break
  }
  case '-': {
    console.log(numOne - numTwo)
    break
  }
  case '*': {
    console.log(numOne * numTwo)
    break
  }
  case '/': {
    console.log(numOne / numTwo)
    break
  }
  default: {
    console.log('유효하지 않은 연산자입니다.')
    break
  }
}
```

​																			

**while**

```javascript
let i = 0
while (i < 6){
    console.log(i) 
    i += 1
}

let evenNumber = 0
while (evenNumber < 6) {
  console.log(evenNumber)
  evenNumber += 2
}
```

​													

**for**

```javascript
for (let i = 0; i < 6; i++){
    console.log(i)   // 0부터 출력된다는거 주의 0, 1, 2, 3, 4, 5
}

for (let oddNumber = 1; oddNumber < 5; oddNumber +=2){
  console.log(oddNumber)
}
```

​												

**for in**

```javascript
const bestMovie = {
  title: '벤자민 버튼의 시간은 거꾸로 간다',
  releaseYear: 2008,
  actors: ['브래드 피트', '케이트 블란쳇'],
  genres: ['romance', 'fantasy'],
}
for (let movie in bestMovie){
  console.log(`${movie}: ${bestMovie[movie]}`)
}
```

​																				

**for of**

```javascript
const movies = [
  {title: '어바웃 타임'},
  {title: '굿 윌 헌팅'},
  {title: '인턴'},
]

for (let movie of movies){
  console.log(`title: ${movie.title}`)
}
```

​																							

### 함수

JavaScript의 함수는 일급 객체에 해당

일급객체의 조건

- 변수에 할당가능

- 함수의 매개변수로 전달 가능

- 함수의 반환 값으로 사용 가능

  ​																

**함수 선언식**

```javascript
function isValid(password) {
	if (password.length >= 8) {
		return true
	} else {
		return false
	}
}
isValid('abcd')

function isValid(password){
	return password.length >= 8
}
```

​																							

**함수 표현식**

```javascript
const join = function(array, separator) {
	return array.join(separator)
	}
join(['010', '1234', '5678'], '-')

const join = function(array, separator){
	let result = ''
	for (let idx = 0; idx < array.length; idx++){
		const word = array[idx]
		result += word
		if (idx < array.length -1){
			result += separator
		}
	}
	return result
}
join(['010', '1234', '5678'], '-')
```

​																											

**함수 기본인자**

```javascript
const makeOrder = function(menu, size = 'regular') {
	console.log(`{menu:'${menu}', size:'${size}' }`)
}
makeOrder('mocha')
```

​																	

**화살표 함수**

```javascript
const celsiusToFahrenheit = function (celsius) {
    const fahrenheit = celsius * 9/5 + 32
    return fahrenheit
}

const celsiusToFahrenheit = (celsius) => celsius * 9/5 + 32

const celsiusToFahrenheit = celsius => celsius * 9/5 + 32
```

​																															

​																																

### 배열과 객체

​												

**새로운 배열 만들기**

```javascript
const homeworks = ['david.zip', null, 'maria.zip', 'tom.zip', null]

const results = []
for (const homework of homeworks){
	if (homework) {
		results.push(homework)
	}
}
console.log(results)


arr.splice(2,0, 'd')
index 2의 위치에 'd' 추가
arr.splice(4,0,'e','f')
index 4의 위치에 2개의 요소를 추가
arr.splice(1, 2);
index 1부터 2개의 요소를 제거
arr.splice(2, 1):
index 2부터 1개의 요소를 제거
```

​																			

**문자열 합치기**

```javascript
const arr1 = ['www', 'samsung', 'com']
const arr2 = ['galaxy', 'buds', 'pro']
const arr3 = ['sec', 'buds']
let homepage = arr1.join('.')
let product = arr2.join('-')

arr3.unshift(homepage)
arr3.push(product)
const result = arr3.join('/')
console.log(result)
```

​																						

**인덱스로 값 교환하기**

```javascript
const weather = ['sunny', 'sunny', 'sunny', 'sunny', 'rainy', 'rainy', 'sunny']

result = weather.indexOf('rainy')
while (result != -1){
	weather[result] = 'sunny'
	result = weather.indexOf('rainy')
}

console.log(weather)
```

​																	

**MAP**

```javascript
const trips = [
  { distance: 34, time: 10 },
  { distance: 90, time: 50 },
  { distance: 59, time: 25 },
]

const speeds = trips.map((num) => {
  return num.distance/num.time
})

console.log(speeds)
```

​																			

**filter**

```javascript
const languages = ['python', 'javascript', 'html', 'java']
const query = 'java'

const java_language = languages.filter((language) => {
  return language.includes(query)
})

console.log(java_language)
```

​																			



**reduce**

```javascript
const scores = [
  { name: 'smith', score: 90 },
  { name: 'peter', score: 80 },
  { name: 'anna', score: 85 },
]

const new_scores = scores.reduce((acc, score) => {
  acc[score.name] = score.score
  return acc
}, {})

console.log(new_scores)
```

​																			

**find**

```javascript
const accounts = [
	{ name: 'justin', balance: 1200 },
	{ name: 'harry', balance: 50000 },
	{ name: 'jason', balance: 24000 },
]

const result = accounts.find((account) => {
  return account.balance === 24000
})
console.log(result)
```

​																				

**some**

```javascript
const requests = [
  { url: '/photos', status: 'complete' },
  { url: '/albums', status: 'pending' },
  { url: '/users', status: 'failed' },
]

const haspending = requests.some((request) => {
  return request.status === 'pending'
})
console.log(haspending)
```

​																												

**every**

```javascript
const isEveryuserSubmitted = users.every((user) => {
  return user.status === 'submmited'
})
console.log(isEveryuserSubmitted)
```

​																							

​													

**object 축약 문법**

```javascript
const username = 'hailey'
const contact = '010-1234-5678'

const user = {
  username,
  contact,
}
```

​																		

​																																		

**object Destructuring**

```javascript
const users = [
  {
    name: 'hailey',
    contact: '010-1234-5678',
  },
  {
    name: 'paul',
    contact: '010-5678-1234',
  },
]

function saveUserData (users) {
  const userData = users.map((user, index) => {
    return { id: index, name: user.name, contact: user.contact }
  })

  return userData
}


function saveUserData (users) {
  return users.map(({ name, contact }, index) => ({
    id: index,
    name,
    contact,
  })
)}

console.log(saveUserData(users))
```

​				

