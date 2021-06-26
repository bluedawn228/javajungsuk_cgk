# 23. 추상 클래스와 추상 메서드
## 디자인 패턴과 추상 클래스 - 템플릿 메서드 패턴
![image](https://user-images.githubusercontent.com/68311318/123498678-70ab0400-d66c-11eb-9928-75d2e6110b17.png)  
템플릿 메서드 패턴은 수퍼 클래스에서 추상적으로 표현하고, 서브 클래스에서 그 구체적인 내용을 결정하는 설계 방식을 말한다. 즉 수퍼 클래스에서 전체적인 `논리 흐름`을 정의하고, 서브 클래스에서 각 흐름에 따라 `구체적인 동작`을 정의한다.  

템플릿 메서드: 틀만 갖춘 상태  

**추상 클래스** 는 

- 서브 클래스에 기본 기능 및 공통 분모를 상속해 주는 역할을 하는 클래스다.
- new 명령을 통해 인스턴스를 생성할 수 없다.
- **상속** 의 기법 중에서 **일반화** 를 통해 수퍼 클래스를 정의한 경우 보통 추상 클래스로 선언한다.
- 추상 메서드를 가질 수 있다.

**추상 메서드** 는 

- 서브 클래스에 따라 구현 방법이 다른 경우 보통 추상 메서드로 선언한다.
- 서브 클래스에서 반드시 구현해야 하는 메서드다.
- 즉 서브 클래스를 정의할 때 반드시 해당 메서드를 구현하도록 강제하고 싶다면 추상 메서드로 선언한다.
- 일반 클래스는 추상 메서드를 가질 수 없다. 
- 추상 클래스와 인터페이스 만이 추상 메서드를 가질 수 있다.