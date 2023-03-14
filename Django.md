# Django

- ### Framework

  - 개발에 자주 사요되는 부분들을 재사용 할 수 있게 좋은 구조의 코드로 만들어놨는데 그러한 코드들을 모아 놓은 것,  **즉 서비스 개발에 필요한 기능들을 미리 구현해서 모아 놓은 것 = 프레임워크(Framwork)**
  - Frame (뼈대,틀) + Work (일하다)
    - 일정한 뼈대, 틀을 가지고 일하다
    - 제공받은 도구들과 뼈대, 규약을 가지고 무언가를 만드는 일
    - 특정 프로그램을 개발하기 위한 여러 도구들과 규약을 제공하는 것
  - " 소프트웨어 프레임워크 " 는 복작한 문제를 해결하거나 서술하는 데 사용되는 기본 개념 구조
  - 따라서, Framework를 잘 사용하기만 하면 웹 서비스 개발에 있어서 모든 것들을 하나부터 열까지 직접 개발할 필요 없이, 내가 만들고자 하는 본질(로직)에 집중해 개발할 수 있음
  - 소프트웨어의 생산성과 품질을 높임



- ### 클라이언트 - 서버 구조

  - 오늘날 우리가 사용하는 대부분의 웹 서비스는 클라이언트-서버 구조를 기반으로 동작

  - 클라이언트와 서버 역시 하나의 컴퓨터이며 이들이 어떻게 상호작용하는지에 대한 간소화된 다이어그램은 다음과 같음

    

    ![image-20230314091733799](images\image-20230314091733799.png)

  - #### 클라이언트

    - 웹 사용자의 인터넷에 연결된 장치 ( 예를 들어 wifi에 연결된 컴퓨터 또는 모바일)
    - Chrome 또는 Firefox와 같은 웹 브라우저
    - 서비스를 요청하는 주체

  - #### 서버

    - 웹 페이지, 사이트 또는 앱을 저장하는 컴퓨터
    - 클라이언트가 웹 페이지에 접근하려고 할 때 서버에서 클라이언트 컴퓨터로 웹 페이지 데이터를 응답해 사용자의 웹 브라우저에 표시됨
    - 요청에 대해 서비스를 응답하는 주체

  - #### 상호작용 예시 (우리가 구글 홈페이지에 접속한다는 것은 무슨 뜻인가?)

    - 결론적으로 인터넷에 연결된 전세계 어딘가에 있는 구글 컴퓨터에게 'google 홈페이지.html' 파일을 달라고 요청하는 것
    - 그러면 구글 컴퓨터는 우리의 요청을 받고 'google 홈페이지.html' 파일을 인터넷을 통해서 우리 컴퓨터에게 응답해줌
    - 그렇게 전달받은 google 홈페이지.html 파일을 웹 브라우저가 우리가 볼 수 있도록 해석해주는 것
    - 여기서 'google 홈페이지.html'을 달라고 요청한 컴퓨터, 웹 브라우저를 **클라이언트**라고 하고 'google 홈페이지.html'파일을 제공한 컴퓨터, 프로그램을 **서버**라고 함
    - 어떠한 자원을 달라고 요청(request)하는 쪽을 클라이언트라고 하고 자원을 제공해주는 쪽을 서버(server)라고 한다.



- ### Django 따라하기

<img src="images\image-20230314101345914.png" alt="image-20230314101345914" style="zoom: 80%;" />

- 공식문서 : https://docs.djangoproject.com/ko/4.1/intro/

- ### 가상환경

  - 프로젝트별 패키지를 독립적으로 분리해서 작업하기 위해 가상환경을 만들어 사용
  - 폴더를 만들어 가상환경 생성 후 Django install 습관화 !!



- ### Django 구성 (Project, App)

  - #### Project

    - 프로젝트는 앱의 집합
    - 프로젝트에는 여러 앱이 포함될 수 있다.
    - 앱은 여러 프로젝트에 있을 수 있다.
    - asgi.py
      - Asynchronous Server Gateway Interface
      - Django 애플리케이션이 비동기식 웹 서버와 연결 및 소통하는 것을 도움
      - 추후 배포 시에 사용한다.
    - settings.py
      - Django 프로젝트 설정을 관리
    - urls.py
      - 사이트의 url과 적절한 views의 연결을 지정
    - wsgi.py
      - Web Server Gateway Interface
      - Django 애플리케이션이 웹서버와 연결 및 소통하는 것을 도움
      - 추후 배포시에 사용
    - manage.py
      - Django 프로젝트와 다양한 방법으로 상호작용 하는 커맨드라인 유틸리티
      - python manage.py < command > [options]  > python manage.py runserver

  - #### Application

    - 앱은 실제 요청을 처리하고 페이지를 보여주는 등의 역할을 담당

    - 앱은 하나의 역할 및 기능 단위로 작성하는 것을 권장함 ( 기능별)

    - App 생성

      - python manage.py startapp (이름(복수형))
      - App : 하나의 큰 기능 단위

    - admin.py

      - 관리자용 페이지를 설정하는 곳

    - apps.py

      - 앱의 정보가 작성된 곳
      - 별도의 추가 코드 작성 x

    - ##### models.py

      - 애플리케이션에서 사용하는 Model을 정의하는 곳
      - MTV 패턴의 M에 해당

    - tests.py

      - 프로젝트의 테스트 코드를 작성하는 곳

    - views.py

      - view 함수들이 정의 되는 곳
      - MTV 패턴의 V에 해당

  - #### App 등록

    - 앱을 사용하기 위해서는 settings.py의 INSTALLED_APPS 리스트에 앱을 추가해줘야함

<img src="images\image-20230314104846389.png" alt="image-20230314104846389" style="zoom: 67%;" />



- ### 요청과 응답

  - 가상환경 생성 > 프로젝트 생성 > 앱 생성

    - python -m venv venv
    - source venv/Scripts/activate
    - pip install django==3.2.18
    - django-admin startproject firstpjt
    - python manage.py runserver
    - python manage.py startapp articles > settings.py 의 INSTALLED_APPS 에 추가 
    - urls.py 작성 > from articles import views > path('articles/', views.index)
    - views.py 에서 index 함수 정의 > from django.http import HttpResponse
    - views의 HttpResponse 불편하므로 articles/templates/articles/index.html 생성
    - render(request, template_name, context )
      - request : 응답을 생성하는 데 사용되는 요청 객체
      - template_name : 템플릿의 전체 이름 또는 템플릿 이름의 경로
      - context : 템플릿에서 사용할 데이터 (딕셔너리 타입으로 작성)

    

  - Django의 세가지 구조 MTV ( Model, View, Template)

  - 코드 작성 순서

    - urls.py > views.py > templates