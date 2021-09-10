# :boom: Django

---



#### Form의 역할

- 데이터의 유효성 검사

- HTML (<input>) 생성

  ​															

#### 더욱 튼튼하게 method 제한두기

from django.views.decorators.http import require_safe, require_POST, require_http_methods

@require_safe

@require_http_methods(['GET','POST'])

​													

#### Model 응용

​	CATEGORY_CHOICES = [

​	('python', '파이썬'),  # (앞에가 저장되는 값, 사용자가 보게될 값)

​	('python', '파이썬'),

​	('python', '파이썬'),

]

(max_length=20, choices = CATEGORY_CHOICES)

{{ question.get_category_display }}  사용자가 보게될 값 변수

​																	

#### Form 응용																			

```python
class QuestionForm(forms.ModelForm):
    # model의 필드와 이름이 같다면, DB에 저장이 된다.
    title = forms.CharField(
    	min_length=2,
        max_length=100,
        required=True
    )
    content = forms.CharField(
    	widget = Textarea,
        required= True,
        min_length=2,
        max_length=10000
    )
    # model 의 필드가 아니면, HTML + 검증은 하되 저장은 하지않는다.
    is_save = forms.BooleanField(required=False, lable='wanna save?', help_text='저장하려면 체크하세요.')
    
    
    class Meta:
        model = Question
        # 아래 필드들은, 모델에 있어야 하며, 데이터 검증 + HTML 생성을 합니다.
        fields = ('title', ' category', 'content' )   # 순서도 중요
       	exclude = ('field_a', 'field_b')  # 100개중에 이거 두개만 안쓸경우
```

​														

```python
 if form.is_valid(): 
    if form.cleaned_data['is_save']:
        question = form.save()
        return redirect('board:detail', question.pk)
    else:
        return redirect('board:create')
```

​																																										

pip install django-bootstrap-v5

settings.py에 추가 'bootstrap5'       # 우리 대신에 태그 만들어주는 게 얘의 역할

맨 위에 {% load bootstrap5 %}

{% bootstrap css %}  # 이게 결국 그냥 cdn 가져온거임

{% bootstrap javascript %}

​																												

CDN 서버가 터져도 우리꺼는 문제가 발생하지 않도록.

Compiled CSS and JS

우리가 CSS 이런 걸 직접 가지고 있어야 함.

​														

STATICFILES_DIRS = [BASE_DIR/ 'static'] 

- static 파일 찾을 때, 여기도 같이 찾아주세요.  폴더 레벨에 static폴더 만들때 

  ​												

static 폴더를 만들 때 고려해야 돼 어느레벨에 만들지.  +) namespace 막기위해 static 안에 앱폴더하나더 권장

ex) base에 필효한 경우 프로젝트 레벨이 좋겠지.

{% load static %}

link rel~~~ href="{% static 'css/bootstrap.min.css' %}"

{% static 'js/bootstrap.min.js' %}

​																

navbar 코딩 부분만 따로 navbar.html 새로 만들어서 저장한 후

base.html 에  {% include 'navbar.html' %}

​																													

### index paginator

```python
from django.core.paginator import Paginator
from django.shortcuts import render

from myapp.models import Contact

def index(request):
    questions = Question.objects.order_by('-pk')
    paginator = Paginator(questions, 2) # Show 25 contacts per page.

    page_number = request.GET.get('page')
    page_obj = paginator.get_page(page_number)
    
    context = {
        'page_obj' : page_obj,
    }

# index 페이지에서 
{% for question in page_obj %}

div.d-flex-justify-content-center

{% bootstrap_pagination page_obj %}
```











