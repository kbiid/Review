## Cloneable , clone
- 모든 클래스의 부모인 Object 클래스는 객체의 클로닝을 위한 Object.clone() 메소드를 제공하고 있다. 객체의 복사는 객체 생성의 또 다른 방법으로 new 연산자를 통한 객체 생성 이외의 다른 방법을 제공한다. 클로닝을 통한 객체 복사를 통해서 객체를 생성할 경우 객체의 생성자 메소드를 실행하지 않으며, 객체가 유지하고 있는 상태값들을 그대로 복사하게 된다. 복사되는 원래 객체에는 아무런 변화도 주지 않는다. Object.clone() 메소드는 객체 구조를 복사하지만 객체 레퍼런스의 경우 레퍼런스만 복사한다. 즉, 객체 레퍼런스가 가리키고 있는 실제 객체는 복사하지 않는다. 이것을 shallow cloning이라고 하며, 레퍼런스로 가리키는 객체까지 모두 복사하는 deep cloning와 구별된다.
- shallow cloning은 primitive 타입이나 immutable한 것들에 사용하는 것이 좋다. 
- deep cloning을 위해서는 clone()을 오버라이딩 할 때 고려하여 코드를 작성하여야 한다.

## equals, hashcode
- equals는 두 객체의 내용이 같은지, 동등성을 비교하는 연산자. default로 primitive type은 내용이 같은지 검사하고, reference type은 객체의 주소가 같은지 검사한다. 
- hashCode는 두 객체가 같은 객체인지, 동일성을 비교하는 연산자
- equals()를 재정의할 때는 equals()와 hashCode()를 함께 재정의 해야만 부작용이 없다. equals로 같은 객체라면 hashCode도 같은 값이여야만 한다. 하지만 반대로 hashCode가 같은 값이더라도 equals도 같은 객체가 아닐 수 있다는 것을 유의해야 한다. 
