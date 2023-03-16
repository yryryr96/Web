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

  - Django를 이용한 프로젝트,App 생성 순서 ( 가상환경 생성 > 프로젝트 생성 > 앱 생성 > 동작)
    - python -m venv venv ( 가상환경 생성)
    - source venv/Scripts/activate  ( 가상환경 활성화 )
    - pip install django==3.2.18  ( 장고 설치 )
    - django-admin startproject firstpjt ( 프로젝트 생성 )
    - python manage.py runserver ( 서버 실행 , 순서 상관없음)
    - python manage.py startapp articles > settings.py 의 INSTALLED_APPS 에 추가 ( App 생성)
    - urls.py 작성 > from articles import views > path('articles/', views.index) ( urls path 추가)
    - views.py 에서 index 함수 정의 > from django.http import HttpResponse ( 동작 설정 )
    - views의 HttpResponse 불편하므로 articles/templates/articles/index.html 생성 ( 함수 페이지에 나타낼 자료를 html에 따로 작성해서 연결 render 함수 사용 )
    - render( request, template_name, context )
      - request : 응답을 생성하는 데 사용되는 요청 객체
      - template_name : 템플릿의 전체 이름 또는 템플릿 이름의 경로
      - context : 템플릿에서 사용할 데이터 (딕셔너리 타입으로 작성)



- ### Django's Design Pattern

  - **MVC** : Model - View - Controller : 데이터 및 논리 제어를 구현하는데 널리 사용되는 소프트웨어 디자인 패턴
  - 하나의 큰 프로그램을 세가지 역할로 구분한 개발 방법론
    - Model : 데이터와 관련된 로직을 관리
    - View : 레이아웃과 화면을 처리
    - Controller : 명령을 model과 view 부분으로 연결
  - MVC 소프트웨어 디자인 패턴의 목적
    - 관심사 분리
    - 더 나은 업무의 분리와 향상된 관리를 제공
    - 각 부분을 독립적으로 개발할 수 있어, 하나를 수정하고 싶을 때 독립적으로 관리 가능
      - 개발 효율성 및 유지보수가 쉬워짐
      - 다수의 멤버로 개발하기 용이함

  

- ### Django 에서의 디자인 패턴

  - Django는 MVC 패턴을 기반으로 한 MTV 패턴을 사용
  - 두 패턴은 서로 크게 다른 점은 없으며 일부 역할에 대해 부르는 이름이 다름

<img src="images\image-20230314141833268.png" alt="image-20230314141833268" style="zoom:80%;" />



- ### MTV 디자인 패턴

  - #### Model

    - MVC 패턴에서 Model의 역할에 해당
    - 데이터와 관련된 로직을 관리
    - 응용프로그램의 데이터 구조를 정의하고 데이터베이스의 기록을 관리

  - #### Template

    - 레이아웃과 화면을 처리
    - 화면상의 사용자 인터페이스 구조와 레이아웃을 정의
    - MVC 패턴에서 View의 역할에 해당

  - #### View

    - Model & Template과 관련한 로직을 처리해서 응답을 반환
    - 클라이언트의 요청에 대해 **처리**를 분기하는 역할
    - 동작 예시
      - 데이터가 필요하다면 model에 접근해서 데이터를 가져오고 가져온 데이터를 template로 보내 화면을 구성하고 구성된 화면을 응답으로 만들어 클라이언트에게 반환
    - MVC 패턴에서 Controller의 역할에 해당

<img src="images\image-20230314142313337.png" alt="image-20230314142313337" style="zoom:80%;" />

- ### 정리 

  - Django는 MTV 디자인 패턴을 가지고 있음
    - Model : 데이터 관련
    - Template : 화면 관련
    - View : Model & Template 중간 처리 및 응답 변환



- ### Django Template Language (DTL)

  - Django template에서 사용하는 built-in template system
  - 조건,반복,변수 치환, 필터 등의 기능 제공
    - python처럼 일부 프로그래밍 구조(if, for 등)를 사용할 수 있지만 이것은 python 코드로 실행되는 것이 아니다.
    - Django 템플릿 시스템은 단순히 Python이 HTML에 포함 된 것이 아니니 주의
  - 프로그래밍적 로직이 아니라 프레젠테이션을 표현하기 위한 것임을 명심!!!



- ### DTL Syntax

  - #### Variable

    - 변수명은 영어, 숫자와 밑줄(_)의 조합으로 구성될 수 있으나 밑줄로는 시작할 수 없음.

      - 공백이나 구두점 문자 또한 사용할 수 없음

    - dot(.)를 사용해 변수 속성에 접근할 수 있다.

    - render()의 세번째 인자로 {'key': value}와 같이 딕셔너리 형태로 넘겨주며, 여기서 정의한 key에 해당하는 문자열이 template에서 사용가능한 변수명이 됨

      - ```python
        # views.py
        
        #1
        def index(request):
        	name = 'aiden'
            return render(request,'myapp/index.html',{'name' : name})
        #2
        def index(request):
            info = {
                'name' : 'aiden',
                'age' : 21,
            }
            
            return render(request,'myapp/index.html',{'info' : info})
        
        # index.html
        <body>
        	<h1>info.name</h1> # aiden
            <h1>info.age</h1> # 21
        </body>
        ```

  - #### Filter { | }

    - 표시할 변수를 수정할 때 사용 > 변수 자체를 변경하는것이 아닌 보여지는 값만 바뀜
    - {{ name | lower }} : name 변수를 모두 소문자로 출력
    - 60개의 builtin template filters를 제공
    - chained가 가능하며 일부 필터는 인자를 받기도 함 {{ name|add:30 }}

  - #### Tags {% tag %}

    - 출력 텍스트를 만들거나, 반복 또는 논리를 수행하여 제어 흐름을 만드는 등 변수보다 복잡한 일들을 수행
    - 일부 태그는 시작과 종료 태그가 필요 {% if %}{% endif %}
    - 약 24개의 built-in template tags를 제공

  - #### Comments {# #}

    - Django template 에서 라인의 주석을 표현하기 위해 사용
    - 유효하지 않은 템플릿 코드가 포함될 수 있음
    - 한 줄 주석에만 사용할 수 있음 ( 줄 바꿈이 허용되지 않음 )
    - 여러 줄 주석은 {% comment %} 와 {% endcomment %} 사이에 입력



- ### Template 상속

  - 템플릿 상속은 기본적으로 코드의 재사용성에 초점을 맞춤

  - 템플릿 상속을 사용하면 사이트의 모든 공통 요소를 포함하고, 하위 템플릿이 재정의 할 수 있는 블록을 정의하는 기본 'skeleton' 템플릿을 만들 수 있음

  - #### 템플릿 상속에 관련된 태그

    - ##### {% extends '' %}

      - 자식 (하위) 템플릿이 부모 템플릿을 확장한다는 것을 알림
      - 반드시 템플릿 최상단에 작성 되어야 함 (1개만)

    - ##### {% block content %}{% endblock content %}

      - 하위 템플릿에서 재지정할 수 있는 블록을 정의
      - 즉, 하위 템플릿이 채울 수 있는 공간
      - 가독성을 높이기 위해 선택적으로 endblock 태그에 이름을 지정할 수 있음 ( 빼도 된다 )
        - {% endblock %} 하나 {% endblock content %} 하나 똑같다.

  - #### Django의 template 처리

    - <img src="images\image-20230315120135672.png" alt="image-20230315120135672" style="zoom: 80%;" />
    - base.index를 프로젝트의 최상위 폴더에 만들어두고 여러앱에서 사용할 수 있도록 하려면 아래 그림처럼 설정

<img src="images\image-20230315120207271.png" alt="image-20230315120207271" style="zoom:80%;" />



- ### Trailing Slashes

  - Django는 URL 끝에 /가 없다면 자동으로 붙여주는 것이 기본 설정

    - 모든 주소가 '/' 로 끝나도록 구성 되어있다.
    - 그러나 모든 프레임워크가 이렇게 동작하는 것은 아니다.

  - Django의 url 설계 철학을 통해 먼저 살펴보자.

    - ##### "기술적인 측면에서, foo.com/bar 와 foo.com/bar/ 는 서로 다른 URL이다. "

    - 검색 엔진 로봇이나 웹 트래픽 분석 도구에서는 그 둘을 서로 다른 페이지로 본다.

    - Django는 URL을 정규화하여 검색 엔진 로봇이 혼동하지 않도록 해야 한다.



- ### Variable routing

  - URL 주소를 변수로 사용하는 것을 의미한다.
  - URL의 일부를 변수로 지정해 view 함수의 인자로 넘길 수 있다.
  - 즉, 변수 값에 따라 하나의 path()에 여러 페이지를 연결 시킬 수 있다.

<img src="images\image-20230315121641788.png" alt="image-20230315121641788" style="zoom:80%;" />

![image-20230315121741309](images\image-20230315121741309.png)



- ### App URL mapping

  - 앱이 많아졌을 때 urls.py를 각 app에 매핑하는 방법을 이해하기
  - 두 번째 app인 pages를 생성 및 등록
  - 예로 App 들의 view 함수들은 이름이 같으므로 from app import views as app_views 식으로 각각 import해도 되지만 너무 불편하다. 더 좋은 방법은??
    - urls.py 를 쪼갠다
    - 하나의 프로젝트에 여러 앱이 존재하면 각각의 앱 안에 urls.py를 만들고 프로젝트 urls.py에서 각 앱의 urls.py 파일로 URL 매핑을 위탁할 수 있다.

<img src="images\image-20230315134450870.png" alt="image-20230315134450870" style="zoom: 50%;" />

<img src="images\image-20230315134633690.png" alt="image-20230315134633690" style="zoom: 80%;" />



- ### Sending form data (Client)

  - 데이터가 전송되는 방법을 정의

  - 웹에서 사용자 정보를 입력하는 여러 방식을 제공하고, 사용자로부터 할당된 데이터를 서버로 전송하는 역할

  - 데이터를 어디(action)로 어떤 방식(method)으로 보낼지

    - #### action

      - 입력 데이터가 전송될 URL을 지정
      - 데이터를 어디로 보낼 것인지 지정하는 것이며 이 값은 반드시 유효한 URL 이어야 함
      - 만약 이 속성을 지정하지 않으면 데이터는 현재 form이 있는 페이지의 URL로 보내짐

    - #### method

      - 데이터를 어떻게 보낼 것인지 정의
      - 입력 데이터의 HTTP request methods를 지정
      - HTML form 데이터는 오직 2가지 방법으로만 전송할 수 있다. > GET, POST

  - #### HTML < input > element

    - 사용자로부터 데이터를 입력 받기 위해 사용

  - #### HTML input's attribute

    - name
      - form을 통해 데이터를 제출했을 때 name 속성에 설정된 값을 서버로 전송하고, 서버는 name 속성에 설정된 값을 통해 사용자가 입력한 데이터 값에 접근할 수 있다.
      - 서버에 전달하는 파라미터 ( name : value ) 로 매핑한다.

  - #### HTML request methods

    - HTTP
      - HTML 문서와 같은 리소스(데이터, 자원)들을 가져올 수 있도록 해주는 프로토콜 (규칙, 규약)
      - 웹에서 이루어지는 모든 데이터 교환의 기초
      - HTTP는 주어진 리소스가 수행 할 원하는 작업을 나타내는 request methods를 정의
      
    - 자원에 대한 행위 (수행하고자 하는 동작)를 정의
  
    - 주어진 리소스(자원)에 수행하길 원하는 행동을 나타냄

    - HTTP Method 예시
      - ##### GET 
      
        - 주소에 데이터를 추가해 전달하는 방식
        - 데이터가 주소 입력창에 그대로 나타난다.
        - 전송할 수 있는 크기가 제한적이다.
        - 쿼리와 같이 크기가 작고 중요도가 낮은 정보를 보낼 때 주로 사용
      
      - ##### POST
      
        - 데이터를 별도로 첨부하여 전달하는 방식
        - 데이터가 외부에 드러나지 않는다.
        - 전송할 수 있는 데이터의 크기가 제한이 없다.
        - 보안성 및 활용성이 GET 방식보다 좋다.
  
  - #### GET
  
    - 서버로부터 정보를 조회하는 데 사용
  
      - 즉, 서버에게 리소스를 요청하기 위해 사용
  
    - ##### 데이터를 가져올 때만 사용해야 함
  
    - 데이터를 서버로 전송할 때 Query String Parameters를 통해 전송
  
      - 데이터는 URL에 포함되어 서버로 보내짐
  
  - #### Query String Parameters
  
    - 사용자가 입력 데이터를 전달하는 방법 중 하나로, url 주소에 데이터를 파라미터를 통해 넘기는 것
  
    - 이러한 문자열은 &로 연결된 key=value 쌍으로 구성되며 기본 URL과 물음표(?) 로 구분된다
  
      - http://host:port/path?key=value&key=value
  
    - ? 시작으로 Query String이 시작함을 알림
  
    - 파라미터가 여러 개일 경우 "&" 을 붙여 여러 개의 파라미터를 넘길 수 있다.
  
    - #### 모든 요청 데이터는 view 함수의 첫번째 인자 request에 들어있다.



- ### Django Model

  - Model의 핵심 개념과 ORM을 통한 데이터베이스 조작 이해
  - Django는 웹 애플리케이션의 데이터를 구조화하고 조작하기 위한 추상적인 계층(모델)을 제공

  

- ### Database

  - 체계화된 데이터의 모임

  - 검색 및 구조화 같은 작업을 보다 쉽게 하기 위해 조직화된 데이터를 수집하는 저장 시스템

  - #### Schema

    - 뼈대 (structure)
    - 데이터베이스에서 자료의 구조, 표현 방법, 관계 등을 정의한 구조

  - #### Table

    - 필드와 레코드를 사용해 조직된 데이터 요소들의 집합
    - 관계(Relation)라고도 부름
    - <img src="images\image-20230316100405625.png" alt="image-20230316100405625" style="zoom:80%;" />

    - ##### 필드(field)

      - 속성 or 컬럼
      - 각 필드에는 고유한 데이터 형식이 지정된다.
        - INT, TEXT 등

    - ##### 레코드(record)

      - 튜플 혹은 행
      - 테이블의 데이터는 레코드에 저장된다.

    - ##### PK (Primary Key)

      - 기본 키

      - 각 레코드의 고유한 값 ( 식별자로 사용 )

      - ##### 기술적으로 다른 항목과 절대로 중복될 수 없는 단일 값(unique)

      - 데이터베이스 관리 및 테이블 간 관계 설정 시 주요하게 활용된다.

    - ##### 쿼리(Query)

      - 데이터를 조회하기 위한 명령어
      - 조건에 맞는 데이터를 추출하거나 조작하는 명령어
      - Query를 날린다 > 데이터베이스를 조작한다.

  

- ### Model

  - Django는 Model을 통해 데이터에 접근하고 조작한다.
  - 저장된 데이터베이스의 구조 (layout)
  - 일반적으로 각각의 모델은 하나의 데이터베이스 테이블에 매핑된다.
    - 모델 클래스 1개 == 데이터베이스 테이블 1개

<img src="images\image-20230316100828986.png" alt="image-20230316100828986" style="zoom:80%;" />



- ### Migration

  - Django가 모델에 생긴 변화( 필드 추가, 수정 등)를 실제 DB에 반영하는 방법

  1. ##### makemigrations ( 하나의 table을 만드는 과정 )

     - 모델의 변경사항에 대한 새로운 migration을 만들 때 사용
     - python manage.py makemigrations

  2. ##### migrate ( 만든 테이블을 DB에 동기화 시키는 과정 )

     - makemigrations로 만든 설계도를 실제 데이터베이스에 반영하는 과정
     - 결과적으로 모델의 변경사항과 데이터베이스를 동기화
     - python manage.py migrate

  - #### Migration 3단계

    1. models.py 에 변경사항이 생기면
    2. migration 생성 (makemigrations)
    3. DB 반영 (migrate)

  - ##### DB는 SQL만 알아들을 수 있는데 makemigrations로 만들어진 설계도는 python으로 작성돼있다. 파이썬 언어를 SQL로 바꿔 DB와 소통할 수 있게 해주는 중간 번역 역할이 ORM



- ### ORM (Object-relational-Mapping)

  - 객체지향 프로그래밍 언어를 사용해 호환되지 않는 유형의 시스템 간에 데이터를 변환하는 프로그래밍 기술

  - 객체 지향 프로그래밍에서 데이터베이스를 연동할 때, 데이터베이스와 객체 지향 프로그래밍 언어 간의 호환되지 않는 데이터를 변환하는 프로그래밍 기법

  - Django는 내장 Django ORM을 사용

  - ##### 한 마디로 SQL을 사용하지 않고 데이터베이스를 조작할 수 있게 만들어주는 매개체

  - <img src="images\image-20230316102816412.png" alt="image-20230316102816412" style="zoom:80%;" />

  - ORM 장단점

    - 장점
      - SQL을 잘 몰라도 객체지향 언어로 DB 조작이 가능하다.
      - 객체 지향 접근으로 인한 높은 생산성
    - 단점
      - ORM만으로 세밀한 DB 조작을 구현하기 어려운 경우가 있다.

  - #### Model 정리 

    - 웹 애플리케이션의 데이터를 구조화하고 조작하기 위한 도구



- ### QuerySet API

  <img src="images\image-20230316154612726.png" alt="image-20230316154612726" style="zoom:80%;" />

  - Django 모델이 데이터베이스 쿼리 작업을 가능하게 하는 인터페이스

  - Django는 기본적으로 모든 Django 모델 클래스에 대해 objects라는 Manager 객체를 자동으로 추가한다.

  - 이 Manager를 통해 특정 데이터를 조작할 수 있다.

  - ##### DB를 Python class로 조작할 수 있도록 여러 메서드를 제공하는 manager

  - #### Query
  
    - 데이터베이스에 특정한 데이터를 보여 달라는 요청
      - 쿼리문을 작성한다 -> 원하는 데이터를 얻기 위해 데이터베이스에 요청을 보낼 코드를 작성한다.
    - 이 때, 파이썬으로 작성한 코드가 ORM에 의해 SQL로 변환되어 데이터베이스에 전달되며, 데이터베이스의 응답 데이터를 ORM이 QuerySet 이라는 자료 형태로 변환하여 우리에게 전달한다.

  - #### QuerySet
  
    - 데이터베이스에게서 전달 받은 객체 목록 (데이터 모음)
      - 순회가 가능한 데이터로써 1개 이상의 데이터를 불러와 사용할 수 있다.
    - Django ORM을 통해 만들어진 자료형이며, 필터를 걸거나 정렬 등을 수행할 수 있다.
    - objects manager를 사용해 복수의 데이터를 가져오는 queryset method를 사용할 때 반환되는 객체
    - 단, DB가 단일 객체를 반환 할 때는 QuerySet이 아닌 모델(Class)의 인스턴스로 반환된다.

<img src="images\image-20230316104706750.png" alt="image-20230316104706750" style="zoom:67%;" />



- ### CRUD (Creat / Read / Update / Delete)

  - #### CREATE

    - <img src="images\image-20230316115730113.png" alt="image-20230316115730113" style="zoom:80%;" />
    
  - #### READ
  
    - ##### get()
  
      - 단일 데이터 조회
      - 예외,에러를 발생시킬 수 있기 때문에 고유성을 보장하는 조회에서 사용해야한다. ex) pk
      - <img src="images\image-20230316160155864.png" alt="image-20230316160155864" style="zoom:80%;" />
  
    - filter()
  
      - 지정된 조회 매개 변수와 일치하는 객체를 포함하는 새 QuerySet을 반환
      - ![image-20230316160242428](images\image-20230316160242428.png)
      - 조회된 객체가 없거나 1개여도 QuerySet을 반환
  
  - #### Update
  
    - 수정하고자 하는 article 인스턴스 객체를 조회 후 반환 값을 저장
    - article 인스턴스 객체의 인스턴스 변수 값을 새로운 값으로 할당
    - save() 인스턴스 메서드 호출
    - <img src="images\image-20230316160437415.png" alt="image-20230316160437415" style="zoom:80%;" />
  
  - #### Delete
  
    - 삭제하고자 하는 article 인스턴스 객체를 조회 후 반환 값을 저장
    - delete() 인스턴스 메서드 호출
    - <img src="images\image-20230316160521560.png" alt="image-20230316160521560" style="zoom:80%;" />