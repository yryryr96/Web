# JavaScript ( JS )

#### JS 란 ? HTML 문서를 동적으로 변경할 수 있는 언어

- 특정 상황에서 html 문서를 다르게 (동적) 보여주기 위한 언어
- HTML 이 없다면 JS는 무용지물



- #### var

  - 생략 가능

  - 변수 호이스팅

  - 암묵적 결합(중복 선언 가능)

  - 재할당, 재선언 가능

  - 함수 레벨 스코프

  - ```js
    // 함수레벨 스코프
    function foo() {
        var x = 5
        console.log(x) // 5
    }
    
    console.log(x) // ReferenceError : x is not defined
    ```

    

  

- #### let

  - 생략 불가능

  - 변수 호이스팅이 동작하지 않는 것 처럼 동작

  - 재선언 불가 ( 재할당은 가능 )

  - 블록 레벨 스코프

  - ```javascript
    // 가능
    let number = 10
    number = 20 
    
    // 불가능
    let number = 10
    let number = 20
    ```

    

- #### const 

  - 생략 불가능
  
  - 변수 호이스팅이 동작하지 않는 것 처럼 동작
  
  - 재선언 불가 (재할당 불가)
  
  - 블록 레벨 스코프
  
  - ```javascript
    // 재할당도 불가능
    const number = 10
    number = 10
    
    // 재선언도 불가능
    const number = 10 
    const number = 20
    ```
  
    

- #### 블록 스코프

  - ```js
    let x = 1
    
    if (x==1){
        let x = 2
        console.log(x) // 2
    }
    console.log(x) // 1
    ```



- #### 호이스팅 (hoisting) 

  - 변수를 선언 이전에 참조할 수 있는 현상
  - var로 선언된 변수는 선언 이전에 참조할 수 있으며, 이러한 현상을 호이스팅이라 한다.
  - 변수 선언 이전의 위치에서 접근 시 undefined를 반환
  - 인터프리터가 변수와 함수의 메모리 공간을 선언 전에 미리 할당하는 것 > 변수의 선언과 초기화를 분리한 후, 선언만 코드의 최상단으로 옮기는 것

  ```js
  // 과정 1
  console.log(name) // undefined
  var name = '홍길동' // 선언
  
  // 과정 2 : 과정 1이 해석되는 형태
  var name // undefined로 초기화
  console.log(name)
  name = '홍길동'
  
  // name이라는 변수가 undefined라는 주소를 참조하고 있다가 name='홍길동' 으로 초기화가 되면 참조하는 주소를 변경
  ```

  

- #### 데이터 타입 ( Data Type )

![image-20230418230624194](images\image-20230418230624194.png)

- ##### null 

  - null 값을 나타내는 특별한 키워드
  - 변수의 값이 없음을 의도적으로 표현할 때 사용

- ##### undefined

  - 값이 정의되어 있지 않음을 표현하는 값
  - 변수 선언 이후 직접 값을 할당하지 않으면 자동으로 할당 된다.



- #### 참조 타입 (Reference Type)

  - Object( 객체 ) : 이름과 값을 가진 속성(property)들의 집합으로 이루어진 자료구조 -> 중괄호 내부에 key,value 쌍으로 표현

  - Array (배열) : 순서를 보장, 배열의 길이는 array.length 로 접근 가능 -> 배열의 마지막 값 array[array.length-1]

  - Function (함수) 

    - 함수 선언식

    - ```js
      function add(num1,num2) {
          return num1+num2
      }
      add(2,7) // 9
      ```

    - 함수 표현식

    - ```js
      const sub = function(num1,num2) {
          return num1 - num2
      }
      sub(7,2) // 5
      
      // 함수의 이름이 없다 : 익명 함수
      // 함수의 이름 명시 가능 -> 호출로는 못쓰고 디버깅용도
      const mySub = function namedSub(num1,num2) {
          return num1-num2
      }
      
      mySub(1,2) // -1
      namedSub(1,2) // ReferenceError : namedSub is not defined
      ```



- ### this

  - 어떤 object를 가리키는 키워드 ( python : self, java : this )

  - 함수를 호출할 때 함수가 어떻게 호출 되었는지에 따라 동적으로 결정된다.

  - obj.functioncall () -> this ===obj, 나머지 this === window object(global)

  - ```js
    // 함수 문맥에서 this
    
    // Nested (Function 키워드)
    const myObj = {
        numbers: [1],
        myFunc() {
            console.log(this) // myObj
            this.numbers.forEach(function (num){
                console.log(num) // 1
                console.log(this) // window
            })
        }
    }
    // 단순 호출 방식으로 사용됐을 때 this 는 전역 객체 window를 가리킴
    
    // Nested (Arrow Function)
    const myObj = {
        numbers: [1],
        myFunc(){
            console.log(this) // myObj
            this.numbers.forEach((number) => {
                console.log(number) // 1
                console.log(this) // myObj
            })
        }
    }
    // 자동으로 한 단계 상위의 scope의 context를 바인딩, 여기서 this는 자신을 감싼 정적 범위
    ```



- ### 객체 관련 문법

- ```js
  const person = {
      name : 'victor',
      age : 30,
      greeting : function() {
          console.log(`hello,my name is ${this.name}.`)
      }
  }
  
  console.log(person.name)
  console.log(person['age'])
  person.greeting()
  
  function Member(name,age,sId) {
      this.name = name
      this.age = age
      this.sId = sId
  }
  
  // 클래스 같은 느낌인가?
  const member3 = new Member('isaac',20,1231290312)
  console.log(member3)
  
  // 속성명 축약
  const books = ['Learning','JavaScript']
  const magazines = ['Vogue','Science']
  
  const bookshop = {
      books,
      magazines,
  }
  
  console.log(bookshop)
  
  //메서드명 축약
  const obj = {
      greeting() {
          console.log('Hi')
      }
  }
  obj.greeting()
  
  // 객체를 정의할 때 key의 이름을 동적으로 생성 가능
  const key = 'country'
  const value = ['korea','japan','france','china']
  
  const Obj = {
      [key] : value,
  }
  
  console.log(Obj) // country : ['korea','japan','france','china']
  console.log(Obj.country) // ['korea','japan','france','china']
  
  // 구조 분해 할당
  const userInformation = {
      name : 'ssafy kim',
      userId : 'ssafyStudent1234',
      email : 'ssafy@ssafy.com'
  }
  
  const {name,userId,email} = userInformation
  // const name = userInformation.name
  console.log(name,userId,email) // ssafy kim ssafyStudent1234 ssafy@ssafy.com
  
  // Spread syntax(...)
  const OBJ = { b:2,c:3,d:4 }
  const newOBJ = {a:1, ...OBJ, e : 5}
  console.log(newOBJ) // {a:1, b:2, c:3, d:4, e:5}
  ```



- ### JSON (JavaScript Object Notation)

  - key-value 형태로 이루어진 자료 표기법
  - JS의 Object와 유사한 구조이지만 JSON 은 형식이 있는 문자열
  - JSON을 Object로 사용하기 위한 변환 작업이 필요

```js
// JSON 변환
const jsObject = {
    coffee : 'Americano',
    iceCream : 'Cookie and Cream',
}

// Obj -> JSON
const objToJson = JSON.stringify(jsObject)

console.log(jsObject)
console.log(objToJson)
console.log(typeof objToJson) // String

//JSON -> Obj
const jsonToObj = JSON.parse(objToJson)
console.log(jsonToObj)
console.log(typeof jsonToObj) // Object
```
