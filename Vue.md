# Vue (JavaScript Framework)

#### Front-end 개발은 Web App 또는 Web Site의 UI/UX를 제작하고 관리하는 과정

- #### Web App

웹 브라우저에서 실행되는 어플리케이션 소프트웨어



- #### SPA ( Single Page Application )

  - SPA는 서버에서 최초 1장의 HTML만 전달받아 모든 요청에 대응하는 방식
    -  Django는 MPA ( Multi Page Application) : 페이지를 새로고침하며 사용자가 요청한 웹 페이지를 보여주는 방식 ( Page Reload )
  - CSR ( Client Side Rendering ) 방식으로 요청을 처리한다.
  - SEO ( Search Engine Optimization ) 관리가 어렵다.
  - 서버의 부하가 적다. ( 필요한 것만 부분적으로 받아오기 때문 )
  - 초기 랜더링 이후에 빠르다.



- #### MPA (Multi Page Application)

  - MPA는 HTML의 정보를 모두 가지고 있기 때문에 SEO 관리에 적절하고 쉽다.
  - 서버의 부하가 많다. ( 모든 정보를 가져오기 때문 )
  - 초기 랜더링 이후에 느리다.



- #### SSR (Server Side Rendering )

  - Server가 사용자의 요청에 적합한  HTML을 렌더링하여 제공하는 방식
  - 전달받은 새 문서를 보여주기 위해 브라우저는 새로고침을 진행 (Page Reload)
  - 요청을 받고 요청받은대로 모든 것을 구성한 후 Page Reload해서 Client에게 전달

<img src="images\image-20230427091910003.png" alt="image-20230427091910003" style="zoom: 80%;" />



- #### CSR (Client Side Rendering)

  - 최초 한 장의 HTML을 받아온다.
    - server로 부터 최초로 받아오는 문서는 빈 html 문서
  - CSR 방식을 사용하는 이유
    - 모든 HTML 페이지를 서버로부터 받아서 표시하지 않아도 된다.
      - 클라이언트-서버 통신 -> 트래픽 감소 -> 응답속도 향상
    - 매번 새 문서를 받아 새로고침하는 것이 아니라 필요한 부분만 고쳐 나가므로 각 요청이 끊김없이 진행
    - BE와 FE 작업 영역을 명확히 분리 할 수 있다.
      - 각자 맡은 역할을 명확히 분리 -> 협업이 용이해진다.

<img src="images\image-20230427092211456.png" alt="image-20230427092211456" style="zoom: 80%;" />



- #### MVVM Pattern

<img src="images\image-20230427152325110.png" alt="image-20230427152325110" style="zoom:80%;" />

view : 눈에 보이는 부분 ( UI, DOM)

Model : 실제 데이터 ( JSON , 비즈니스 코드 ( 계산적 ))

ViewModel  : 함수가 저장돼있다. 함수 작성 공간



- ### Vue CLI

  - npm install -g @vue/cli  : 설치
  - vue create vue-cli : 프로젝트 생성
  - cd vue-cli -> npm run serve
  - node_modules : python의 venv와 비슷한 역할



- ### Vue State Management

  - ##### Centralized Store

    - 중앙 저장소(store)에 데이터를 모아서 상태 관리

<img src="images\image-20230504091020768.png" alt="image-20230504091020768" style="zoom:80%;" />

- ### Vuex

  - Vuex 왜 쓰냐 ? 

    - props-emit 으로 데이터 전달을 하면 단점이 많다.
    - 데이터를 통합적으로 관리하기 위해 사용한다 => 상태 관리

  - #### State

    - vue 인스턴스의 data에 해당

    - ##### 중앙에서 관리하는 모든 상태 정보

      - 개별 component가 관리하던 data를 중앙 저장소 (Vuex Store의 state) 에서 관리하게 된다.
      - 개별 data도 생성 가능
      - $store.state

  - #### Mutations

    - ##### 실제로 state를 변경하는 유일한 방법

    - vue instance의 methods에 해당하지만 Mutations에서 호출되는 핸들러 함수는 동기적

    - 첫 번째 인자로 state를 받으며, component 혹은 Actions에서 commit() 메서드로 호출된다.

  - #### Actions

    - ##### mutations와 비슷하지만 비동기 작업을 포함할 수 있다는 차이가 있다.

    - state를 직접 변경하지 않고 commit() 메서드로 mutations를 호출해서 state 변경

    - component에서 dispatch() 메서드로 호출된다.

      - dispatch(A,B) : A 호출 요청, B 데이터 전달

    - dispatch(actions 접근) -> actions(요청) -> mutations(적용)

  - #### Getters

    - ##### state를 활용해 계산된 값을 얻고자 할 때 사용



- ### UX (User Experience)

- ### UI (User Interface)

  - Interface
    - 서로 다른 두 개의 시스템, 장치 사이에서 정보나 신호를 주고받는 경우의 접점
      - 사용자가 기기를 쉽게 동작 시키는데 도움을 주는 시스템



- ### Routing 

  - 네트워크에서 경로를 선택하는 프로세스

  - 웹 서비스에서의 라우팅

    - 유저가 방문한 URL에 대해 적절한 결과를 응답하는 것

  - #### SSR

    - Server가 모든 라우팅을 통제
    - URL 요청이 들어오면 응답으로 완성된 HTML을 제공
    - Routing에 대한 결정권을 서버가 가진다

  - #### CSR / SPA

    - 서버는 하나의 HTML 만 제공
    - 하나의 URL만 가질 수 있다.

![image-20230511114254473](C:\Users\SSAFY\Desktop\github\Web\images\image-20230511114254473.png)
