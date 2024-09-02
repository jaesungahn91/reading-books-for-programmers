## 3.1 소프트웨어 아키텍처의 개념과 중요성
- 소프트웨어 아키텍처 : 소프트웨어 시스템의 기본 구조
- 소프트웨어 시스템 구조는 소프트웨어 요소, 소프트웨어 요소 간의 관계, 요소와 관계를 이루는 속성들로 구성
- 소프트웨어 아키텍처의 기초를 이루는 요소는 물리적인 아키텍처의 기초만큼이나 이동이나 교체가 어렵다.

## 3.2 JUnit 4 아키텍처
- JUnit 5는 JUnit Vintage를 통해 기존 레거시 프로젝트에서 이전 JUnit 4 코드와 함께 작동하도록 설계

### 3.2.1 JUnit 4 모놀리식 아키텍처
- JUnit 4는 단순한 모놀리식 아키텍처

### 3.2.2 JUnit 4 runner
- JUnit 4 runner는 JUnit 테스트의 실행을 담당
- JUnit 4 runner는 리플렉션을 사용하여 테스트를 확장 -> 캡슐화 저해

### 3.2.3 JUnit 4 rule
- JUnit 4 rule은 테스트 메서드 호출을 가로채는 컴포넌트.
- JUnit 4 rule을 사용해서 테스트 메서드가 실행되기 전후에 다른 작업을 수행할 수 있다.
- 실행할 테스트에 동작을 추가하려면 TestRule 인터페이스를 구현한 필드에 @Rule 애노테이션을 사용
- ExpectedException, TemprorayyFolder
- JUnit 4 rule을 작성하려면 TestRule 인터피에스를 구현하는 클래스를 만들어야 함
- JUnit 5에서 4를 사용하는 데 필요한 의존성은 `junit-vintage-engine`

### 3.2.4 JUnit 4 아키텍처의 단점
- JUnit 4가 제공하는 API가 충분히 유연하지 못해 IDE나 빌드 도구와 지나치게 결합도가 높아짐

## 3.3 JUnit 5 아키텍처
### 3.3.1 JUnit 5 모듈성
- 요구사항
	- 개발자가 주로 사용하는 테스트를 작성하기 위한 API
	- 테스트를 발견하고 실행하는 데 사용하는 메커니즘
	- IDE나 빌드 도구와 쉽게 상호작용하고 테스트를 구동할 수 있는 API
- 세 가지 모듈
	- JUnit Platform : JVM 위에서 테스트 프레임워크를 구동하기 위한 기반이 되는 플랫폼, 또한 콘솔, IDE, 빌드 도구에서 테스트를 구동할 수 있는 API도 제공 
	- JUnit Jupiter : JUnit 5에서 테스트와 extension을 만들 수 있도록 프로그래밍 모델과 확장 메돌을 결합
	- JUint Vintage : 3, 4 기반의 테스트를 실행하기 위한 테스트 엔진으로, 하위 호환성을 보장

### 3.3.3 JUnit Jupiter
- JUnit Jupiter의 확장 모델은 하나의 일관된 개념인 Extension API로만 구성