## EJB
- Enterprise JavaBeans. 기업환경의 시스템을 구현하기 위한 서버측 컴포넌트 모델. 애플리케이션의 업무 로직을 가지고 있는 서버 애플리케이션. JSP는 화면 로직. EJB는 업무 로직. 즉, 효율적으로 서버를 관리하고 프로그램 관련 문제를 처리해줌으로써 업무 효율성을 증대시켜주는 프로그램.
- EJB 기본구성 : Enterprise Bean, Container, EJB Server, Client Application
- 종류
<ol>
  <li> 세션빈 -> DB 연동이 필요없다.</li>
  <li> Entity Bean -> DB의 데이터 관리객체(Insert, Update, Delete, Select). DB관련 쿼리는 자동이며 개발자는 고급 업무 처리에 집중한다. DB수정시 코드 수정없이 다시 배포한다. </li>
  <li> Message-dirven Bean : JMS로 빈을 날려준다.</li>
</ol>
- 장점
<ol>
  <li> 정형화된 비즈니스 계층을 제공. 비즈니스 계층을 논리적,물리적 분리가 가능하도록 지원함. </li>
  <li> 선언적인 트랜잭션 관리와 같이 Non EJB 아키텍쳐에는 지원하기 힘들었던 기능을 EJB컨테이너가 제공함. </li>
  <li> EJB는 다양한 클라이언트에 대한 지원이 가능. EJB는 웹 UI 계층뿐만 아니라 Swing과 같은 GUI 클라이언트도 지원하는 것이 가능 </li>
  <li> 분산 기능을 지원 가능 </li>
  <li> 비즈니스 객체를 여러 서버에 분산시키는 것이 가능 </li>
</ol>
- 단점
<ol>
  <li> 분산환경을 지원하기 위해 객체를 직렬화 하는 과정 때문에 실행속도 저하가 발생함. </li>
  <li> 개발 사이클의 소스 수정, 빌드, 배포, 테스트와 같이 복잡한 과정을 거치기 때문에 개발 생산성이 저하되는 결과를 가져옴 </li>
  <li> EJB는 EJB컨테이너가 종속적이기 때문에 개발한 후 EJB컨테이너에 배포한 다음 테스트를 진행하여야 함. 테스트를 어렵게 만들며, 테스트의 어려움으로 제품의 질이 저하되는 결과 초래. </li>
  <li> EJB의 실행 속도 문제를 해결하기 위한 방법으로 EJB를 위한 변형된 패턴들이 등장하면서 객체지향적으로 개발하는데 제약사항. </li>
  <li> EJB 자체 스펙이 가지고 있는 실행속도가 떨어진다는 문제로 인해 EJB 컨테이너를 만드는 대형 벤더들 나름대로 자신들만의 기능들을 추가하면서 EJB 컨테이너 사이의 이식성이 떨어짐.</li>
</ol>

## WS(Web Server)
- Web Server의 개념 : 소프트웨어와 하드웨어로 구분된다. 하드웨어는 Web 서버가 설치되어 있는 컴퓨터. 소프트웨어는 웹 브라우저 클라이언트로부터 HTTP 요청을 받아 정적인 컨텐츠(.html .jpeg .css 등)를 제공하는 컴퓨터 프로그램.
- Web Server의 기능 : HTTP 프로토콜을 기반으로 하여 클라이언트(웹 브라우저 또는 웹 크롤러)의 요청을 서비스하는 기능을 담당한다. 요청에 따라 두 가지 기능 중 적절하게 선택하여 수행한다.
<ol>
  <li>기능 1 : 정적인 컨텐츠 제공. WAS를 거치지 않고 바로 자원을 제공한다.</li>
  <li>기능 2 : 동적인 컨텐츠 제공을 위한 요청 전달. 클라이언트의 요청(Request)을 WAS에 보내고, WAS가 처리한 결과를 클라이언트에게 전달(응답,Response)한다. 클라이언트는 일반적으로 웹 브라우저를 의미한다.</li>
</ol>

- nginx : 트래픽이 많은 웹사이트의 확장성을 위해 설계한 비동기 이벤트 기반구조의 웹서버 소프트웨어. 더 적은 자원으로 빠르게 서비스를 하는 SW로 알려져 있다. 이 프로그램은 가벼움과 높은 성능을 목표로 만들어 졌으며, 러시아의 프로그래머, 이고르 시쇼브가 Apache의 C10K Problem(하나의 웹서버에 10,000개의 클라이언트의 접속을 동시에 다룰 수 있는 기술적인 문제)를 해결하기 위해 만든 Event-driven 구조의 HTTP, Reverser Proxy, IMAP/POP PROXY server를 제공하는 오픈소스 서버 프로그램이다.
- WS로 기존에 apache가 존재했었다. apache는 다양한 기능과 써드파티 확장기능과 함께 어떠한 웹 어플리케이션 개발에도 적용할 수 있는 웹 서버가 되었지만,
클라이언트 접속당 CPU와 메모리 사용량이 증가함으로써 확장성이 떨어진다는 단점이 있었다. 그래서 대량의 클라이언트를 관리하기 위한 웹서버가 필요시되었고, 그래서 나온 것이 nginx였다. nginx는 event 기반으로 동작하기 때문에 apache와 같이 각각의 웹페이지 요청을 처리하기 위해 새로운 process or thread를 생성하지 않는다고 한다. 그렇기 때문에 단일 서버에서도 수만 개의 동시 연결을 처리할 수 있다고 한다. 현재 nginx는 분산 메모리 객체 캐시 시스템이 추가되었고, 로드 밸런싱을 위한 reverse proxy, 캐싱 같은 것도 추가되었다고 한다.

- apache : 세계에서 가장 많이 쓰는 웹 서버중 하나이며, 아파치 소프트웨어 제단에서 관리하는 HTTP 웹 서버이다. Apache는 Apache재단에서 만든 HTTP서버로 워낙 다양한 추가기능에, 구축이 쉽다는 이유 때문에 많이 쓰고 있다. 하지만 Apache 자체만으로 엄청 무겁고, Squid와 함께 Slowloris 취약점이 발견되었기에, 프로그래밍이 능숙한 사람이나 대형사이트 운영자는 Nginx, IIS를 주로 쓰고있지만 대부분의 중소기업에서는 무료이기 때문에 많이 쓴다.

- WebtoB : 티맥스소프트사의 웹 서버 제품이다. 대규모 트랜잭션 처리에 적합하도록 설계되어 처리속도 지연, 서버 장애 등의 웹 시스템상의 문제점을 해결하는 아키텍처로 설계되었다.

## WAS(Web Application Server)

- WAS의 개념 : DB 조회나 다양한 로직 처리를 요구하는 동적인 컨텐츠를 제공하기 위해 만들어진 Application Servere. HTTP를 통해 컴퓨터나 장치에 애플리케이션을 수행해주는 미들웨어(소프트웨어 엔진)이다. "웹 컨테이너(Web Container)" 혹은 "서블릿 컨테이너(Servlet Container)"라고도 불린다. Container란 JSP,Servlet을 실행시킬 수 있는 소프트웨어를 말한다. 즉, WAS는 JSP,Servlet 구동 환경을 제공한다.
- WAS의 역할 : WAS = Web Server + Web Container. Web Server 기능들을 구조적으로 분리하여 처리하고자하는 목적으로 제시되었다. 분산 트랜잭션, 보안, 메시징, 쓰레드 처리 등의 기능을 처리하는 분산 환경에서 사용된다. 주로 DB 서버와 같이 수행된다. 현재는 WAS가 가지고 있는 Web Server도 정적인 컨텐츠를 처리하는데 있어서 성능상 큰 차이가 없다.
- WAS의 주요 기능
<ul>
  <li>프로그램 실행 환경과 DB 접속 기능 제공</li>
  <li>여러 개의 트랜잭션(논리적인 작업 단위) 관리 기능</li>
  <li>업무를 처리하는 비즈니스 로직 수행</li>
</ul>

## Web Server와 WAS를 구분하는 이유
- Web Server가 필요한 이유? 클라이언트(웹 브라우저)에 이미지 파일(정적 컨텐츠)을 보내는 과정을 생각해보자.
<ul>
  <li>이미지 파일과 같은 정적인 파일들은 웹 문서(HTML 문서)가 클라이언트로 보내질 때 함께 가는 것이 아니다.</li>
  <li>클라이언트는 HTML 문서를 먼저 받고 그에 맞게 필요한 이미지 파일들을 다시 서버로 요청하면 그때서야 이미지 파일을 받아온다.</li>
  <li>Web Server를 통해 정적인 파일들을 Application Server까지 가지 않고 앞단에서 빠르게 보내줄 수 있다.</li>
</ul>
-> 따라서 Web Server에서는 정적 컨텐츠만 처리하도록 기능을 분배하여 서버의 부담을 줄일 수 있다.

- WAS가 필요한 이유? 웹 페이지는 정적 컨텐츠와 동적 컨텐츠가 모두 존재한다.
<ul>
  <li>사용자의 요청에 맞게 적절한 동적 컨텐츠를 만들어서 제공해야 한다.</li>
  <li>이때, Web Server만을 이용한다면 사용자가 원하는 요청에 대한 결과값을 모두 미리 만들어 놓고 서비스를 해야 한다.</li>
  <li>하지만 이렇게 수행하기에는 자원이 절대적으로 부족하다.</li>
</ul>
-> 따라서 WAS를 통해 요청에 맞는 데이터를 DB에서 가져와서 비즈니스 로직에 맞게 그때 그때 결과를 만들어서 제공함으로써 자원을 효율적으로 사용할 수 있다.

## WAS가 Web Server의 기능도 모두 수행하지 않는 이유?
<ol>
  <li>기능을 분리하여 서버 부하 방지 : WAS는 DB 조회나 다양한 로직을 처리하느라 바쁘기 때문에 단순한 정적 컨텐츠는 Web Server에서 빠르게 클라이언트에 제공하는 것이 좋다. WAS는 기본적으로 동적 컨텐츠를 제공하기 위해 존재하는 서버이다. 만약 정적 컨텐츠 요청까지 WAS가 처리한다면 정적 데이터 처리로 인해 부하가 커지게 되고, 동적 컨텐츠의 처리가 지연됨에 따라 수행 속도가 느려진다. 즉, 이로 인해 페이지 노출 시간이 늘어나게 될 것이다.</li>
  <li>물리적으로 분리하여 보안 강화 : SSL에 대한 암복호화 처리에 Web Server를 사용.</li>
  <li>여러 대의 WAS를 연결 가능 : Load Balancing을 위해서 Web Server을 사용. fail over(장애 극복),fail back처리에 유리. 특히 대용량 웹 어플리케이션의 경우(여러 개의 서버 사용) Web Server와 WAS를 분리하여 무중단 운영을 위한 장애 극복에 쉽게 대응할 수 있다.</li>
  <li>여러 웹 어플리케이션 서비스 가능 : 예를 들어, 하나의 서버에서 PHP Application과 JAVA Applicaiton을 함께 사용하는 경우.</li>
  <li>접근 허용 IP 관리, 2대 이상의 서버에서의 세션 관리 등도 Web Serveer에서 처리하면 효율적이다.</li>
</ol>
- 즉, 자원 이용의 효율성 및 장애 극복,배포 및 유지보수의 편의성을 위해 Web Server와 WAS를 분리한다.
- Web Server를 WAS 앞에 두고 필요한 WAS들을 Web Server에 플러그인 형태로 설정하면 더욱 효율적인 분산 처리가 가능하다.

## MiddleWare
- Client - MiddleWare Server - DB Server(DBMS)
- 동작 과정
<ol>
  <li>Client는 단순히 요청만 중앙에 있는 MiddleWare Server에게 보낸다.</li>
  <li>MiddleWare Server에서 대부분의 로직이 수행된다.</li>
  <li>이때, 데이터를 조작할 일이 있으면 DBMS에 부탁한다.</li>
  <li>로직의 결과를 Client에게 전송한다.</li>
  <li>Client는 그 결과를 화면에 보여준다.</li>
</ol>
- 즉, 비즈니스 로직을 Client와 DBMS 사이의 MiddleWare Server에서 동작하도록 함으로써 Client는 입력과 출려만 담당하게 된다.
- https://gmlwjd9405.github.io/2018/10/27/webserver-vs-was.html
