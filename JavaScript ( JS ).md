# JavaScript ( JS )

#### JS 란 ? HTML 문서를 동적으로 변경할 수 있는 언어

- 특정 상황에서 html 문서를 다르게 (동적) 보여주기 위한 언어
- HTML 이 없다면 JS는 무용지물



- #### var

  - 생략 가능

  - 변수 호이스팅 ( 선언과 초기화가 동시에 진행)

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

  - 변수 호이스팅이 동작하지 않는 것 처럼 동작 ( 실질적으로는 동작, 선언과 초기화가 따로 진행)

  - 재선언 불가 ( 재할당은 가능 )

  - 블록 레벨 스코프

  - ```javascript
    // 재할당 가능
    let number = 10
    number = 20 
    
    // 재선언 불가능
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

    <img src="images\image-20230426121456140.png" alt="image-20230426121456140" style="zoom: 67%;" />

  <img src="images\image-20230426121532621.png" alt="image-20230426121532621" style="zoom:67%;" />

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

  - 식별자를 선언 이전에 참조할 수 있는 현상
  - var로 선언된 변수는 선언 이전에 참조할 수 있으며, 이러한 현상을 호이스팅이라 한다.
  - 인터프리터가 변수와 함수의 메모리 공간을 선언 전에 미리 할당하는 것 > 변수의 선언과 초기화를 분리한 후, 선언만 코드의 최상단으로 옮기는 것
  
  ```js
  // 과정 1
  console.log(name) // undefined
  var name = '홍길동' // 선언
  
  // 과정 2 : 과정 1이 해석되는 형태
  var name // undefined로 초기화
  console.log(name)
  name = '홍길동'
  ```
  
  
  
- #### 데이터 타입 ( Data Type )

![image-20230418230624194](images\image-20230418230624194.png)

- ##### null 

  - null 값을 나타내는 특별한 키워드
  - 변수의 값이 없음을 **의도적**으로 표현할 때 사용

- ##### undefined

  - 값이 정의되어 있지 않음을 표현하는 값
  - 변수 선언 이후 직접 값을 할당하지 않으면 자동으로 할당 된다.
  - 개발자들의 실수를 넘어가주기 위해 사용(?)



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
      
      // 함수 호이스팅
      add(2,7)
      function add(num1, num2) {
          return num1 + num2
      	}   
      // 호이스팅이 일어난다면 함수 호이스팅
      ```
      
    - 함수 표현식
    
    - ```js
      const sub = function(num1,num2) {
          return num1 - num2
      	}
      sub(7,2) // 5
      // 호이스팅이 일어나면 변수 호이스팅
      // 함수의 이름이 없다 : 익명 함수
      // 함수의 이름 명시 가능 -> 호출로는 못쓰고 디버깅용도
      const mySub = function namedSub(num1,num2) {
          return num1-num2
      	}
      
      mySub(1,2) // -1
      namedSub(1,2) // ReferenceError : namedSub is not defined
      
      sub(7,2)
      const sub = function(num1,num2) {
          return num1 - num2
      	}
      // 변수 호이스팅
      ```

​     

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
    // 자동으로 한 단계 상위의 scope의 context를 바인딩, 여기서 this myFunc()의 this와 동일한 myObj
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
  
  console.log(person.name)	//victor
  console.log(person['age'])	// 30
  person.greeting()			// hello,my name is victor
  
  function Member(name,age,sId) {
      this.name = name
      this.age = age
      this.sId = sId
  }
  
  // 클래스 같은 느낌인가? new 가 붙으면 생성자 함수로 동작
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



- ### DOM ( Document Object Model )

  - 문서의 구조화된 표현을 제공하며 프로그래밍 언어가 DOM 구조에 접근할 수 있는 방법을 제공
  - HTML 문서를 구조화 하여 각 요소를 객체로 취급



- ### EVENT

  - HTML 요소에서 발생하는 모든 상황
  - 예시 : 키보드 키 입력, 브라우저 닫기, 데이터 제출, 텍스트 복사 등등

- Event object

  - 네트워크 활동이나 사용자와의 상호작용 같은 사건의 발생을 알리기 위한 객체
  - 이벤트가 발생했을 때 생성되는 객체
  - DOM 요소는 Event를 받고 ("수신")
  - 받은 Event를 "처리" 할 수 있음
    - Event 처리는 주로 addEventListener() 메서드를 통해 Event 처리기를 다양한 html 요소에 "부착"해서 처리
  - " **대상**에 **특정 Event**가 발생하면, **할 일**을 등록하자"
  - **EventTarget**.addEventListener(**type**, **handler function**)



- ### 동기와 비동기

  - #### 동기 ( Synchronous )

    - 모든 일을 순서대로 하나씩 처리하는 것
    - python 코드 처럼 작동

    

  - #### 비동기식 ( Asynchronous )

    - 작업을 시작한 후 결과를 기다리지 않고 다음 작업을 처리하는 것 ( 병렬적 수행 )
    - 끝나는 시간이 일정하지 않다.



- ### JavaScript의 비동기 처리 

  - JavaScript는 한 번에 하나의 일만 수행할 수 있는 Single Thread 언어이다.

```markdown
Thread ?
작업을 처리할 때 실제로 작업을 수행하는 주체
프로그램 -> 파일 -> 프로세스 -> Thread (처리)
```



- ### 비동기 처리 동작 방식 

1. 모든 작업은 Call Stack(LIFO) 으로 들어간 후 처리된다.
2. 특정 작업이 Call Stack으로 들어오면 Web API로 보내 별도로 처리하도록 한다.

3. Web API에서 처리가 끝난 작업들은 곧바로 Call Stack으로 들어가지 못하고 Task Queue(FIFO)에 순서대로 들어간다.
4. Event Loop가 Call Stack이 비어 있는 것을 계속 체크하고 Call Stack이 빈다면 Task Queue에서 가장 오래된 (가장 앞에 있는) 작업을 Call Stack으로 보낸다.

```Js
console.log('Hi')

setTimeout(function ssafy() {
    console.log('SSAFY')
},3000)
console.log('Bye')

1. Call Stack 에 console.log('Hi') 저장 -> 바로 출력
2. ssafy() CallStack에 저장 -> Web API 넘겨야 하는것들은 Web API에 저장 (3초) (0초여도 마찬가지)
3. console.log('Bye') Call Stack에 저장 -> 바로 출력
4. Web API 에서 Task Queue 로 ssafy() 저장 -> Call Stack 비어있는지 확인 후 비었다면 실행
```



- ### 비동기 처리의 단점

  - 비동기 처리의 핵심은 작업이 완료되는 순서에 따라 처리한다는 것

  - 코드의 실행 순서가 불명확하다는 단점이 있다.

    - 이를 해결하기 위해 콜백 함수를 썼는데 가독성, 유지보수 측면에서 사용 불편 -> Promise

    - ##### Callback 함수란 ?

      - 다른 함수의 인자가 되거나 특정 함수가 시작되기 전에 실행되지 않는 함수
  
  - ##### Promise (Web API 안에서 순서를 정하기 위해 사용??)
  
    - 비동기 작업의 완료 또는 실패를 나타내는 객체
    - ##### then(callback)
    
      - 요청한 작업이 성공하면 callback 실행
      - callback은 이전 작업의 성공 결과를 인자로 전달 받는다.
    - ##### catch(callback)
    
      - then()이 하나라도 실패한다면 callback 실행
      - callback은 이전 작업의 실패 객체를 인자로 전달 받는다.

![image-20230425103101137](images\image-20230425103101137.png)
