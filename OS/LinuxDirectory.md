# 리눅스 디렉토리

## 리눅스 디렉토리 구조
<ul>
  <li>/ : 루트. 최상위(루트) 디렉토리. 디렉토리들의 절대 경로를 표기할 때 이 디렉토리로부터 시작함.</li>
  <li>/bin : 바이너리. 이진파일(실행파일). 기본적인 명령어가 저장된 디렉토리. 리눅스에서 자주 사용하는 mv, cp, rm등과 같은 명령어들이 이 디렉토리에 존재함.</li>
  <li>/boot : 부트. 리눅스의 부트로더(Boot loader)가 있는 디렉토리임.</li>
  <li>/dev : 디브(디바이스). 시스템 디바이스(device)파일을 저장하고 있는 디렉토리. /dev/sda(하드디스크 장치파일), /dev/cdrom(CD-ROM)장치파일 등과 같은 장치 파일들이 여기에 위치함.</li>
  <li>/etc : 설정파일을 두는 디렉토리.</li>
  <li>/home : 홈. 사용자들의 홈디렉토리가 있는 곳. 사용자를 추가하면 사용자의 id와 동일한 디렉토리가 이곳에 자동으로 생성.</li>
  <li>/lib : 립(라이브러리). 커널이 필요로 하는 각종 라이브러리 파일, 커널 모듈파일 등이 존재하는 디렉토리.</li>
  <li>/media : 미디어. DVD, CD-ROM, USB 등의 탈부탁 가능한 장치들의 마운트 포인트로 사용하는 디렉토리.</li>
  <li>/mnt : 마운트. 탈부착 가능한 장치들에 대한 마운트 포인트로 사용하는 디렉토리.</li>
  <li>/opt : 옵트. 응용프로그램 패키지 설치 장소. 패키지 매니저가 자체적으로 설치/삭제를 수행함.</li>
  <li>/proc : 프록(프로세스). '가상파일시스템' 이라고 하는 곳으로 현재 메모리에 존재하는 작업들이 파일 형태로 존재하는 곳임.</li>
  <li>/root : 루트. 관리자계정 root 사용자의 홈디렉토리.</li>
  <li>/sbin : 시스템 바이너리. 시스템 이진파일(실행파일). ifconfig,ethtool,halt,e2fsck와 같은 시스템 명령어들을 저장하고 있는 디렉토리.</li>
  <li>/usr : 유저. 일반 사용자들이 사용하는 디렉토리.</li>
  <li>/var : 바. 시스템 운용중 생성되었다가 삭제되는 데이터를 임시 저장하기 위한 공간으로 사용되는 디렉토리.</li>
</ul>

## etc 폴더 구조
- https://openwiki.kr/tech/%EB%A6%AC%EB%88%85%EC%8A%A4_etc_%ED%8F%B4%EB%8D%94_%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0

## /etc/profile .profile
- .profile은 유닉스에서 로그인을 위한 환경설정을 저장한다. (리눅스는 /etc/progile은 있지만 .profile은 없는 경우도 있다)
- /etc/profile은 모든 계정에 공통적으로 적용되고, .profile은 해당하는 로그인 계정에서 사용하는 환경설정을 저장한다.(.profile은 각 계정의 홈 디렉토리 아래에 존재한다.)
- root로 로그인을 하면 먼저 /etc/profile을 읽어들여서 적용하고 그 다음 루트의 홈 디렉토리 아래에 있는 루트의 .profile을 읽어들인다.