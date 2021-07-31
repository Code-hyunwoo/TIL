# :boom: Project review

---

​																					

## problem.a

```python
def popular_count():
    """popular 영화목록의 개수 출력.

    TMDB API 서버에 요청을 보내고 
    응답 결과에서 인기 영화목록의 개수를 반환합니다.

    Returns:
        popular 영화목록의 개수를 반환합니다.
    """

    tmdb_helper = TMDBHelper('496da14443480bfbd854ad2cf1a22692')
    url = tmdb_helper.get_request_url(language='ko', region='KR')
    data = requests.get(url).json()
    
    #영화 목록 받아옴
    movies = data['results']
    
    #영화 목록의 개수 반환
    return len(movies)
```

​															

## problem.b

```python
def vote_average_movies():
    """popular 영화목록중 vote_average가 8 이상인 영화목록 출력.

    TMDB API 서버에 요청을 보내고 
    응답 결과인 인기 영화목록 중 vote_average가 8 이상인 영화 목록을 리스트로 반환합니다.

    Returns:
        popular 영화목록의 개수를 반환합니다.
    """
    tmdb_helper = TMDBHelper('496da14443480bfbd854ad2cf1a22692')
    url = tmdb_helper.get_request_url(language='ko', region='KR')
    data = requests.get(url).json()
    
    #영화 목록을 받아오고, 평점이 8 이상인 영화들을 저장할 리스트 생성
    movies = data['results']
    movies_over_8 = []

    #영화 목록에서 평점이 8이상인 경우를 찾아 앞서 생성한 리스트에 추가 후 반환
    for movie in movies:
        if movie['vote_average'] >= 8:
            movies_over_8.append(movie)

    return movies_over_8

```

​															

## problem.c

```python
def ranking():
    """popular 영화목록을 정렬하여 평점순으로 5개 출력.

    TMDB API 서버에 요청을 보내고 
    응답 결과인 인기 영화목록을 정렬하고, 상위 5개 영화의 정보를 리스트로 반환합니다

    Returns:
        받아온 데이터 중 평점이 높은 영화 다섯 편의 정보를 리스트로 반환합니다.
    """
    tmdb_helper = TMDBHelper('496da14443480bfbd854ad2cf1a22692')
    url = tmdb_helper.get_request_url(language='ko', region='KR')
    data = requests.get(url).json()

    #영화목록을 받아오고, vote_average를 기준으로 정렬
    #평점 상위 5개 영화를 리스트로 반환
    movies = data['results']
    movies.sort(key = lambda x: x['vote_average'], reverse=True)
    return movies[:5]
```

​														

## problem.d

```python
def recommendation(title):
    """추천 영화 목록 출력

    제목에 해당하는 영화가 있으면
    해당 영화의 id를 기반으로 추천 영화 목록을 출력.
    추천 영화가 없을 경우 [] 출력.
    영화 id검색에 실패할 경우 None 출력.

    Args:
            title: 영화 제목.
        
    Returns:
        추천 영화 목록을 반환합니다.
        id값은 존재하지만 추천영화가 없는 경우 빈 리스트로 반환합니다.
        단, id가 없을 경우 None을 반환합니다.
    """
    tmdb_helper = TMDBHelper('496da14443480bfbd854ad2cf1a22692')
    movie_id = tmdb_helper.get_movie_id(title)

    #id가 존재하는 경우
    if movie_id:
        url = tmdb_helper.get_request_url(f'/movie/{movie_id}/recommendations',language='ko')
        data = requests.get(url).json()
        results = data.get('results')
        
        #추천목록이 존재하는 경우
        #추천목록에서 영화의 title만 따로 뽑아 리스트로 반환
        if results:
            recommendations = []
            for movie in results:
                recommendations.append(movie['title'])
            return recommendations
        #추천목록이 없는 경우, 빈 리스트로 반환
        else:
            return []
    #id가 존재하지 않는 경우
    else:
        return None
```

​																

## problem.e

```python
def credits(title):
    """영화 출연진 출력

    제목에 해당하는 영화가 있으면
    해당 영화 id를 통해 영화 상세정보를 검색하여
    주연배우 목록과 목록을 출력.
    영화 id검색에 실패할 경우 None 출력.

    Args:
            title: 영화 제목.
        
    Returns:
        영화에 출연한 배우들과 제작진의 정보를 딕셔너리로 반환합니다.
        단, id가 없을 경우 None을 반환합니다.
    """
    tmdb_helper = TMDBHelper('496da14443480bfbd854ad2cf1a22692')
    movie_id = tmdb_helper.get_movie_id(title)
    
    #id가 존재하는 경우
    if movie_id:
        url = tmdb_helper.get_request_url(f'/movie/{movie_id}/credits',language='ko')
        data = requests.get(url).json()
        #받아온 데이터에서 casts, crews 정보를 따로 저장
        casts = data.get('cast')
        crews = data.get('crew')

        #조건에 따라 분류한 결과를 저장할 딕셔너리를 초기화
        credits_dic = {'cast': [], 'crew': []}

        #제작진 중 감독인 경우를 찾아 'crew'쪽 value에 추가
        for crew in crews:
            if crew['department'] == 'Directing':
                credits_dic['crew'].append(crew['name'])
        #출연한 배우 중 'cast_id'가 10보다 작은 경우 'cast'쪽 value에 추가
        for cast in casts:
            if cast['cast_id'] < 10:
                credits_dic['cast'].append(cast['name'])
        
        return credits_dic
    #id가 존재하지 않는 경우
    else:
        return None
```

