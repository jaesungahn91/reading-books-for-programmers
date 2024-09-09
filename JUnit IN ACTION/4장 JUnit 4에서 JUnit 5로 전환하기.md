## 4.1 JUnit 4에서 JUnit 5로의 전환 과정
- JUnit은 JUnit Vintage 테스트 엔진을 활용하여 테스트를 JUnit 4에서 JUnit 5로 전환하는 로드맵을 제시
- 중요 단계
	- 의존성을 교체
	- 애노테이션 교체
	- 테스트 클래스와 메서드 교체
	- JUnit 4 rule과 runner를 JUnit 5의 확장 모델로 교체
- 자바 버전 갱신
	- JUnit 4는 자바 5이상 요구
	- JUnit 5는 자바 8이상 요구

## 4.2 JUnit 4에서 JUnit 5로 전환하는 데 필요한 의존성
- JUnit 5 Vintage 적용하는 것이 전환하는 첫 번째 단계
- JUnit 4 애노테이션을 JUnit 5 Jupiter 애노테이션으로 교체
- junit-jupiter-api와 junit-jupiter-engine 의존성 추가
- 파라미터 테스트를 위한 junit-jupiter-params 의존성 추가(옵셔널)

## 4.3 JUnit 5 애노테이션, 클래스, 메서드
