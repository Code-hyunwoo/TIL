# :boom: API

---



DRF API server 제작



제일 먼저 해야하는 것.

우리가 만들고자 하는 모델링.

프로젝트를 시작할 때, 무작정 시작하는게 아니라 전체적인 그림을 생각해보자.



python -m venv venv

source venv/Scripts/activate

pip install django django_extensions djangorestframework

django-admin startproject live08 .

python manage.py startapp jukebox



settings.py에서 installed_apps에 등록

jukebox

django_extensions

rest_framework



juke > models.py 에서 모델링 시작

​													
