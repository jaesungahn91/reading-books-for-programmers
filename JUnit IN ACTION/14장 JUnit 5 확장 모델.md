- Extension 자체는 내부에 필드나 메서드가 없는 인터페이스인 마커 인터페이스이다.
- 확장 지점의 종류 및 구현 인터페이스
	- 조건부 테스트 실행 : ExecutionCondition
	- 생애 주기 콜백 : BeforeAllCallback, AfterAllCallback, BeforeEachCallback, AfterEachCallback
	- 파라미터 리졸브 : ParameterResolver
	- 예외 처리 : TestExecutionExceptionHandler
	- 테스트 인스턴스 후처리 : TestInstancePostProcessor