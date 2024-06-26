## 03-1 LAN을 넘어서는 네트워크 계층
### 데이터 링크 계층의 한계
- 물리 계층과 데이터 링크 계층만으로는 다른 네트워크까지의 도달 경로를 파악하기 어렵다.
	- 패킷이 이동할 최적의 경로를 결정하는 것을 라우팅이라고 한다.
	- 라우팅을 수행하는 대표적인 장비로는 라우터가 있다.
- MAC 주소만으로는 모든 네트워크에 속한 호스트의 위치를 특정하기 어렵다.
	- 수신지의 역할을 하는 정보는 네트워크 계층의 IP주소
	- MAC주소를 물리주소, IP주소를 논리 주소라고도 부른다.
### 인터넷 프로토콜
- 네트워크 게층의 가장 핵심적인 프로토콜 하나는 인터넷 프로토콜이다.
	- IP버전 4(IPv4)와 IP버전 6(IPv6), 두 가지 버전이 있다.
- IP 주소는 4바이트(32비트)로 주소를 표현할 수 있고, 숫자당 8비트로 표현되기에 0~255 범위 안에 있는 네 개의 10진수로 표기된다.
	- 점으로 구분된 8비트를 옥텟이라고 한다.
- IP의 대표적인 기능에는 크게 IP 주소 지정과 IP 단편화가 있다.
	- IP 주소 지정은 IP 주소를 바탕으로 송수신 대상을 지정하는 것을 의미
	- IP 단편화는 전송하고자 하는 패킷의 크기가 MTU라는 최대 전송 단위보다 클 경우, 이를 MTU 크기 이하의 복수의 패킷으로 나누는 것을 의미한다.

**IPv4**
- IPv4 패킷은 프레임의 페이로드로 데이터 필드에 명시된다.
- 식별자, 플래그, 단편화 오프셋 필드는 IP 단편화 기능에 관여하고, 송신지 IP 주소, 수신지 IP 주소는 IP 주소 지정 기능에 관여한다.
```
- 식별자 : 패킷에 할당된 번호
- 플래그 : 총 세 개의 비트로 구성된 필드(DF, MF)
- 단편화 오프셋 : 패킷이 단편화되기 전에 패킷의 초기 데이터에서 몇 번째로 떨어진 패킷인지 나타냄
- TTL : 패킷의 수명(홉 단위)
- 프로토콜 : 상위 계층의 프로토콜이 무엇인지를 나타내는 필드
- 송신지 IP 주소 수신지 IP 주소
```

**IPv6**
- 43억 개라는 IPv4의주소의 총량의 고갈문제 떄문에 등장한 버전
- 16바이트로 주소를 표현할 수 있고, 콜론으로 구분된 8개 그룹의 16진수로 표기
- 기본 헤더는 IPv4에 비해 간소화
```
- 다음 헤더 : 상위 계층의 프로토콜을 가리키거나 확장 헤더를 가르킨다. 추가적인 헤더 정보가 필요할 경우에 기본헤더와 더불어 확장 헤더라는 추가 헤더를 가질 수 있다.
- 홉 제한 : 패킷의 수명을 나타내는 필드
- 송신지 IP 주소와 수신지 IP 주소
```

### ARP
- IP 주소를 통해 MAC 주소를 알아내는 프로토콜
- ARP의 동작과정
	- ARP 요청 : 같은 내트워크 내의 모든 호스트에게 브로드캐스트 메시지를 보낸다.
	- ARP 응답
	- ARP 테이블 갱신

## 03-2 IP 주소
- 하나의 IP 주소는 크게 네트워크 주소와 호스트 주소로 이루어진다.
### 네트워크 주소와 호스트 주소
- 네트워크 주소는 네트워크 ID, 네트워크 식별자 등으로 부르기도 하며, 호스트 주소는 호스트 ID, 호스트 식별자 등으로 부른다.
- IP 주소에서 네트워크 주소와 호스트 주소를 구분하는 범위는 유동적이다.
### 클래스풀 주소 체계
- 클래스는 네트워크크기에 따라 IP 주소를 분류하는 기준
- 클래스를 기반으로 IP 주소를 관리하는 주소 쳬계를 클래스풀 주소 체계라고 한다.
```
- A 클래스 : 8/24
- B 클래스 : 16/16
- C 클래스 : 24/8
```
### 클래스 리스 주소 체계
- 이름처럼 클래스 개념 없이 클래스에 구애받지 않고 네트워크의 영역을 나누어서 호스트에게 IP 주소 공간을 할당하는 방식
- 클래스리스 주소 체계에서는 네트워크와 호스트를 구분 짓는 수단으로 서브넷 마스크를 이요한다.
- 서브넷 마스크는 IP 주소상에서 네트워크 주소는 1, 호스트 주소는 0으로 표기한 비트열열을 의미
- 서브넷 마스크를 이용해 슼ㄹ래스를 원하는 크기로 더 잘게 쪼개어 사용하는 것을 서브네팅이라고 한다.
- 서브넷 마스크를 이용해 네트워크 주소와 호스트 주소를 구분 짓는 방법은 IP 주소와 서브넷 마스크를 비트 AND 연산을 하면 된다.
- 서브넷 마스크를 표기하는 방법
	- 10진수로 표기하는 방법
	- IP 주소/서브넷 마스크상의 1의 개수 형식으로 표기하는 방법 = CIDR 표기법
### 공인 IP 주소와 사설 IP 주소
**공인 IP 주소**
- 전 세계에서 고유한 IP 주소
- ISP나 공인 IP 주소할당 기관을 통해 할당 받을 수 있다.

**사설 IP 주소와 NAT**
- 사설 네트워크에서 사용하기 위한 IP 주소
- 외부 네트워크에 공개되지 않은 네트워크를 의미
- 사설 IP 주소로 사용하도록 특별히 예약된 IP 주소 공간
	- 10.0.0.0/8
	- 172.16.0.0/12
	- 192.168.0.0/16
- 사설 IP 주소 할당 주체는 일반적으로 라우터
- NAT(Network Address Translation)는 IP 주소를 변환하는 기술
### 정적 IP 주소와 동적 IP 주소
**정적 할당**
- 호스트에 직접 수작업으로 IP 주소를 부여하는 방식
- 정적 IP 주소

**동적 할당과 DHCP**
- 정적 할당과는 달리 IP 주소를 직접 일일이 입력하지 않아도 호스트에 IP 주소가 동적으로 할당되는 방식
- 동적 IP 주소
- IP 동적 할당에 사용되는 대표적인 프로토콜이 바로 DHCP(Dynamic Host Configuration Protocol)
	- IP 주소를 제공하는 DHCP 서버가 필요
	- DHCP 서버의 역할은 일반적으로 라우터(공유기)가 수행
- 클라이언트와 DHCP 서버 간에 주고받는 메시지 종류
	- DHCP Discover
	- DHCP Offer
	- DHCP Request
	- DHCP Acknowledgment

## 03-3 라우팅
- 라우팅은 패킷이 이동할 최적의 경로를 설정한 뒤 해당 경로로 패킷을 이동시키는 것
### 라우터
- 오늘날 라우터와 L3 스위치는 기능상 상당 부분 유사하므로 엄밀히 구분하지 않는 경우가 많다.
- 라우터와 라우터 간에 이동하는 하나의 과정을 홉이라고 한다.
- 패킷은 여러 홉을 거쳐 라우팅될 수 있다
### 라우팅 테이블
- 특정 수신지까지 도달하기 위한 정보를 명시한 일종의 표와 같은 정보
- 라우팅 테이블에 포함된 정보는 라우팅 방식에 따라, 호스트의 환경에 따라 달라질 수 있다.
- 공통적인 정보이자 핵심적인 정보
	- 수신지 IP 주소와 서브넷 마스크 : 최종적으로 패킷을 전달할 대상을 의미
	- 다음 홉 : 최송 수신지까지 가기 위해 다음으로 거쳐야 할 호스트의 IP 주소나 인터페이스를 의미. 게이트웨이라고 명시되기도 한다.
	- 네트워크 인터페이스 : 패킷을 내보낼 통로
	- 메트릭 : 해당 경로로 이동하는데에 드는 비용
- 라우팅 테이블에 없는 경로로 패킷을 전송해야 할 때는 디폴트 라우트로 패킷을 내보낸다.
### 정적 라우팅과 동적 라우팅
**정적 라우팅**
- 사용자가 수동으로 직접 채워 넣은 라우팅 테이블의 항목을 토대로 라우팅되는 방식

**동적 라우팅**
- 자동으로 라우팅 테이블 항목을 만들고, 이를 이용하여 라우팅하는 방식
- 네트워크 경로상에 문제가 발생했을 때 우회할 수 있게 경로가 자동으로 갱신
- 자동으로 라우팅 테이블 항목을 만드는 과정
	- 최적의 경로를 찾아 라우팅 테이블에 추가하려는 노력
	- 라우터끼리 서로 자신의 정보 교환
	- 이때 사용되는 프로토콜이 바로 라우팅 프로토콜
### 라우팅 프로토콜
- 라우터끼리 자신들의 정보를 교환하며 패킷이 이동할 최적의 경로를 찾기 위한 프로토콜
- AS 내부에서 수행되느냐 외부에서 수행되느냐에 따라 IGP, EGP로 나눌 수 있다.
**IGP: RIP와 OSPF**
- 최적의 경로를 선정하는 과정에서 거리 벡터(RIP)가 사용되느냐, 링크 상태(OSPF)가 사용되느냐로 구분
- RIP는 거리 벡터 기반의 라우팅 프로토콜
	- 거리 벡터 라우팅 프로토콜이란 거리를 기반으로 최적의 경로를 찾는 라우팅 프로토콜
	- 거리는 홉의 수를 의미
	- 특정 수신지에 도달하기까지의 홉 수를 알 수 있다.
	- 인접한 라우터끼리 경로 정보를 주기적으로 교환하며 라우팅 테이블을 갱신
- OSPF는 링크 상태 라우팅 프로토콜
	- 링크 정보를 비롯한 현재 네트워크의 상태를 그래프의 형태로 링크 상태 데이터베이스에 저장
	- 네트워크의 구성이 변경되었을 때 라우팅 테이블이 갱신
	- 네트워크의 규모가 매우 커졌을 때는 모든 정보를 저장하기 어렵다. 따라서 AS를 에어리어라는 단위로 나누고 에어리어 내에서만 링크 상태를 공유한다.
	- 에어리어 경계에 있는 ABR이라는 라우터가 에어리어 간의 연결을 담당

**EGP: BFP**
- 대표적인 EGP로는 BGP가 있다. 
- BGP 프로토콜
	- AS 간의 통신에서 사용되는 대표적인 프로토콜로, 엄밀하게는 AS 간의 통신이 '가능한' 프로토콜
	- AS 간의 통신을 위한 eBGP, AS 내의 통신을 위한 iBGP
	- 피어 : BGP 메시지를 주고받을 수 있도록 연결된 BGP 라우터
	- 피어링 : BGP 라우터 끼리 연결되어 피어 관계가 되도록 연결되는 과정
- BGP의 속성
	- AS-PATH : 메시지가 수신지에 이르는 과정에서 통과하는 AS들의 목록
	- NEXT-HOP : 이름 그대로 다음 홉, 다음으로 거칠 라우터의 IP 주소를 나타낸다.
	- LOCAL-PREF : AS 외부 경로에 있어 AS 내부에서 어떤 경로를 선호할지에 대한 척도를 나타내는 속성
- BGP(eBGP)의 특징
	- BGP는 AS 간 라우팅을 할 때 거치게 될 '라우터'의 수가 아닌 'AS'의 수를 고려한다.
	- BGP는 RIP처럼 단순히 수신지에 이르는 '거리'가 아닌, 메시지가 어디를 거쳐 어디로 이동하는지를 나타내는 '경로'를 고려한다.
