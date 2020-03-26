<h3>2 티어 아키텍처 구조(2 Tier Architecture Structure)</h3>

- 클라이언트(UI, Business Logic) + DB
- 과거 많은 어플리케이션은 2 Tier 형태의 아키텍쳐를 가지고 있다. 2 Tier 아키텍쳐란 클라이언트와 DB가 물리적으로 분리되어있는 구조 안에서, 클라이언트에는 UI와 비즈니스 로직(Business Logic)이 함께 있는 구조이다.
- 장점
  <ol>
    <li>쉽게 빠르게 개발할 수 있으며 시스템 구축이 어렵지 않다.</li>
    <li>애플리케이션의 구조가 단순하다.</li>
    <li>개발 비용이 비교적 저렴하다.</li>
  </ol>
  
- 단점 : 이 단점들을 개선하고자 3 Tier 혹은 N Tier 아키텍처로 설계를 한다.
   <ol>
     <li>클라이언트에서 DB에 직접 붙기 때문에 안정성에도 문제가 있다.</li>
     <li>UI와 비즈니스 로직을 클라이언트에서 모두 관리하기 때문에, 클라이언트에 부하가 걸리기 쉽다.</li>
     <li>재사용이 어렵다.</li>
     <li>비즈니스가 점점 더 복잡해지거나 비대해지면 관리하기가 어려워진다.</li>
   </ol>

<h3>3 티어 아키텍처 구조(3 Tier Architecture Structure)</h3>

- 클라이언트(UI) + 비즈니스(Business Logic) + DB
- 2 티어 아키텍처의 구조와 큰 차이점은 클라이언트 안에 존재하는 UI와 비즈니스 로직(Business Logic)이 분리된다는 점이다.
- 클라이언트를 프레젠테이션 티어, 비즈니스 계층은 애플리케이션 티어라고 부르기도 한다.
- 장점
  <ol>
    <li>클라이언트가 직접 DB에 붙는 것이 아닌 Business 계층을 통해 붙기 때문에 보안에 용이하다.</li>
    <li>재사용이 쉬우며, 확장에 용이하다.</li>
    <li>비즈니스 로직과 UI를 분리할 수 있다.</li>
  </ol>
  
<h3>MPA 어플리케이션</h3>
  
  - MPA(Multiple Page Application). 전통적인 웹 어플리케이션 방식이다.
  - 가장 큰 단점은 프론트엔드와 백엔드가 강하게 결합되어 있다는 점이다. 이러한 점은 2 티어 아키텍쳐의 단점과 같다.
  - 이러한 구조는 웹서버라고 불리우는 형태의 애플리케이션이다.
  - 처리 과정
    <ol>
      <li>"A"에 대한 페이지 정보를 서버에 요청한다.</li>
      <li>"A"에 대한 요청을 받은 서버는 해당하는 UI와 필요한 데이터(게시판이라고 하면 게시글 데이터를 의미한다)를 이용하여 HTML 데이터로 파싱한다.</li>
      <li>브라우저는 전달받은 HTML 데이터를 지정된 인코딩으로 변환하여 사용자에게 보여준다.</li>
    </ol>
    
 - 브라우저는 이러한 과정을 거치면서 페이지를 갱신하게 되며 사용자는 페이지가 이동될때마다 새로고침되는 것을 볼 수 있다. 이러한 새로고침은 로딩 시간이 늘어질 뿐만 아니라 사용자의 경험 역시 좋지 않을 수 밖에 없다.
 - 이러한 단점을 AJAX라는 기술이 어느정도 해결해주지만, 근본적으로 페이지 이동시 새로고침된다는 문제를 해결하기에는 역부족이었다.
 - 장점
  <ol>
    <li>애플리케이션에 시각적으로 어디로 가야할지 필요한 사용자에게 완벽한 접근방법이다. 몇몇의 네비게이션 메뉴에 있어서 전통적인 MPA는 필수적이다.</li>
    <li>SEO 최적화에 효율적이다. 하나의 키워드당 하나의 페이지에 최적화시킬 수 있기 때문에 다른 키워드에 랭크될 수 있는 이점을 가지고 있다.</li>
  </ol>
  
  - 단점
    <ol>
      <li>프론트엔드와 백엔드 개발이 밀접하게 연관되어 있다.</li>
      <li>개발이 꽤 복잡해졌다. 개발자는 클라이언트 사이드와 백엔드 사이드 모두 프레임워크를 사용해야 한다. 이 결과로 애플리케이션 개발에 많은 시간이 소요된다.</li>
    </ol>
 
 <h3>SPA 애플리케이션</h3>
 
- MPA 애플리케이션의 단점을 개선해줄 수 있는 것이 SPA 애플리케이션이다. SPA란 Single Page Application의 약자로서 다른 말로 CSR(Client Side Rendering)이라고 표현하기도 한다.
 - SPA 애플리케이션은 하나의 HTML 파일만 있으면 나머지는 Javascript를 이용해서 동적으로 화면을 구성할 수 있다. 서버는 어떠한 요청을 받던 무조건 동일한 HTML 파일을 내려준다.
- 사용자는 하나의 HTML파일에서 Javascript를 이용해 동적으로 구성되는 UI 화면 속에서 마치 페이지가 이동되는 것처럼 보여지는 느낌을 받는다.
- 이렇게 URL을 조작해 마치 이동되는 것처럼 보여지게 하는 것은 해쉬 방식 혹은 HTML5의 히스토리 API를 통해 가능하다.
- SPA의 가장 큰 장점으로는 변경된 부분만 효율적으로 변경한다는 점이다.
- 애플리케이션의 모든 페이지들이 Javascript 안에 포함되어져 있기 때문에 애플리케이션에서 사용하는 Javascript 파일은 점점 커지며 애플리케이션의 초기 렌더링 속도가 느리다. 또한, SEO에 굉장히 취약하다.

- 장점
  <ol>
    <li>SPA는 HTML, CSS, Javascript를 어플리케이션 라이프사이클에서 한번만 로드한다. 서버와 데이터만 주고받는다.</li>
    <li>개발이 간편하고 간소화되었다. 서버에 렌더링되는 페이지를 작성할 필요가 없다. 이것은 서버 사용없이 file://URI를 이용함으로 개발을 하는데 수월해졌다.</li>
    <li>SPA는 크롬으로 디버깅을 하기 쉽다. network operations를 통해서 모니터링이 가능하고 소스코드와 관련된 요소와 데이털르 검사할 수 있다.</li>
    <li>개발자가 백엔드 코드를 웹어플리케이션과 네이티브 모바일 어플리케이션에서 동일하게 사용할 수 있어 모바일 어플리케이션을 만들기 쉽다.</li>
    <li>SPA는 모든 로컬스토리지를 효율적으로 캐시할 수 있다. 어플리케이션은 서버에 한번만 요청하고 모든 데이터를 저장하고 사용한다. 그 데이터는 오프라인 상태로 사용할 수 있다.</li>
  </ol>

- 단점
  <ol>
    <li>SEO가 어렵다.</li>
    <li>무거운 클라이언트 프레임워크가 클라이언트 로드되어야 하기 때문에 다운로드 속도가 느리다.</li>
    <li>자바스크립트가 존재하고 활성화되어 있어야한다. 만약 일부 사용자의 브라우저에서 자바스크립트를 사용할 수 없게 설정되어 있다면 어플리케이션을 사용할 수 없다.</li>
    <li>전통적은 어플리케이션과 비교했을 때 보안에 취약하다. 다른 사용자가 클라이언트 사이트 스크립트를 통해 Cross-Site Scripting(XSS)으로 공격할 수 있다.</li>
    <li>자바스크립트의 메모리 부족은 어플리케이션 속도를 저하시킬 수 있다.</li>
  </ol>

<h3>참고 사이트</h3>

- https://blog.martinwork.co.kr/devops/2019/05/24/server-side-rendering01.html
- https://yngmanie.space/posts/spa-mpa