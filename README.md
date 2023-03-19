# Web ( HTML, CSS, JS)

- ## HTML ( Hyper Text Markup Language)

  - 참조 (하이퍼링크)를 통해 사용자가 한 문서에서 다른 문서로 즉시 접근할 수 있는 텍스트
  - Markup Language - 태그 등을 이용해 문서나 데이터의 구조를 명시하는 언어
    - HTML, Markdown
  - 웹 페이지를 작성(구조화) 하기 위한 언어



- #### HTML 기본 구조

  - html : 문서의 최상위(root) 요소
  - head : 문서 메타데이터 요소
    - 문서 제목, 인코딩, 스타일, 외부 파일 로딩 등
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

  ![001](images\001.png)

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

- #### CSS Layout

  - 웹 페이지의 구성 > 박스모델의 집단

- #### Float

  - 박스를 왼쪽 혹은 오른족으로 이동시켜 텍스트를 포함 인라인요소들이 주변을 감싸도록 함
  - 요소가 Normal flow를 벗어나도록 함 > 공간을 차지하지 않는듯 ? 같은 자리의 블럭을 덮음
  - float : left,right > 왼쪽, 오른쪽으로 몰아서 정렬
  - Float은 레이아웃을 구성하기 위해 필수적으로 활용 되었으나, 최근 Flexbox, Grid 등장과 함께 사용도가 낮아짐
  - Float 활용 전략 - Normal Flow에서 벗어난 레이아웃 구성
    - 원하는 요소들을 Float로 지정하여 배치

- #### Flexbox

  - 행과 열 형태로 아이템들을 배치하는 1차원 레이아웃 모델
  - 축
    - main axis (메인 축)
    - cross axis (교차 축)
  - 구성 요소
    - Flex Container (부모 요소)
    - Flex Item (자식 요소)

  <img src="images\image-20230309092631465.png" alt="image-20230309092631465" style="zoom:80%;" />

  - Flexbox 축
    - flex-direction : row
  - Flexbox 구성 요소
    - Flex Container (부모 요소)
      - flexbox 레이아웃을 형성하는 가장 기본적인 모델
      - Flex Item들이 놓여있는 영역
      - display 속성을 flex 혹은 inline-flex로 지정
    - Flex Item (자식 요소)
      - 컨테이너에 속해 있는 컨텐츠(박스)

- #### Flexbox 속성

  - ##### justify-content

    - Main axis 기준으로 공간 배분

  - ##### align-content

    - Cross axis 기준으로 공간 배분 (아이템이 한 줄로 배치되는 경우 확인할 수 없음)

  ![image-20230309100524398](images\image-20230309100524398.png)

  <img src="images\image-20230309101631292.png" alt="image-20230309101631292" style="zoom:80%;" />

  - ##### align-items

    - 모든 아이템을 Cross axis를 기준으로 정렬

  <img src="images\image-20230309100650162.png" alt="image-20230309100650162" style="zoom:80%;" />

  - ##### align-self

    - 개별 아이템을 Cross axis 기준으로 정렬 
      - 주의 ! 해당 속성은 컨테이너에 적용하는 것이 아니라 개별 아이템에 적용

  

  - ##### Cross axis를 중심으로

    - stretch : 컨테이너를 가득 채움
    - flex-start : 위
    - flex-end: 아래
    - center : 가운데
    - baseline : 텍스트 baseline에 기준선을 맞춤

  - <img src="images\image-20230309100712881.png" alt="image-20230309100712881" style="zoom:80%;" />

  - #####  기타 속성

    - flex-grow : 남은 영역을 아이템에 분배
    - order : 배치 순서