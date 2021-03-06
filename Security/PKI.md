## SSL
- SSL(Secure Socket Layer) : SSL 프로토콜은 처음에 Netscape사에서 웹서버와 브라우저 사이의 보안을 위해 만들었다. SSL은 Certificate Authority(CA)라 불리는 서드 파티로부터 서버와 클라이언트의 인증을 하는데 사용된다.
- SSL과 TLS(Transport Layer Security Protocol)는 같은 의미이다. Netscape에 의해서 SSL이 발명되고, 이것이 점차 폭넓게 사용되다가 표준화 기구인 IETF의 관리로 변경되면서 TLS라는 이름으로 바뀌었다. TLS 1.0은 SSL 3.0을 계승한다.
- SSL의 핵심은 암호화이다. SSL은 보안과 성능상의 이유로 두가지 암호화 기법을 혼용해서 사용하고 있다.
<ul>
  <li>대칭키 기법 : 동일한 키로 암호화와 복호화를 같이 할 수 있는 방식의 암호화 기법을 의미한다. 대칭키 암호 방식으로 정보를 누군가한테 보낼 때 암호키도 함께 보내야 하는데 암호키를 암호화 되지 않은 평문으로 분실하거나 타인에게 노출되면 보안에 취약해진다. 키 전달 및 관리에 어려움이 있지만 암호화 연산 속도가 빠르기 때문에 효율적인 암호 시스템을 구축할 수 있다는 장점이 있다.</li>
  <li>공개키 기법 : 두 개의 키를 갖게 되는 방식으로 A키를 암호화를 하면 B키로 복호화 할 수 있고, B키로 암호화하면 A키로 복호화 할 수 있는 방식이다.두개의 키 중 하나를 비공개키(개인키,비밀키)로 하고, 나머지를 공개키로 지정한다. 비대칭키 암호라고도 한다. 공개키 암호는 키 전달 문제를 해결했지만, 암호화와 복호화를 위해 복잡한 수학연산을 수행하기 때문에 대칭키에 비해 속도가 느리다.</li>
</ul>

- 용량이 큰 정보는 대칭키로 암호화하고, 암호화에 사용된 대칭키는 공개키로 암호화하여 대상에게 전달하는 하이브리드 암호화 방법이 일반적으로 활용되고 있다.
- https://brownbears.tistory.com/332
- https://gaeko-security-hack.tistory.com/123
* IETF(Internet Enginerring Task Force, 국제 인터넷 표준화 기구) : 인터넷의 운영,관리,개발에 대해 협의하고 프로토콜과 구조적인 사안들을 분석하는 인터넷 표준화 작업기구이다.
- 장점
<ul>
  <li>정보유출 방지</li>
  <li>위조 사이트(피싱) 방지</li>
  <li>사이트 신뢰도 향상</li>
</ul>

## SSL 작동원리
<ol>
  <li>[웹브라우저] SSL로 암호화 된 페이지를 요청하게 된다.(https://)</li>
  <li>[웹서버] Public Key를 인증서와 함께 전송한다.</li>
  <li>[웹브라우저] 인증서가 자신이 신용있다고 판단한 CA(일반적으로 trusted root CA라고 불림)로부터 서명된 것인지 확인한다. 또한 날짜가 유효한지, 그리고 인증서가 접속하려는 사이트와 관련되어 있는지 확인한다.</li>
  <li>[웹브라우저] Publlic Key를 사용해서 랜덤 대칭 암호화키(Random symmetric encryption key)를 비롯한 URL, http 데이터들을 암호화해서 전송한다.</li>
  <li>[웹서버] Private Key를 이용해서 랜덤 대칭 암호화키와 URL, http 데이터를 복호화한다.</li>
  <li>[웹서버] 요청받은 URL에 대한 응답을 웹브라우저로부터 받은 랜덤 대칭 암호화키를 이용하여 암호화해서 브라우저로 전송한다.</li>
  <li>[웹브라우저] 대칭 키를 이용해서 http 데이터와 html문서를 복호화하고, 화면에 정보를 뿌려준다.</li>
</ol>

## SSL 인증서
- 인증서는 클라이언트와 서버간의 통신을 제3자가 보증해주는 전자화된 문서이다. 
- SSL과 SSL 인증서를 이용했을 때의 이점
  <ul>
    <li>통신 내용이 공격자에게 노출되는 것을 막을 수 있다.</li>
    <li>클라이언트가 접속하려는 서버가 신뢰할 수 있는 서버인지를 판단할 수 있다.</li>
    <li>통신 내용의 악의적인 변경을 방지할 수 있다.</li>
  </ul>
- SSL인증서는 클라이언트가 접속한 서버가 신뢰할 수 있는 서버임을 보장한다. SSL 통신에 사용할 공개키를 클라이언트에게 제공한다.
- CA : 인증서의 역할은 클라이언트가 접속한 서버가 클라이언트가 의도한 서버가 맞는지를 보장하는 역할. 이 역할을 하는 기업을들 CA혹은 Root Certificate라고 부른다. SSL을 통해서 암호화 된 통신을 제공하려는 서비스는 CA를 통해서 인증서를 구입해야 한다. 
- https://12bme.tistory.com/80

## PKI
- PKI(Public Key Infrastructure) : 공개키 알고리즘을 통한 암호화 및 전자 서명을 제공하기 위한 복합적인 보안 시스템 환경을 말한다.
- 전자서명 기술을 효과적으로 이용하기 위해서는 공개키 암호 방식이 필요하며, 공개키 암호 방식을 이용한 인증 방법을 구현하기 위한 기술적, 제도적 기반이 요구되는데 이를 공개키 기반구조(PKI)라고 한다.
- 전자상거래의 안전성과 신뢰성을 확보하기 위한 인증, 무결성, 부인봉쇄 등의 서비스는 전자서명 기술을 활용함으로써 해결 가능하다. 전자서명 기술을 효과적으로 이용하기 위해서는 공개키 암호 방식이 필요하며, 공개키 암호 방식을 인증 방법을 구현하기 위한 기술적, 제도적 기반이 요구되는데 이를 공개키 기반구조라고 한다.
- PKI의 구성요소
<ul>
  <li>인증기관(CA: Certification Authority) : 인증기관은 암호화, 암호 해독 및 인증을 위한 서명 키 제공 및 할당을 담당하며 공개 키와 특성 집합이 들어있는 인증서를 사용하여 키를 배포하며 독립된 신뢰기관으로써의 역할 수행</li>
  <li>등록기관(RA : Registration Authority) : CA의 위임을 받아 사용자의 등록 및 인증서 분배 등 CA의 역할 중 사용자와 접촉이 필요한 부분 주로 담당</li>
  <li>디렉토리(Directory) : 인증서 및 인증서 취소 목록 등 PKI 관련 정보들을 저장 및 검색하는 장소</li>
  <li>사용자(End Entitry) : PKI의 최종 사용자 및 시스템을 포함하며 인증서와 비공개키를 소지하고 있음</li>
</ul>
- http://wiki.wikisecurity.net/wiki:pki

## 암호화 알고리즘
- DES(Data Encryption Standard) : 평문을 64비트로 나눠 56비트의 키를 이용해 다시 64비트의 암호문을 만들어 내는 알고리즘이다.
- AES(Advanced Encryption Standard Algoritm) : DES를 대체한 암호 알고리즘이며 암호화와 복호화 과정을 동일한 키를 사용하는 대칭키 알고리즘이다. DES에 비해서 키 사이즈가 자유롭다. 즉, 가변 길이의 블록과 가변 길이의 키 사용이 가능하다. 속도와 코드 효율성 면에서 효율적이다. DES와의 차이점은 페이스텔 구조가 아닌 SPN 구조를 이용한다.
- https://www.crocus.co.kr/1230
- RSA(Rivest Sharmir Adleman) : 공개키 암호시스템의 하나로, 암호화뿐만 아니라 전자서명이 가능한 최초의 알고리즘으로 알려져 있다. 

## 전자서명
- 전자서명이라 함은, 서명자를 확인하고 서명자가 당해 전자문서에 서명했다는 사실을 나타내는 데 이용하려고, 특정 전자문서에 첨부되거나 논리적으로 결합된 전자적 형태의 정보를 말한다.
- 전자서명에 제공하는 보안서비스
<ol>
  <li>인증 : 내가 송신하고자 하는 메시지(문서)의 근원이 나 자신 이라는 것</li>
  <li>무결성 : 수신측에서는 내가 보낸 메시지가 중간에 위/변조 되지 않았음을 검증</li>
  <li>부인봉쇄 : 신뢰받는 제3자를 이용하면 나중에 상대방이 전자서명의 행위자체를 부인하는 것을 방지할 수가 있게 된다.</li>
</ol>

- 전자문서에 첨부되거나 논리적으로 결합된 전자적 형태의 정보를 만들기 위해서 기술적으로는 서명 알고리즘(Signing Algoritm)이 이용되고, 서명자를 확인하고 서명자가 당해 전자문서에 서명하였음을 확인하기 위해서 검증 알고리즘(Verifying Algoritm)이 적용된다.

- 나의 공개키가 해쉬된 값을 인증기관의 비밀키로 암호화 한 결과값을 디지털 서명이라고 한다.
<ul>
  <li>공개키에 대해서 (해쉬한 후) 인증기관의 비밀키로 암호화 함</li>
  <li>역으로 인증기관(CA)에서 발행한 공개키로 이 디지털 서명값을 복호화 하면 인증서에 대한 해쉬값을 얻을 수 있음 </li>
  <li>인증서에 등록되어 있는 해쉬값과 인증기관에서 발행한 공개키로 서명값을 복호화해서 나온 해쉬값이 서로 동일하면 인증서의 내용과 공개키가 위변조 되지 않았음을 보증할 수 있음</li>
</ul>

## 인증서
- 인증서 원리
<ol>
  <li>인터넷 사이트는 자신의 정보와 공개키를 인증 기관에 제출</li>
  <li>인증 기관은 검증을 거친 후 사이트 정보와 공개키를 인증기관의 개인키로 암호화하여 사이트 인증서를 제작</li>
  <li>사이트로 인증서 발급</li>
  <li>인증 기관은 웹 브라우저에게 자신의 공개키를 제공. 브라우저에 내장됨</li>
  <li>사용자가 웹 브라우저로 사이트에 접속하면 사이트는 자신의 인증서를 웹 브라우저에게 보냄</li>
  <li>웹 브라우저는 인증 기관의 공개키로 서버 인증서를 해독하여 검증</li>
  <li>이렇게 얻은 사이트 공개키로 대칭키를 암호화해서 보냄</li>
  <li>사이트는 자신의 개인키로 암호문을 해독해서 대칭키를 얻는다. </li>
  <li>대칭키로 암호문을 주고 받을 수 있음</li>
</ol>

- https://soul0.tistory.com/372

- 인증서의 정보
  <ul>
    <li>인증서 소유자의 e-mail 주소</li>
    <li>소유자의 이름</li>
    <li>인증서의 용도</li>
    <li>인증서 유효기간</li>
    <li>발행 장소</li>
    <li>Distingushed Name(DN) : Common Name(CN), 인증서 정보에 대해 서명한 사람의 디지털 ID</li>
    <li>Public Key</li>
    <li>해쉬(Hash)</li>
  </ul>

- https://wiki.kldp.org/HOWTO/html/SSL-Certificates-HOWTO/x70.html
