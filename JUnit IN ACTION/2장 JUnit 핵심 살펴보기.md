- 테스트 메서드 : @Test, @RepeatedTest, @ParameterizedTest, @TestFactory, @TestTemplate
- 생애 주기 메서드 : @BeforeAll, @AfterAll, @BeforeEach, @AfterEach
- 테스트 메서드는 추상 메서드일 수 없으며 반환 값을 가질 수 없다. 반환 타입은 반드시 void여야 한다.
- JUnit 5를 구동하는 데 필요한 최소한의 의존성
	- junit-jupiter-api
	- junit-jupiter-engine
- JUnit은 테스트 메서드의 격리성을 보장하고 테스트 코드에서 의도치 않은 부수효과를 방지하기 위해, @Test 메서드를 호출하기 전에 테스트 클래스 인스턴스를 매번 새로 만든다.
- 테스트 클래스에 @TestInstance(Lifecycle.PER_CLASS) 애노테이션이 없다면 @AfterAll, @BeforeAll 테스트 메서드는 정적으로 선언해야 한다.

- 중첩 테스트는 개발자가 테스트 그룹 간의 관계를 표현하는 데에도 도움이 된다.
- 테스트를 몇몇 카테고리로 범주화할 때 태그를 사용
- JUnit Jupiter의 모든 단언문은 `org.junit.jupiter.api.Assertions` 클래스
- assertAll 메서드의 좋은 점은 일부 단언문이 실패하더라도 모든 단언문을 항상 검증한다.
- assumingThat 메서드를 제공하며 이 메서드는 가정이 충족된 경우에만 단언문을 실행

- @RepeatedTest 애노테이션을 사용하여 반복 횟수를 지정한 후 해당 횟수만큼 테스트를 반복할 수 있다.
	- name 속성으로 반복마다 디스플레이 네임을 표현 가능
- @ParameterizedTest
	- @ValueSource
	- @EnumSource
	- @CsvSource
	- @CsvFileSource

- JUnit 5는 런타임에 테스트를 생성할 수 있는 동적 프로그래밍 모델을 도입
	- @TestFactory 애노테이션
- Hamcrest 라이브러리로 복잡한 단언문을 간명하게 만든다.