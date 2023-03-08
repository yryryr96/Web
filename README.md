# Web ( HTML, CSS, JS)

- ## HTML ( Hyper Text Markup Language)

  - 참조 (하이퍼링크)를 통해 사용자가 한 문서에서 다른 문서로 즉시 접근할 수 있는 텍스트
  - Markup Language - 태그 등을 이용해 문서나 데이터의 구조를 명시하는 언어
    - HTML, Markdown
  - 웹 페이지를 작성(구조화) 하기 위한 언어



- #### HTML 기본 구조

  - html : 문서의 최상위(root) 요소
  - head : 문서 메타데이터 요소
    - 문서 제목, 이놐딩, 스타일, 외부 파일 로딩 등
    - 일반적으로 브라우저에 나타나지 않는 내용
  - body : 문서 본문 요소
    - 실제 화면 구성과 관련된 내용

  ```html
  <!DOCTYPE html>
  <html lang="ko">
  <head>
      <meta charset="UTF-8">
      <title>Document</title>
  </head>
  <body>
      
  </body>
  </html>
  ```

- #### 요소

  - HTML 요소는 시작 태그와 종료 태그 그리고 태그 사이에 위치한 내용으로 구성
    - 태그(Element,요소)는 컨텐츠(내용)를 감싸는 것으로 그 정보의 성격과 의미를 정의
  - 내용이 없는 태그들
    - br,hr,img,input,link,meta
  - 요소는 중첩(nested)될 수 있음
    - 요소의 중첩을 통해 하나의 문서를 **구조화**
    - 여는 태그와 닫는 태그의 쌍을 잘 확인해야함
      - 오류를 반환하는 것이 아닌 그냥 레이아웃이 깨진 상태로 출력되기 때문에, 디버깅이 힘들어질 수 있음

- #### 속성

  - 속성은 속성명과 속성값으로 이루어져 있다.
  - 속성을 통해 태그의 부가적인 정보를 설정할 수 있음
  - 요소는 속성을 가질 수 있으며, 경로나 크기와 같은 추가적인 정보를 제공
  - 요소의 시작 태그에 작성하며 보통 이름과 값이 하나의 쌍으로 존재
  - 태그와 상관없이 사용 가능한 속성(HTML Global Attribute)들도 있음

```html
<a href="https://google.com"></a>
href : 속성명
주소 : 속성값
```

- HTML Global Attribute
  - 모든 HTML 요소가 공통으로 사용할 수 있는 대표적인 속성 ( 몇몇 요소에는 아무 효과가 없을 수도 있음)
    - id : 문서 전체에서 유일한 고유 식별자 지정
    - class : 공백으로 구분된 해당 요소의 클래스 목록(CSS,JS에서 요소를 선택하거나 접근)
    - style : inline 스타일



- ## CSS

  - 스타일을 지정하기 위한 언어 -> 선택하고, 스타일을 지정한다.
  - CSS 구문은 선택자를 통해 스타일을 지정할 HTML 요소를 선택
  - 중괄호 안에서는 속성과 값, 하나의 쌍으로 이루어진 선언을 진행
  - 각 쌍은 선택한 요소의 속성, 속성에 부여할 값을 의미
    - 속성 (Property) : 어떤 스타일 기능을 변경할지 결정
    - 값 (Value) : 어떻게 스타일 기능을 변경할지 결정



- ####  CSS 구문 - 용어 정리

![image-20230307104421712](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230307104421712.png)

- #### 선택자(Selector) 유형

  - 기본 선택자
    - 전체 선택자(*), 요소(tag) 선택자
    - 클래스(class) 선택자, 아이디(id) 선택자, 속성(attr) 선택자
  - 결합자(Combinators)
    - 자손 결합자, 자식 결합자

  

- ####  CSS 선택자 정리

  - 요소 선택자
    - HTML 태그를 직접 선택
  - 클래스(class) 선택자
    - 마침표(.) 문자로 시작하며, 해당 클래스가 적용된 항목을 선택
  - 아이디(id) 선택자
    - #문자로 시작하며, 해당 아이디가 적용된 항목을 선택
    - 일반적으로 하나의 문서에 1번만 사용, 여러 번 사용해도 동작하지만, 단일 id를 사용하는 것을 권장



- ####  CSS 적용 우선순위 (cascading order)

  - CSS 우선순위를 아래와 같이 그룹을 지어볼 수 있다.

    - 1. 중요도(Importance) - 사용시 주의

      - !important

    - 2. 우선 순위(Specificity)

      - 인라인 > id > class, 속성 > 요소

- #### Box model

  - 모든 HTML 요소는 box 형태로 되어있음
  - 하나의 박스는 네 부분으로 이루어짐
    - content - 글이나 이미지 등 요소의 실제 내용
    - padding - 테두리 안쪽 내부 여백, 요소에 적용되는 배경색, 이미지는 padding까지 적용
    - border - 테두리 영역
    - margin - 테두리 바깥의 외부 여백, 배경색을 지정할 수 없음

- #### CSS Display

  - display : block
    - 줄 바꿈이 일어나는 요소 (다른 요소를 밀어낸다)
    - 화면 크기 전체의 가로 폭을 차지한다.
    - 블록 레벨 요소 안에 인라인 레벨 요소가 들어갈 수 있음.
  - display : inline
    - 줄 바꿈이 일어나지 않는 행의 일부 요소
    - content를 마크업 하고 있는 만큼만 가로 폭을 차지한다.
    - width, height, margin-top, margin-bottom을 지정할 수 없다.
    - 상하 여백은 line-height로 지정한다.