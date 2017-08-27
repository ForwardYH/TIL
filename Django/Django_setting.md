# Django

* Django란 무엇인가?
> Django는 파이썬으로 만들어진 무료 오픈소스 Web application framework이다.
쉽고 빠르게 웹사이트를 개발할 수 있도록 돕는 구성요소로 이루어진 웹 프레임워크

* 왜 프레임워크가 필요한가?
> 편지(request, 요청)가 도착했는지 확인해주는 메일박스(port, 포트)가 있다고 상상해보자.
이것은 웹 서버가 해주는 일이다. 웹 서버는 받은 편지를 읽고 웹 페이지와 함께 답장을 준다.
그런데 무언가를 주고 싶을 때는 그 안에 내용이 있어야 한다. 장고는 그 특정 컨텐츠를
만들 수 있는 역할을 한다.

# Django Install (Windows, miniconda3 기준)

- python 3.5버전을 사용하는 가상환경을 만들어주기.

  ```conda create -n Django python=3.5```
- pip가 최신버전인지 확인

  ```conda update pip or pip install --upgrade pip```
  
- 그런 다음 Django 설치

  ```pip install django~=1.10.0```


# 나의 첫 번째 Django 프로젝트!
  - 현재 디렉토리에서 mysite 디렉토리에 프로젝트 생성

  ```django-admin startproject mysite```

  - ```manage.py```는 스크립트이고, 사이트 관리를 도와주는 역할을 한다.
  - ```settings.py```는 웹사이트 설정이 있는 파일
  - ```urls.py```는 ```urlresolver```가 사용하는 패턴 목록을 포함하고 있음.

  ## 설정 변경
  - settings.py를 열어서 설정을 변경해야 한다.

    - 시간대 변경

      ```Time_Zone = 'Asia/Seoul'```

    - 정적파일 경로 추가
    ```
    STATIC_URL = '/static/'
    STATIC_ROOT = os.path.join(BASE_DIR, 'static')
    # 이 부분 마지막 줄에 추가
    ```
    - 호스트는 ```['localhost', '127.0.0.1', '[::1]']```에 대해서 유효
    - 에플리케이션을 배포할 때 PythonAnywhere의 호스트 이름과 일치하지 않으므로
      다음 설정을 아래와 같이 변경해줘야 함.

      ```ALLOWED_HOSTS = ['127.0.0.1', '.pythonanywhere.com']
      ```

    - 데이터베이스 설정 : Mysql로 설정

      ```
      DATABASES = {
      'default': {
          'ENGINE': 'django.db.backends.mysql',
          'NAME': 'DB Name',
          'USER': 'User Name',
          'PASSWORD': 'mysql password',
          'HOST': 'localhost',
          'PORT': "3306"
          }
      }
      ```

# 데이터베이스를 생성

  ```python manage.py migrate```

  * migrate : 적용되지 않은 migrations들을(설정값들을) 적용시키는 역할

# 웹 서버를 시작
  ```python manage.py runserver```



# Reference
- [Djangogirls Tutorial](http://tutorial.djangogirls.org/ko/django/)
