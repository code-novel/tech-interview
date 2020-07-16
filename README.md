# JS
## JavaScript 요점 정리

> * [JavaScript란?](#JavaScript)
> * [변수](#변수)
>   * [var](#var)
>   * [let](#let)
>   * [const](#const)
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