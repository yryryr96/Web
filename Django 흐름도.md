# Django 흐름도

- 가상환경 생성

- 프로젝트 생성

- 앱 생성

- setting.py 설정

- url 분기

- views, template, urls , html 등등 설정

- models.py 에서 class로 테이블 설정

- forms.py 설정

- model에 변경이 있을 시 makemigrations and migrate

- CRUD 체험

- ### 로그인 로그아웃 구현

  - accounts 앱 생성

  - setting.py 등록

  - models.py 에서 User(AbstractUser) 클래스 작성

  - 커스텀 유저 모델 쓰기위해서 setting.py 에 AUTH_USER_MODEL = 'accounts.User'

  - admin.py 에 등록 > admin.site.register(User,UserAdmin)

  - 커스텀 유저 모델 쓸때는 처음에 migrate 해줘야한다. 중간에 바꾸면 큰일남!!

  - urls.py , views.py 에서 login 경로, 함수 설정 logout도 마찬가지

  - login 함수에서 사용되는거 AuthentificationForm() >> from django.contrib.auth.forms import AuthentificationForm

  - ```python
    def login(request):
    	if request.method == 'POST' :
            form = AuthentificationForm(request, request.POST)
            if form.is_valid():
                auth_login(request, form.get_user())
                return rediect('articles:index')
        else :
            form = AuthentificationForm()
        context = {'form' : form}
        return render(request, 'accounts/login.html',context)
    
    def logout(request):
        auth_logout(request)
        return redirect('articles:index')
    ```

  - 

