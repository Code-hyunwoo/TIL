# :boom: Requests & Response

---

​												

#### 가장 대표적인 클라이언트 프로그램

브라우저.   브라우저를 통해 우리는 항상 요청을 보내고 있다.

​													

#### 가장 대표적인 서버 프로그램

네이버 구글같은 모든 웹 서비스

​																								

### 크롤링

​		**requests**

​	pip install requests

HTML의 존재 이유 == 브라우저를 통해 보여주기 위해 

requests의 역할은 HTML을 받아오는 것 까지, 원하는 대로 사용하기 위해 추가적 작업 필요

​																												

​	**Beautiful  Soup**

HTML에서 데이터를 뽑아 주는 애.

**설치**  pip install beautifulsoup4

​																									

```python
import requests
from bs4 import BeautifulSoup

# 요청을 보낼 URL 또는 재료
url = 'https://finance.naver.com/sise/'

# 실제 요청을 보내고, 응답 객체를 response 변수에 저장
response = requests.get(url)

# 응답 객체의 본문(text)을 해석하여 data 변수에 저장
data = BeautifulSoup(response.text, 'html.parser') #html을 parser 장치를 통해 해석해 보자!

# 해석한 data에서 원하는 정보를 선택하고, 내용만 Kospi에 저장
kospi = data.select_one('#KOSPI_now').text
# 원하는거 copy selector / 그 중에서도 본문 .text

print(kospi)
```

​																																									

​	**크롤링의 단점**

1.  브라우저가 아닌 상황에서 필요없는 데이터가 너무 많음
2. 원하는 데이터를 얻기 위한 추가작업 

   ​																			

-  핵심 데이터만 받을 수는 없을까?
- 원하는 데이터를 쉽게 접근할 수 는 없을까?

  ​																			

### API

응용 프로그램을 위한 접점 

​																													

### API Server

응용 프로그램(개발자)를 위한 데이터를 응답하는 프로그램







