# JS
## JavaScript 요점 정리

> * [JavaScript란?](#JavaScript)
> * [변수](#변수)
>   * [var](#var)
>   * [let](#let)
>   * [const](#const)
> * [함수와 메서드](#함수와-메서드)
>   * [메서드(Method)](#메서드) 
>   * [함수(Function)](#함수)
>   * [함수 객체의 기본 프로퍼티(Property)](#함수-객체의-기본-프로퍼티)
>   * [함수 생성 방법](#함수-생성)
>       * [함수 선언(Function Declaration)](#함수-선언)
>       * [함수 표현식(Function Expression)](#함수-표현식)
>       * [Function() 생성자 함수](#Function()-생성자-함수)
>
> ### JavaScript
>   * 자바 스크립트에 대하여...
>
> ### 변수
> JavaScript에서는 변수 선언에 3가지 방법이 있다.  
> var, let, const가 있는데 이들의 차이점에 대해서 알아보자.
>
> ### var
> 초기의 변수는 var로 선언하였다.  
> 하지만 var에는 치명적인 단점이 존재한다.
>   ```javascript
>       var name = 'abcd'
>       console.log(name) // abcd
>   
>       var name = 'efg'
>       console.log(name) // efg
>   ```
> 변수를 한 번 더 선언했음에도 불구하고, 각기 다른 값이 출력된다.  
> 유연한 변수 선언에는 장점이 될 수 있지만 코드의 양이 늘어난다면 변수 파악이 힘들고 값이 변경될 우려가 있다.
> 그래서 ES6부터 let과 const가 등장하게 된다.
>
> ### let
> var 변수 때와 같이 같은 이름의 변수를 let으로 선언하면 아래와 같다.
>   ```javascript
>       let name = 'abcd'
>       console.log(name) // abcd
>   
>       let name = 'efg'
>       console.log(name) // efg
>       // Uncaught SyntaxError: Identifier 'name' has already been declared
>   ```
> 그 경우 name이 이미 선언되었다는 에러가 발생한다.(const도 마찬가지)  
> 그러면 const와의 차이점은 무엇일까?
> 바로 변수의 재할당이다.
>   ```javascript
>       let name = 'abcd'
>       console.log(name) // abcd
>   
>       name = 'efg'
>       console.log(name) // efg
>   ```
> 비슷한 예제이지만 name의 값을 'abcd'로 선언한 후 다시 'efg'로 바꾸어 주면 아무런 에러가 발생하지 않는다.
>
> ### const
> const의 경우에는 재선언과 재할당 둘 다 불가능하다.  
> let의 상황 처럼 name의 값을 재할당해보자.
>   ```javascript
>       const name = 'abcd'
>       console.log(name) // abcd
>   
>       name = 'efg'
>       console.log(name) // efg
>       //Uncaught TypeError: Assignment to constant variable.
>   ```
> TypeError가 발생하는 것을 확인할 수 있다.
>
> ### 함수와 메서드
>
> 자바스크립트에서 함수(function)는 실제로 자바스크립트 내장 객체인 Function 생성자로 생성된 객체이기 때문에 자바의 메서드(method)와는 매우 다르다. Fuction 자체가 또한 하나의 객체다.    
> #### 메서드
> 함수가 객체의 프로퍼티(property) 일 때.  
> 자바스크립트에서 메서드는 함수지만, 모든 함수가 메서드는 아니다.  
> 메서드는 앞의 객체에 this를 바인딩한다.  
> #### 함수
> 자바스크립트 내장 객체인 Function 생성자로 생성된 객체.  
> 자바스크립트의 함수는 값으로 취급된다.  
> #### 함수 객체의 기본 프로퍼티
> * length : 기대되는 인자의 개수
> * prototype : 프로토타입
> * name : 함수의 이름
> * caller : 자신을 호출한 함수
> * arguments : 함수를 호출할 때 전달된 인자값
> * ```__proto__``` : 자신의 프로토타입을 가리키는 내부 프로퍼티
> #### 함수 생성
> ##### 함수 선언
> * Function Declaration
>   ```js
>   function a() {
>      console.log("hi");
>   }
>   ```
> ##### 함수 표현식
> * Function Expression
>   ```js
>   let a = function () {
>      console.log("hi");
>   }
>   ```
> ##### Function() 생성자 함수
> Function() 생성자 함수로 선언 시 성능, 가독성이 떨어진다.
>   ```js
>   let a = new Function(arg1, arg2, ...argN, functionBody)
>   ```
>
> [함수 선언](#함수-선언)과 [함수 표현식](#함수-표현식)의 차이는 할당 여부이다.  
> 호이스팅 시 함수 선언은 함수가 올라가고 함수 표현식은 변수가 올라간다.  
> 함수 선언 시 같은 이름의 함수일 경우 덮어 씌어질 수 있기 때문에 함수 표현식 사용을 권장한다.  