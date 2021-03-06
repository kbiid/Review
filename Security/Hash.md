## 단방향 해시 함수
- 단방향 해시 함수는 수학적인 연산을 통해 원본 메시지를 변환하여 암호화된 메시지인 다이제스트를 생성한다. 원본 메시지를 알면 암호화된 메시지를 구하기는 쉽지만 암호화된 메시지로는 원본 메시지를 구할 수 없어야 하며 이를 `단방향성`이라고 한다.
- 대부분의 해시 함수는 입력 값의 일부가 변경되었을 때 다이제스트가 완전히 달라지도록 설계되어 있다. 이 특징을 avalanche 효과라고 하며, 사용자의 원본 패스워드를 추론하기 어렵게 만드는 중요한 요소이다. 그러나 이것만으로는 충분히 안전하다고 할 수 없다.

## 단방향 해시 함수의 문제점
  <ul><li>인식 가능성(recognizability) : 동일한 메시지가 언제나 동일한 다이제스트를 갖는다면, 공격자가 전처리(pre-computing)된 다이제스트를 가능한 한 많이 확보한 다음 이를 탈취한 다이제스트와 비교해 원본 메시지를 찾아내거나 동일한 효과이 메시지를 찾을 수 있다. 이와 같은 다이제스트 목록을 레인보우 테이블(rainbow table)이라 하고, 이와 같은 공격 방식을 레인보우 공격(rainbow attack)이라 한다.게다가 다른 사용자의 패스워드가 같으면 다이제스트도 같으므로 한꺼번에 모두 정보가 탈취될 수 있다.</li>
    <li>속도(speed) : 해시 함수는 짧은 시간에 데이터를 검색하기 위해 설계된 것이다. 해시 함수의 빠른 처리 속도로 인해 공격자는 매우 빠른 속도로 임의의 문자열의 다이제스트와 해킹할 다이제스트를 비교할 수 있다. 이런 방식으로 패스워드를 추측하면 패스워드가 충분히 길거나 복잡하지 않은 경우에는 그리 긴 시간이 걸리지 않는다.</li></ul>
    
## 단방향 해시 함수 보완하기
  <ul><li>솔팅(salting) : 솔트(salt)는 단방향 해시 함수에서 다이제스트를 생성할 때 추가되는 바이트 단위의 임의의 문자열이다. 그리고 이 원본 메시지에 문자열을 추가하여 다이제스트를 생성하는 것을 솔팅이라 한다. 이 방법을 사용할 때에는 모든 패스워드가 고유의 솔트를 갖고 솔트의 길이는 32바이트 이상이어야 솔트와 다이제스트를 추측하기 어렵다.</li>
    <li>키 스트레칭(key stretching) : 입력한 패스워드의 다이제스트를 생성하고, 생성된 다이제스트를 입력 값으로 하여 다이제스트를 생성하고, 또 이를 반복하는 방법으로 다이제스트를 생성할 수도 있다. 이렇게 하면 입력한 패스워드를 동일한 횟수만큼 해시해야만 입력한 패스워드의 일치 여부를 확인할 수 있다. 이것이 기본적인 키 스트레칭 과정이다.</li></ul>
    
## Adative Key Derivation Functions
- 다이제스트를 생성할 때 솔팅과 키 스트레칭을 반복하며 솔트와 패스워드 외에도 입력 값을 추가하여 공격자가 쉽게 다이제스트를 유추할 수 없도록 하고 보안의 강도를 선택할 수 있다.
- 이 함수들은 GPU(Graphics Processing Unit)와 같은 장비를 이용한 병렬화를 어렵게 하는 기능을 제공한다. 이와 같은 기능은 프로그램이 언어에서 제공하는 라이브러리만으로는 구현하기 어렵다.
- 주요한 key derivation function은 다음과 같다.
  <ul><li>PBKDF2 : 가장 많이 사용되는 것으로써 Password-Based Key Derivation Function의 줄임말이다. 해시 함수의 컨테이너인 PBKDF2는 솔트를 적용한 후 해시 함수의 반복 횟수를 임의로 선택할 수 있다. 아주 가볍고 구현하기 쉬우며, SHA와 같이 검증된 해시 함수만을 사용한다.</li>
    <li>bcrypt : 패스워드 저장을 목적으로 설계되었다. 현재까지 사용되는 가장 강력한 해시 메커니즘 중 하나이다. OpenBSD에서 기본 암호 인증 메커니즘으로 사용되고 있다. bcypt에서 "work factor"인자는 하나의 해시 다이제스트를 생성하는 데 얼마만큼의 처리 과정을 수행할지 결정한다. "work factor"를 조정하는 것만으로 간단하게 시스템의 보안성을 높일 수 있다. 다만 PBKDF2나 scrypt와는 달리 bcrypt는 입력 값으로 72 bytes character를 사용해야 하는 제약이 있다.</li> 
    <li>scrypt : PBKDF2와 유사하며 Colin Percival이 2012년 9월 17일 설계했다. scrypt는 다이제스트를 생성할 때 메모리 오버헤드를 갖도록 설계되어, 억지 기법 공격(brute-force attack)을 시도할 때 병렬화 처리가 매우 어렵다. scrypt는 보안에 아주 민감한 사용자들을 위한 백업 솔루션을 제공하는 Tarsnap에서도 사용하고 있다. 여러 프로그래밍 언어의 라이브러리로 제공받을 수 있다.</li></ul>

## 참고
- https://d2.naver.com/helloworld/318732

## MD5
- Message-Digest algoritm 5. 128비트 암호화 해시 함수이다. 주로 프로그램이나 파일이 원본 그대로인지를 확인하는 무결성 검사 등에 사용된다. 1991년에 로널드 라이베스트가 예전에 쓰이던 MD4를 대체하기 위해 고안했다. 
