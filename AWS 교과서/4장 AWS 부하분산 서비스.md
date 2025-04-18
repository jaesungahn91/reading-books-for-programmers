## 4.1 Amazon ELB 기능 소개
### 4.1.1 부하분산이란
- 부하분산은 서버-클라이언트 환경에서 서버가 클라이언트 요청을 받아 처리하는 과정에서 발생하는 부하에 대해 동일한 목적을 수행하는 다수의 서버에 분산 처리하는 기능
- 고가용성 및 내결함성이 향상
- 부하분산을 로드 밸런싱이라고하며, 수행하는 대상을 로드 밸런서라고 한다.
### 4.1.2 Amazon ELB 기능
- 트래픽을 자동 분산 처리하는 기술
- 다양한 프로토콜 지원
- 오토 스케일링 기능과 결합
- SSL 암호화 지원
### 4.1.3 Amazon ELB 구성요소
- 로드 밸런서: 트래픽을 대상 그룹에 있는 인스턴스로 분산시켜 애플리케이션의 가용성을 유지하는 역할
- 대상 그룹: 로드 밸런서에서 분산할 대상의 집하을 정의하는 구성 요소
- 리스너: 로드 밸러서에서 사용할 포트와 프로토콜을 설정하는 구성 요소
### 4.1.4 Amazon ELB 동작 방식
1. 클라이언트 요청 수신
2. 대상 그룹 선택
3. 트래픽 분산
4. 응답 반환
### 4.1.5 Amazon ELB 교차 영역 로드 밸런싱
- 여러 가용 영역에 걸쳐 있다면 기본적으로 로드 밸러서는 동일한 비중으로 가용 영역 내에 있는 대상으로 트래픽을 분산
- 불균형 처리 문제 발생
- ELB 교차 영역 로드 밸런싱으로 해결
	- 트래픽을 분산하는 기준이 가용 영역이 아닌 대상 그룹에 속한 자원으로 기준
### 4.1.6 Amazon ELB 종류
- CLB
	- 초기 출시
	- 레거시 서비스
- ALB
	- L7 로드 밸런서
	- 웹 애플리케이션 프로토콜 지원
	- 대상 그룹 단위로 트래픽 분산
	- 웹 애플리케이션에 특화된 세밀한 라우팅 제어 가능
- NLB
	- L4 로드 밸런서
	- TCP, UDP, TLS 프로토콜 지원
	- 대규모 트래픽 처리 가능
	- 높은 처리량, 빠른 응답 시간, 높은 가용성, IP 주소 보존, 모니터링
- GWLB
	- 네트워크 트래픽을 서드 파티의 방화벽/어플라이언스 장비로 부하분산 처리하는 로드 밸런서