## Docker란
- 도커의 역사 : 도커는 2013년 3월 산타클라라에서 열린 Pycon Conference에서 dotCloud의 창업자인 Solomon Hykes가 The future of Linux Containers라는 세션을 발표하면서 처음 세상에 알려졌다. 이 발표 이후 도커가 인기를 얻으면서 2013년 10월 회사이름을 도커(Docker Inc.)로 바꾸고 2014년 6월 도커 1.0을 발표한다.
- 도커는 리눅스의 응용 프로그램들을 소프트웨어 컨테이너 안에 배치시키는 일을 자동화하는 오픈 소스 프로젝트이다.
- 리눅스 커널에서 제공하는 컨테이너 기술(LXC)를 이용. 하나의 어플리케이션을 격리된 공간(컨테이너)에서 독립적으로 실행할 수 있도록 해준다. 격리된 공간(컨테이너)들을 생성하고 관리해주는 것이 Docker Engine.
- 리눅스 커널이 제공하는 기능들 위에 빌드되기 때문에 도커 컨테이너는 가상 머신과는 달리 별도의 운영체제를 요구하거나 포함하지 않는다. 그 대신, 커널의 기능에 의존하며 리소스 격리(CPU, 메모리, 블록 입출력, 네트워크 등) 및 격리된 이름공간을 사용하여 운영 체제에 대한 운영 프로그램의 관점을 격리시킨다. 

&#42; LXC(LinuX Containers) : 단일 컨트롤 호스트 상에서 여러 개의 고립된 리눅스 시스템(컨테이너)들을 실행하기 위한 운영 시스템 레벨 가상화 방법이다. 

## 장점
<ul>
  <li>계층화된 파일시스템을 사용하기 때문에 가상화된 컨테이너의 변경사항을 모두 축적하고 관리해준다. 따라서, 특정 상태가 항상 보존되어 필요할 때 언제 어디서나 이를 실행가능하다.</li>
  <li>복잡한 리눅스 어플리케이션을 컨테이너로 묶어서 실행 가능</li>
  <li>개발,테스트,서비스 환경을 하나로 통일하여 효율적으로 관리 가능</li>
</ul>

## 특징
<ul>
  <li>도커는 Guest OS를 설치하지 않는다. 이미지에 서버운영을 위한 프로그램과 라이브러리만 격리해서 설치하여 이미지 용량이 크게 줄어듬. 호스트와 OS자원을 공유.</li>
  <li>도커는 하드웨어 가상화 계층이 없다. 메모리 접근,file system,네트워크 전송 속도가 가상머신에 비해 빠르다.호스트와 도커 컨테이너 사이의 성능 차이가 크지 않다.</li>
  <li>이미지 생성과 배포에 특화. 이미지 버전 관리를 제공. 중앙 저장소에 이미지를 올리고 받을 수 있다. Github와 비슷한 형태로 도커 이미지를 올리고 받을 수 있다. Github와 비슷한 형태로 도커 이미지를 공유하는 Docker hub가 있다.</li>
  <li>다양한 API를 제공하여 원하는 만큼 자동화 가능. 개발과 서버 운용에 유용.</li>
</ul>

## Container
- 컨테이너는 어플리케이션과 그에 필요한 것들이 포함되어 있지만 다른 컨테이너와 커널을 공유하고 Host OS에서 구분된 사용자 공간에서 프로세스가 실행된다. Docker 컨테이너는 특정 인프라에 묶여 있지 않으며 어떤 컴퓨터 어떤 인프라 어떤 클라우드에서도 구동된다.
- 기존의 가상화 방식은 주로 OS를 가상화하였다. VMware나 VirtualBox같은 가상머신은 호스트 OS위에 게스트 OS 전체를 가상화하여 사용하는 방식이다. 이 방식은 여러가지 OS를 가상화 할 수 있고 비교적 사용법이 간단하지만 무겁고 느려서 운영환경에선 사용할 수 없다.
- 이러한 상황을 개선하기 위해 CPU의 가상화 기술(HVM : Hardware Virtual Machine)을 이용한 KVM(Kernel_bassed Virtual Machine)과 반가상화(Paravirtualization) 방식의 XEN이 등장한다. 이 방식은 게스트 OS가 필요하긴 하지만 전체OS를 가상화 하는 방식이 아니였기 때문에 호스트형 가상화 방식에 비해 성능이 향상된다. 이러한 기술들은 OpenStack나 AWS, Rackspace같은 클라우드 서비스에서 가상 컴퓨팅 기술의 기반이 되었다.
- 하지만 추가적인 OS를 설치하여 가상화하는 방법은 어쨌든 성능문제가 있었고 이를 개선하기 위해 프로세스를 격리하는 방식이 등장한다. 리눅스에서는 이 방식을 리눅스 컨테이너라고 하고 단순히 프로세스를 격리시키기 때문에 가볍고 빠르게 동작한다.

## Image
- 도커에서 가장 중요한 개념은 컨테이너와 함께 이미지라는 개념. 이미지는 컨테이너 실행에 필요한 파일과 설정값들을 포함하고 있는 것으로 상태값을 가지지않고 변하지 않는다. 컨테이너는 이미지를 실행한 상태라고 볼 수 있고 추가되거나 변하지 않는 값은 컨테이너에 저장된다. 같은 이미지에서 여러 개의 컨테이너를 생성할 수 있고 컨테이너의 상태가 바뀌거나 삭제되더라도 이미지는 변하지 않고 그대로 남아있다.
- 이미지는 컨테이너를 실행하기 위한 모든 정보를 가지고 있기 때문에 더 이상 의존성 파일을 컴파일하고 여러가지를 설치할 필요가 없다.
- 이미지 생성 주기 : pull-> 도커 이미지를 받음. commit -> 파생된 이미지를 만듬. rmi -> 이미지 삭제
- Docker에서 실제로 실행되는 건 이미지를 기반으로 생성된 컨테이너

## Layer 저장방식
- 도커 이미지는 컨테이너를 실행하기 위한 모든 정보를 가지고 있기 때문에 보통 용량이 수백MB에 이른다. 처음은 부담이 되지 않지만 기존 이미지에 파일 하나를 추가했다고 다시 다운받는다면 매우 비효율적일 수 밖에 없다.
- 도커는 이런 문제를 해결하기 위해 레이어(Layer)라는 개념을 사용하고 유니온 파일 시스템을 이용하여 여러개의 레이어를 하나의 파일시스템으로 사용할 수 있게 해준다. 이미지는 여러개의 읽기 전용 레이어로 구성되고 파일이 추가되거나 수정되면 새로운 레이어가 생성된다. 따라서, 굉장히 효율적으로 이미지를 관리할 수 있다.
- 컨테이너를 생성할 때도 레이어 방식을 사용하는데 기존의 이미지 레이어 위에 읽기/쓰기 레이어를 추가한다. 이미지 레이어를 그대로 사용하면서 컨테이너가 실행중에 생성하는 파일이나 변경된 내용은 읽기/쓰기 레이어에 저장되므로 여러개의 컨테이너를 생성해도 최소한의 용량만 사용한다. 

## 이미지 경로
- 이미지는 url 방식으로 관리하여 태그를 붙일 수 있다. ubuntu 14.04 이미지는 docker.io/library/ubuntu:14.04 또는 docker.io/library/ubuntu:trusty
이고 docker.io/library는 생략가능하여 ubuntu:14.04 로 사용할 수 있다. 이 방식은 이해하기 쉽고 편리하게 사용할 수 있으며 태그 기능을 잘 이용하면 테스트나 롤백도 쉽게할 수 있다.

## Dockerfile
- 도커는 이미지를 만들기 위해 Dockerfile이라는 파일에 자체 DSL(Domain-specific language)언어를 이용하여 이미지 생성 과정을 적는다. 서버에 어떤 프로그램을 설치하려고 여러 의존성 패키지를 설치하고 설정파일을 만들었던 경험이 있다면 Dockfile로 관리하면 된다. 이 파일은 소스와 함께 버전 관리되고 원한다면 누구나 이미지 생성과정을 보고 수정할 수 있다.

## 도구
- Doker Compose : Compose는 멀티 컨테이너 도커 애플리케이션을 정의하고 실행하는 도구이다. YAML 파일을 사용하여 애플리케이션의 서비스를 구성하며 하나의 명령을 가지고 모든 컨테인너의 생성 및 시작 프로세스를 수행한다.
- Doker Swarm : 도커 컨테인너의 네이티브 클러스터링 기능을 제공하며 도커 엔진을 하나의 가상 도커 엔진으로 탈바꿈시킨다. 도커 1.12부터 Swarm 모드가 도커 엔진에 통합되어 있다.

## Kitematic
- Mac 또는 Windows PC에서 Docker를 사용하여 단순화하고 간소화하도록 만들어진 오픈소스 프로젝트.

## 도커 머신
- 도커 머신(Docker Machine)은 사용자의 로컬 컴퓨터, 클라우드 서비스가 제공하는 인스턴스, 원격 서버에 오커 호스트를 구성해준다. 도커 머신을 이용하면 자동으로 도커를 설치하고 도커 호스트를 만들 수 있고, 도커 클라이언트를 사용해서 설정한 서버의 도커 호스트에 도커 명령을 실행할 수 있다.

## 참고
- https://subicura.com/2017/01/19/docker-guide-for-beginners-1.html
- https://ko.wikipedia.org/wiki/%EB%8F%84%EC%BB%A4_(%EC%86%8C%ED%94%84%ED%8A%B8%EC%9B%A8%EC%96%B4)#cite_note-6
- https://seunguklee.github.io/2018/02/13/what-is-docker/
- https://avilos.codes/infra-management/virtualization-platform/docker/what-is-docker/
- https://judo0179.tistory.com/14
- https://kyulingcompany.wordpress.com/2017/06/22/union-file-system/
- https://futurecreator.github.io/2018/11/16/docker-container-basics/
- https://arisu1000.tistory.com/27798
- https://sori-nori.gitlab.io/youngkyung-done/docker-swarm/
