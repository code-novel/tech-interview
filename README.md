## JAVA 공부

### :book: - List

* [JAVA의 장단점](#JAVA의-장단점)
* [OOP(Object-Oriented Programming)](#OOP)
* [OOP의 5대 원칙](#OOP의-5대-원칙)
* [Data Type](#Data-Type)
* [static 변수](#static-변수)
* [Overloading vs Overriding](#Overloading-vs-Overriding)
* [MVC 패턴](#MVC-패턴)
*
*
*

### JAVA의 장단점
>* 장점
>   - 운영체제에 독립적이다 -> JVM에서 동작하기 때문에 특정 운영체제에 종속되지 않음.
>   - [객체지향 언어](#)
>   - 자동으로 메모리를 관리(Garbage Collector)
>   - Open Source->많은 개발자, 라이브러리
>   - Multi-Thread
>   - 동적 로딩(Dynamic Loading)을 지원
>* 단점
>   - 속도가 느리다.(JVM에 의해 기계어로 번역되고 실행되는 과정을 거치기 때문에)
>   - 예외처리가 느리다.(프로그래머 검사가 필요한 예외가 발생한다면 프로그래머가 선언해줘야 한다.)

### OOP
>* OOP(Object-Oriented Programming)의 약자
>* 오브젝트를 기준으로 코드를 나누어 구현하는 프로그래밍 방법 -> 객체 지향 프로그래밍  
>* JAVA의 경우에는 구분 단위가 CLASS  
>   - 캡슐화(Encapsulation) : 정보 은닉(infoamation hiding) 필요가 없는 정보는 외부에서 접근하지 못하도록 제한하는 것
>   - 상속(Inheritance) : 기존 CLASS의 변수와 메소드를 그대로 가지면서 추가적인 기능도 가지는 CLASS를 새로 만드는 것
>   - 추상화(Abstraction) : 구체적인 사물들의 공통적인 특징을 파악해서 이를 하나의 개념(집합)으로 다루는 것
>   - 다형성(Polymorphism) : 서로 다른 클래스의 객체가 같은 메세지를 받았을 때 각자의 방식으로 동작하는 능력

### OOP의 5대 원칙
> "SOLID" 원칙
>
>   * S : 단일 책임 원칙(SRP, Single Responsibility Principle)
>       * 객체는 단 하나의 책임만 가져야 한다.
>   * O : 개방-폐쇄 원칙(OCP, Open Closed principle)
>       * 기존의 코드를 변경하지 않으면서 기능을 추가할 수 있도록 설계가 되어야 한다.
>   * L : 리스코프 치환 원칙(LSP, Liskov Substitution Principle)
>       * 일반화 관계에 대한 이야기며, 자식 클래스는 최소한 자신의 부모 클래스에서 가능한 행위는 수행할 수 있어야 한다.
>   * I : 인터페이스 분리 원칙(ISP, Interface Segregation Principle)
>       * 인터페이스를 클라이언트에 특화되도록 분리시키라는 설계원칙이다.
>   * D : 의존 역전 원칙(DIP, Dependency Inversion Principle)
>       * 의존 관계를 맺을 때 변화하기 쉬운 것 또는 자주 변화하는 것 보다는 변화하기 어려운 것, 거의 변화가 없는 것에 의존하라는 것이다.

### Data Type
> 1. 기본 데이터 타입(Primitive Data Type)
>       * 정수형 : byte, short, int, long
>       * 실수형 : float, double
>       * 논리형 : boolean(true/false)
>       * 문자형 : char
>       기본 타입의 크기가 작고 고정적이기 때문에 메모리의 Stack영역에 저장된다.
>
> 2. 참조 타입(Reference Data Type)
>       * 기본형을 제외하고는 모두 참조형
>       * new 키워드를 이용하여 객체를 생성하여 데이터가 생성된 주소를 참조
>       * String, StringBuffer, List, Class 등
>       * String과 배열은 참조 타입과 달리 new 없이 생성이 가능 하지만 기본 타입이 아닌 참조 타입
>       * 참조 타입의 데이터의 크기가 가변적, 동적이기 때문에 동적으로 관리되는 Heap 영역에 저장된다.
>       * 더 이상 참조하는 변수가 없을 때 가비지 컬렉션에 의해 파괴된다.
>       * 참조 타입은 값이 저장된 곳의 주소를 저장하는 공간으로 객체의 주소를 저장(Call-By-Value)

### static 변수
>   * static 멤버
>       * 공간적 특성 : 멤버는 클래스당 하나가 생성
>           * 멤버는 객체 내부가 아닌 별도의 공간에 생성
>           * CLASS 멤버라고 부른다.
>       * 시간적 특성 : CLASS 로딩 시에 멤버가 생성된다.
>           * 객체가 생기기 전에 이미 생성된다.
>           * 객체가 생기기 전에도 사용이 가능하다. (즉, 객체를 생성하지 않고도 사용할 수 있다.)
>           * 객체가 사라져도 멤버는 사라지지 않는다.
>           * 멤버는 프로그램이 종료될 때 사라진다.
>       * 공유의 특성 : 동일한 클래스의 모든 객체들에 의해 공유된다.
>   * non-static 멤버
>       * 공간적 특성 : 멤버는 객체마다 별도로 존재
>           * 인스턴스 멤버라고 부른다.
>       * 시간적 특성 : 객체 생성 시에 멤버가 생성된다.
>           * 객체가 생길 때 멤버도 생성
>           * 객체 생성 후 멤버 사용이 가능
>           * 객체가 사라지면 멤버도 사라진다.
>       * 공유의 특성 : 공유되지 않는다.
>           * 멤버는 객체 내에 각각의 공간을 유지한다.

### Overloading vs Overriding
> Overloading :  
> Overriding :  

### MVC 패턴(Model, View, Controller)
>   1. Model  
>*   프로그램의 내부 상태, 즉 프로그램의 정보(데이터)를 말하는 것이다.
>   2. Controller  
>*  데이터와 비지니스 로직 간의 상호 작용을 뜻함.
>   3. View
>*  사용자 인터페이스 요소를 뜻하는데, 유저에게 보여지는 것을 말한다.
>
> MVC2 패턴



### Interface
### Abstract Class
### Generic
### FrameWork
### Library
### 접근 제어자
### final
### singleton
