# Django

- ### Django Form

  - #### 개요

    - 우리는 지금까지 HTML form, input 태그를 통해 사용자로부터 데이터를 받았다.

    - 현재 Django 서버는 들어오는 요청을 모두 수용하고 있는데, 이러한 요청 중에는 비정상적인 혹인 악의적인 요청이 있다는 것을 생각해야한다.

    - 이처럼 사용자가 입력한 데이터가 우리가 원하는 데이터 형식이 맞는지에 대한 유효성 검증이 반드시 필요하다.

    - ##### Django Form은 이 과정에서 과중한 작업과 반복 코드를 줄여줌으로써 훨신 쉽게 유효성 검증을 진행할 수 있도록 만들어준다.

  - #### Form에 대한 Django의 역할 

    - Django는 Form 과 관련된 유혀성 검사를 단순화하고 자동화 할 수 있는 기능을 제공하며, 개발자가 직접 작성하는 코드보다 더 안전하고 빠르게 수행하는 코드를 작성할 수 있다.

  - #### Django는 Form에 관련된 작업의 세 부분을 처리

    - 렌더링을 위한 데이터 준비 및 재구성
    - 데이터에 대한 HTML forms 생성
    - 클라이언트로부터 받은 데이터 수신 및 처리



- ### Django Form Class

  - #### 개요

    - Form Class
      - Django form 관리 시스템의 핵심

  - #### Form Class 선언

    - Form Class를 선언하는 것은 Model Class를 선언하는 것과 비슷하다.
    - Model 과 마찬가지로 상속을 통해 선언 (forms 라이브러리의 Form 클래스를 상속받는다.)
    - 앱 폴더에 forms.py 를 생성하고 ArticleForm Class 생성
    - form에는 model field와 달리 TextField가 존재하지 않는다.



- ### Static files

  - 응답할 때 별도의 처리 없이 파일 내용 그대로 보여주면 되는 파일
    - 사용자의 요청에 따라 내용이 바뀌는 것이 아니라 요청한 것을 그대로 보여주는 파일
  - 파일 자체가 고정되어 있고, 서비스 중에도 추가되거나 변경되지 않고 고정 되어있다.
    - 예를 들어, 웹 사이트는 일반적으로 이미지, 자바스크립트 또는 CSS와 같은 미리 준비된 추가 파일(정적)을 제공해야한다.
  - Django에서는 이러한 파일들을 "static file" 이라고 한다.
    - Django는 staticfiles 앱을 통해 정적 파일과 관련된 기능을 제공한다.

- #### Meida File

  - 미디어 파일
  - 사용자가 웹에서 업로드하는 정적 파일
  - 유저가 업로드 한 모든 정적 파일

- #### 웹 서버와 정적 파일

  - 웹 서버의 기본 동작
    - 특정 위치(URL)에 있는 자원을 요청( HTTP request) 받아서
    - 응답(HTTP response)을 처리하고 제공(serving)하는 것
  - ![image-20230321104146058](images\image-20230321104146058.png)

- #### Static files 구성하기

  1. STATIC_ROOT
     - Django 프로젝트에서 사용하는 모든 정적 파일을 한곳에 모아 넣은 경로 (배포 시)
  2. STATICFILES_DIRS
     - 기본경로 외에 추가적인 정적 파일 경로 목록을 정의하는 리스트
     - 추가 파일 디렉토리에 대한 전체 경로를 포함하는 문자열 목록으로 작성되어야한다.



- ### Django authentication system

  - #### 개요

    - Django authentication system은 인증과 권한 부여를 함께 제공(처리)하며, 이러한 기능을 일반적으로 인증 시스템이라고 한다.
    - 필수 구성은 settings.py에 이미 포함되어 있으며 INSTALLED_APPS에서 확인이 가능하다. (django.contrib.auth)
    - Authentication(인증)
      - 신원 확인
      - 사용자가 자신이 누구인지 확인하는 것
    - Authorization (권한,허가)
      - 권한 부여
        - 인증된 사용자가 수행할 수 있는 작업을 결정

- ### Custom User model

  - 개발자들이 작성하는 일부 프로젝트에서는 django에서 제공하는 built-in User model의 기본 인증 요구사항이 적절하지 않을 수 있다.
    - 예를 들어, 내 서비스에서 회원가입 시 username 대신 email을 식별 값으로 사용하는 것이 더 적합한 사이트인 경우, Django의 User Model은 기본적으로 username를 식별 값으로 사용하기 때문에 적합하지 않다.
    - Django는 현재 프로젝트에서 사용할 User Model을 결정하는 AUTH_USER_MODEL 설정 값으로 Default User Model을 재정의(override) 할 수 있도록 한다.





- ### 쿠키 (Cookie)

  - #### 개요

    - HTTP 쿠키는 상태가 있는 세션을 만들도록 해준다.
    - 웹 서비스는 언제 / 어디서나 / 누구에게나 열려있다.
    - 접근성을 챙긴대신 클라이언트를 구분해서 관리하기 어렵기 때문에 서버에서 클라이언트를 구분할 수단으로 쿠키를 사용??

    

  - #### 개념

    - 서버가 사용자의 웹 브라우저에 전송하는 작은 데이터 조각
    - 사용자가 웹사이트를 방문할 경우 해당 웹사이트의 서버를 통해 사용자의 컴퓨터에 설치되는 작은 기록 정보 파일
      - 브라우저(클라이언트)는 쿠키를 로컬에 KEY-VALUE의 데이터 형식으로 저장
      - 이렇게 쿠키를 저장해 놓았다가, 동일한 서버에 재요청 시 저장된 쿠키를 함께 전송
    - 쿠키는 두 요청이 동일한 브라우저에서 들어왔는지 아닌지를 판단할 때 주로 사용된다.
      - 이를 이요야해 사용자의 로그인 상태를 유지할 수 있다.
      - 상태가 없는 HTTP 프로토콜에서 상태 정보를 기억시켜 주기 때문
    - 즉, 웹 페이지에 접속하면 웹 페이지를 응답한 서버로부터 쿠키를 받아 브라우저에 저장하고, 클라이언트가 같은 서버에 재요청 시마다 요청과 함께 저장해 두었던 쿠키도 함께 전송

  - #### 쿠키 사용 예시

  - <img src="images\image-20230322100802957.png" alt="image-20230322100802957" style="zoom:67%;" />

  - #### 쿠키 사용 목적

    - 세션 관리(Session management)
      - 로그인, 아이디 자동완성, 공지 하루 안보기, 팝업 체크, 장바구니 등의 정보 관리
    - 개인화 (Personalization)
      - 사용자 선호, 테마 등의 설정
    - 트래킹 (Tracking)
      - 사용자 행동을 기록 및 분석

  

  - #### 세션 (Session)

    - 사이트와 특정 브라우저 사이의 "state(상태)" 를 유지시키는 것

    - 클라이언트가 서버에 접속하면 서버가 특정 session id를 발급하고, 클라이언트는 session id를 쿠키에 저장

      - 클라이언트가 다시 동일한 서버에 접속하면 요청과 함께 쿠키(session id가 저장된)를 서버에 전달
      - 쿠키는 요청 때마다 서버에 함께 전송 되므로 서버에서 session id를 확인해 알맞은 로직 처리

    - session id는 세션을 구별하기 위해 필요하며, 쿠키에는 session id만 저장

    - #### 과정

      - 서버에는 session table 이 있다 (session id : value) , value에는 민감한 정보 수용 가능 -> 테이블이 서버에 있기 때문
      - 클라이언트가 로그인 요청 -> 쿠키를 서버에 전달 -> 서버에서 쿠키를 열어 session id 비교해서 로직 처리

  - #### 쿠키 Lifetime (수명)

    1. Session cookie
       - 현재 세션이 종료되면 삭제된다.
       - 브라우저 종료와 함께 세션이 삭제된다.
    2. Persistent cookies
       - Expires 속성에 지정된 날짜 혹은 Max-Age 속성에 지정된 기간이 지나면 삭제된다.

  - #### Session in Django

    - **Django는 database-backed sessions** 저장 방식을 기본 값으로 사용
      - session 정보는 Django DB의 **django_session 테이블**에 저장
      - Django는 특정 ssesion id를 포함하는 쿠키를 사용해 각각의 브라우저와 사이트가 연결된 session을 알아낸다.

  

- ### Login

  - #### 개요

    - 로그인은 session을 create하는 과정

```python
from django.shortcuts import render,redirect
from django.contrib.auth import login as auth_login

def login(request):
    if request.method == 'POST' : # db의 데이터를 변환 시키기 때문에 POST
        form = AuthenticationForm(request, request.POST)
        #form = AuthenticationForm(request, data = request.POST)
        if form.is_valid():
            auth_login(request, form.get_user())
            return redirect('articles:index')
    else:
        form = AuthenticationForm()
    context = {
        'form' : form,
    }
    return render(request, 'accounts/login.html',context)
            
```



- ### Logout

  - 개요
    - 로그아웃은 클라이언트와 db의 session을 delete하는 과정
      - 현재 요청에 대한 session data를 db에서 삭제
      - 클라이언트의 쿠키에서도 session id를 삭제
      - 이는 다른 사람이 동일한 웹 브라우저를 사용해 로그인하고, 이전 사용자의 세션 데이터에 접근하는 것을 방지하기 위함이다.

```python
from django.contrib.auth import logout as auth_logout

def logout(request):
    auth_logout(request)
    return redirect('articles:index')
```



- #### templates 에서 user 사용하기 

  https://docs.djangoproject.com/en/4.0/ref/contrib/auth/

  

  