## SOAP란
- SOAP(Simple Object Access Protocol). 일반적으로 널리 알려진 HTTP, HTTPS, SMTP 등을 통해 XML 기반의 메세지를 컴퓨터 네트워크 상에서 교환하는 프로토콜이다. 웹 서비스에서 기본적인 메세지를 전달하는 기반이 된다.
- SOAP에는 몇 가지 형태의 메세지 패턴이 있지만, 보통의 경우 원격 프로시저 호출(RPC) 패턴으로, 네트워크 노드(클라이언트)에서 다른 쪽 노드(서버)쪽으로 메세지를 요청 하고, 서버는 메세지를 즉시 응답하게 된다. SOAP는 XML-RPC와 WDDX에서 envelope/header/body로 이루어진 구조와 전송(transport)과 상호 중립성(interaction neutrality)의 개념을 가져왔다. 
- XML을 근간으로 헤더와 바디를 조합하는 디자인 패턴으로 설계되어 있다. Envelope는 SOAP의 Header와 Body를 둘러싼 것으로 SOAP 메세지를 위한 네임스페이스라고 할 수 있다. SOAP Header는 메세지를 처리하는데 필요한 인증정보나 세션, 트랜잭션 같은 추가 정보를 기술하며 압축알고리즘 같은 Body에서 인코딩하기 힘든 데이터를 전달할 때마다 이용한다. SOAP Body는 실제 메세지를 기술한다.
- 자바에서는 SAAJ라는 라이브러리가 있다. 개발자에게 SOAP 1.1사양과 SOAP에 파일 첨부하는 것을 만들 수 있게 한다. 개발자는 JAX-RPC를 사용하지 않고 직접 SOAP 애플리케이션을 생성할 수 있다.

## 만들어진 이유
- 과거에도 DCOM이나 CORBA같은 방법으로 RPC를 사용해 인터넷 상에서 의사소통을 할 수 있었지만, 호환성과 보안의 문제로 일반적인 방화벽은 이런 종류의 트래픽을 차단하기 때문에 문제가 있었다. 
- HTTP는 모든 인터넷 브라우저와 서버에 의해 지원되기 때문에 응용 프로그램간에 통신이 더 용이하다. SOAP는 HTTP의 이 부분을 활용하기 위해 만들어졌다.

## 전달과정
- Client -> 중계자 -> 중계자 -> Default Actor
- 먼저 Client에서 특정한 작업을 요청하게 되면 중계자가 받게된다. 그리고 자신이 처리할 내용이 있는지 확인 후 다음 중계자에게 전달한다. 이렇게 중계자를 통해 메세지의 일부를 변경하여 다음 중계자에게 포워딩하다가 액터를 만나게 되면 해당 작업을 처리한다. 이 액터를 Default Actor라고 하며 SOAP message의 최종 수신자라고 말할 수 있다. 

## 장단점
- 장점
   <ul>
    <li>SOAP을 사용한 HTTP는 다른 RPC에 비해 프록시와 방화벽에 구애받지 않고 쉽게 통신 가능하다.</li>
    <li>SOAP는 융통성있게도 각각 다른 트랜스포트 프로토콜들의 사용을 허용하고 있다. 표준 스택에서는 HTTP를 사용하지만, 
       다른 프로토콜도 사용 가능하다. 하지만 유일하게 표준화된 프로토콜이 HTTP이기 때문에 거의 모든 구현이 HTTP를 지원한다.</li>
    <li>HTTP와 XML을 사용하기 때문에 개발도구나 플랫폼에 구애받지 않고 SOAP 서버 혹은 클라이언트를 개발할 수 있다. 이처럼 SOAP 서버 혹은 클라이언트를 보다 쉽게 개발할 수 있도록 해주는 COM 컴포넌트, 유틸리티 등으로 구성된 SOAP 툴킷(toolkit)도 제공되고 있다. HTTP와 XML이 갖는 장점을 모두 포함하면서 컴포넌트의 상호운용성을 높일 수도 있다.</li>
    <li>SOAP는 프로그래밍 언어에 독립적이다.</li>
    <li>SOAP는 확장가능하다.</li>
    <li>SOAP는 전송 매체로서 HTTP를 사용하기 때문에 인터넷에서 널리 사용할 수 있다. SOAP는 인터넷에서 원격 객체를 액세스하기 위해 고안된 프로토콜이다.</li>
    <li>SOAP는 컴포넌트를 활성화하는 방법이나 호출하는 방법에 대해 전혀 관여하지 않으며 이에 대한 상세한 사항은 HTTP Request를 수신하는 수신자에게 위임하고 있다. 따라서 객체지향기술이나 컴포넌트 기술을 사용하지 않는 애플리케이션일지라도 SOAP를 통해 객체서비스를 제공하거나 제공받을 수 있다.         </li></ul>

- 단점
  <ul>
  <li>XML 포맷은 태그 형태로 보내기 때문에 CORBA같은 미들웨어 기술과 비교해서 상대적으로 느리다. 전송할 메시지가 적을때에는 문제가 되지 않을 수 있다. 성능을 향상시키기 위해서 바이너리 객체를 포함시킨 특별한 경우의 XML(Binary XML)로 MTOM(Message Transmission Optimization Mechanism; 메시지 전송 최적화 메커니즘)이 나왔다. 일반적인 XML의 성능을 향상시키기 위해, VTD-XML과 같은 emerging non-extractive XML 처리 모델이 있다.</li></ul>

## 참고
- https://ko.wikipedia.org/wiki/SOAP
- https://girlsy7.tistory.com/137
- https://j2enty.tistory.com/entry/SOAP-Soap-%EB%9E%80
