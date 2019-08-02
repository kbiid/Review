## SOA란
- Service Oriented Architecture. 기존의 애플리케이션들의 기능들을 비즈니스적인 의미를 가지는 기능 단위로 묶어서 표준화된 호출 인터페이스를 통해서 서비스라는 소프트웨어 컴포넌트 단위로 재조합한 후, 이 서비스들을 서로 조합하여 업무 기능을 구현한 애플리케이션을 만들어내는 소프트웨어 아키텍처.
- 대규모 컴퓨터 시스템을 구축할 때의 개념으로 업무상의 일 처리에 해당하는 소프트웨어 기능을 서비스로 판단하여 그 서비스를 네트워크 상에 연동하여 시스템 전체를 구축해 나가는 방법론이다.
- 기존의 시스템이 각각의 독립된 업무 시스템으로 개발되었던 반면 SOA는 기업의 전체 업무가 하나의 거대한 SOA시스템으로 구성이 된다.
- 각각의 시스템의 기능들을 업무 기준으로 주요 기능들로 묶어서 플랫폼에 독립적인 인터페이스(예를 들어 XML/HTTP, CORBA, SOAP)를 구현하여 외부로 서비스를 제공한다.

## 구성요소
<ul>
  <li>서비스 사용자(Service Consumer) : '서비스 제공자'에 의해 제공되고 있는 하나 이상의 서비스를 사용</li>
  <li>서비스 제공자(Service Provider) : '서비스 사용자'가 호출 시 입력하는 값을 가공하여 해당되는 결과를 제공. 경우에 따라서 '서비스 제공자'는 또 다른 '서비스 제공자'의 서비스를 사용하는 '서비스 사용자'가 될 수 있음</li>
  <li>서비스 레지스트리(Service Registry) : 서비스에 대한 설명정보(description)를 저장. '서비스 제공자'는 자신이 제공하고 있는 서비스를 등록하고, '서비스 사용자'는 자신이 원하는 서비스를 발견하여 사용함.</li>
</ul>

### 서비스
- 명확한 기능적인 의미를 지닌 소프트웨어 컴포넌트로, 고차원의 비즈니스 개념을 캡슐화 하고 있는 것을 말한다.
- 서비스는 인터페이스, 규약, 구현체 3가지로 구성되어 있다.
- 인터페이스는 서비스내의 하나의 업무 기능을 이야기 한다. 그리고 이 서비스를 사용하기 위한 여러가지 규약들(데이터 포맷, 변수형, 서비스 호출을 위한 인자, 인터페이스 이름 등) 정의되는 곳이 서비스 규약(contract)이다. 이에 대한 실제 구현체가 있다.
- SOA의 관점에서 서비스는 인터페이스를 통해 자신이 가진 비즈니스 프로세스를 처리할 수 있는 컴포넌트로 정의된다. 서비스는 인터페이스와 구현 부분으로 구성된다. 서비스가 가지는 특징을 다음 3가지로 요약할 수 있다.
  <ul><li>서비스의 인터페이스는 플랫폼에 독립적이다.</li>
    <li>서비스는 동적으로 검색될 수 있으며, 호출될 수 있다.</li>
    <li>서비스는 self-contained하다. 즉, 자신의 상태를 스스로 유지한다.</li></ul>
    
### 메시지
- 서비스 제공자와 서비스 사용자는 통해 서로 통신한다. 서비스 제공자는 서비스 명세를 통해 자신이 가진 서비스의 인터페이스를 공개하는데, 이 명세 내에는 서비스가 제공하는 기능과 이를 이용하기 위해 사용자와 주고 받아야 하는 메시지의 형식이 정의되어 있다. SOA의 관점에서 서비스는 플랫폼 독립적이어야 하므로, SOA에서 정의되는 메시지는 특정 기술에 독립적이어야 한다.

### 서비스 발견
- 서비스 사용자가 서비스 레지스트리로부터 자신의 원하는 서비스 제공자를 찾는 작업을 말한다. 이를 위해서는 서비스 레지스트리는 서비스를 등록하고 발견하는 기능을 제공해야 한다. 서비스 레지스트리는 다음과 같은 요구사항을 만족해야 한다.
  <ul><li>서비스의 확장성(scalability) 보장</li>
      <li>서비스 사용자와 제공자의 분리(decoupling)</li>
      <li>서비스의 동적인 변경 기능 제공(hot update)</li>
      <li>서비스 사용자를 위한 검색 기능 제공(동적인 검색 기능 포함)</li></ul>

## EAI
- Enterprise Architecture Integration. 기업 애플리케이션 통합. 기업용 응용 프로그램의 구조적 통합 방안을 가리킨다. 전사적 응용 프로그램 통합이라고도 한다.

## ESB
- ESB = SOA + EAI
- Enterprise Service Bus. ESB는 SOA를 지원하는 서비스와 응용 컴포넌트간의 연동을 지원한다. 즉, ESB는 SOA를 구현할 수 있게 해주는 실체로, Loosely coupled의 ansynchronous 메세지 방식의 SOA를 위한 라우팅 알고리즘을 제공한다. 
- 엔터프라이즈 미들웨어를 인프라로 하여 다양한 이질적 기업 환경(애플리케이션, 데이터, 플랫폼 및 네트워크 등)을 통합하여 하나의 시스템으로 관리 운영할 수 있는 유기적인 시스템

## 참고
- https://sarc.io/index.php/miscellaneous/742-soa-service-oriented-architecture
- https://ko.wikipedia.org/wiki/%EC%84%9C%EB%B9%84%EC%8A%A4_%EC%A7%80%ED%96%A5_%EC%95%84%ED%82%A4%ED%85%8D%EC%B2%98
- https://blog.naver.com/clickspace/120026142040
- https://bcho.tistory.com/48
- https://ko.wikipedia.org/wiki/%EA%B8%B0%EC%97%85_%EC%9D%91%EC%9A%A9_%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%A8_%ED%86%B5%ED%95%A9
- https://sheerheart.tistory.com/entry/EAI-%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80
- https://sarc.io/index.php/miscellaneous/671-soa-mci-eai-esb
- http://egloos.zum.com/longun3/v/4044432
- https://m.blog.naver.com/PostView.nhn?blogId=cache798&logNo=130024626366&proxyReferer=https%3A%2F%2Fwww.google.com%2F