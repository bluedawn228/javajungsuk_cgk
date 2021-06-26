# 25. `Iterator` 디자인 패턴

**반복자(Iterator) 패턴** 은 

- 객체 목록을 관리하는 컬렉션(collection)에서 
  `목록 조회 기능`을 별도의 객체로 캡슐화하는 설계 기법이다.
- 컬렉션의 관리 방식(data structure)에 상관없이 일관된 목록 조회 방법을 제공할 수 있다.
- 컬렉션을 변경하지 않고도 다양한 방식의 목록 조회 기법을 추가할 수 있다.  

![image](https://user-images.githubusercontent.com/68311318/123500417-df8e5a00-d678-11eb-976d-691f2793e41d.png)  
Stack아 너 조회할래 -> Stack : 내가 안해 iterator 줄게  

![image](https://user-images.githubusercontent.com/68311318/123501288-ddc79500-d67e-11eb-8848-45dca86b1022.png)  
Stack은 pop(), Queue는 poll(), LinkedList와 AraryList는 get(). 이처럼 이 자료구조들은 값을 꺼낼때마다 호출하믄 메서드가 다르다. 즉, 목록을 따라가면서 값을 조회(순차적으로 조회한다; iterator)하는 방법이 컬렉션의 타입에 따라 다르다(호출하는 메서드가 다르다). 따라서 프로그래밍에 일관성이 없다는 문제점이 있다. 순차적으로, 반복적으로 따라가면서 값을 조회하는 것을 영어로 하면 Iterator이다. 컬렉션의 타입이 다르더라도 목록을 따라가면서 값을 조회하는 방법을 같게 해야 한다. 이 뜻은 메서드 시그너처를 통일한다는 것이고, 호출 규칙을 정의한다는 것이다. 호출 규칙을 정의할 때 사용하는 문법이 Interface이다.  

컬렉션이 제공한 대리자를 통해서 컬렉션의 값을 조회하자. 이 대리자를 iterator라고 부른다. 클라이언트는 대리자를 사용규칙에 따라 사용함으로써 프로그래밍의 일관성을 유지할 수 있다.  
"있나요?"라고 물어보고(hasNext()), "한 개 주세요" next()).  
![image](https://user-images.githubusercontent.com/68311318/123501510-701c6880-d680-11eb-9d53-ef91aa6efe7b.png)  
Caller입장에서는 자신이 사용하는 객체(여기선 컬렉션)가 어떤 객체인지 알 필요가 없어지는 것이다! 일상에서도 마찬가지이다. 택시를 탈 때 기사가 누구인지 정확히 알 수 없어도 '운전기사'라는 레퍼런스로 소통할 수 있다. 그 사람이 누군지 정확히 알지 않아도 우리는 소통할 수 있다. "저기요", 아주머니"와 같은 보다 추상적인 명칭으로 부르면 되기 때문에 일상이 편해진다.  

프로그래밍도 일상 생활과 똑같다. 이렇게 될 경우 `직접적인 종속이 발생하지 않는다`. BoardHandler 가 쓰는 객체는 LinkedList 객체가 맞지만, LinkedList가 아니더라도 LinkedList와 같은 규칙으로 만든 객체를 사용한다면 이 규칙에 따라 메서드를 호출하면 되는 것이다. 

한편 AbstractList의 경우 ListIterator를 `직접 사용`하기 때문에 `이 객체에 대해 정확하게 알아야 한다.` 그러나 프로젝트에서 ListIterator를 직접 사용하는 클래스는 AbstractList뿐이다. 따라서 일반 패키지 레벨 클래스(top level class)로 선언하지 말고 중첩 클래스로 바꿔 유지 보수를 용이하게 하자.  
