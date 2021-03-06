## 생성 패턴
- 생성 패턴(Creational Pattern)은 인스턴스를 만드는 절차를 추상화하는 패턴이다. 이 범주에 해당하는 패턴은 객체를 생성 합성하는 방법이나 객체의 표현 방법과 (소트프웨어) 시스템을 분리해 준다.
  <ul>
  <li>클래스 생성 패턴 : 인스턴스로 만들 클래스를 다양하게 만들기 위한 용도로 상속을 사용함</li>
  <li>객체 생성 패턴 : 인스턴스화 작업을 다른 객체에게 떠넘김</li>
  </ul>
- 생성 패턴의 특징
  <ul>
    <li>생성 패턴은 시스템이 어떤 클래스를 사용하는 지에 대한 정보를 캡슐화 한다.</li>
    <li>생성 패턴은 이들 클래스의 인스턴스들이 어떻게 만들고 어떻게 서로 맞붙는지에 대한 부분을 완전히 숨긴다.</li>
  </ul>
- 생성 패턴을 이용하면 무엇이 생성되고 누가 이것을 생성하며, 이것이 어떻게 생성되는지, 언제 생성할 것인지 결정하는데 유연성을 확보할 수 있게 된다.

## 추상 팩토리(Abstract Factory Pattern)
- 팩토리 메서드 패턴과의 차이점
  <ul>
    <li>팩토리 메서드 패턴 : 조건에 따른 객체 생성을 팩토리 클래스로 위임하여, 팩토리 클래스에서 객체를 생성하는 패턴</li>
    <li>추상 팩토리 패턴 : 서로 관련이 있는 객체들을 통째로 묶어서 팩토리 클래스로 만들고, 이들 팩토리를 조건에 따라 생성하도록 다시 팩토리를 만들어 객체를 생성하는 패턴</li>
  </ul>
- 추상 팩토리 패턴은 팩토리 메서드 패턴을 좀 더 캡슐화한 방식이라고 볼 수 있다. 추상 팩토리 패터이 팩토리 메서드 패턴의 상위호환은 아니다.

