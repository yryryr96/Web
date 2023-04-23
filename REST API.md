# REST API

- ### URI (Uniform Resource Identifier)

  인터넷에서 리소스를 식별하는 문자열

  가장 일반적인 URI 는 웹 주소로 알려진 URL

  

- #### URL (Uniform Resource Locator)

  웹에서 주어진 리소스의 주소

  네트워크 상에 리소스가 어디있는지 (주소)를 알려주기 위한 약속

![image-20230422170059259](images\image-20230422170059259.png)

- #### URN (Uniform Resource Name)

​		책의 고유 일련번호 같은 느낌



- ### API (Application Programming Interface)

​	애플리케이션과 프로그래밍으로 소통하는 방법



- ### REST (Representational State Transfer)

  - ##### HTTP 프로토콜에서 (자원, 식별자 http 메서드)를 사용해서 제한된 인터페이스에서 클라이언트와 서버를 상호작용하게하는 아키텍쳐
  - 자원을 식별 - URI
  - 자원에 대한 행위 - HTTP Methods
  - 자원을 표현 - JSON



- ### JSON (JavaScript Object Notation)

  - JS의 표기법을 따른 단순 문자열
  - key-value 형태의 구조를 갖고있다.



- ### Serialization

  - 직렬화
    - 직렬화란 ? 어떤 데이터를 내가 원하는 형태로 만드는 것 ( 여기서는 QuerySet -> JSON )
  - 여러 시스템에서 활용하기 위해 데이터 구조나 객체 상태를 나중에 재구성할 수 있는 포맷으로 변환하는 과정
    - 즉, 어떤 언어나 환경에서도 나중에 다시 쉽게 사용할 수 있는 포맷으로 변환하는 과정



- ### Django REST framework (DRF)

  - Django에서 Restful API 서버를 쉽게 구축할 수 있도록 도와주는 오픈소스 라이브러리
