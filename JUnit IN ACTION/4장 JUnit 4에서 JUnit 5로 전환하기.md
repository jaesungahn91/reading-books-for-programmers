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
### 4.3.1 JUnit 4와 JUnit 5에서 비슷하게 사용하는 애노테이션, 클래스, 메서드
- 애노테이션
	- @BeforeClass, @AfterClass -> @BeforeAll, @AfterAll
	- @Before, @After -> @BeforeEach, @AfterEach
	- @Ignore -> @Disabled
	- @Category -> @Tag
- 단언문
	- Assert 클래스 -> Assertions 클래스
	- 단언문 메시지 첫 번째 파라미터 -> 마지막 파라미터
	- assertThat 메서드 사용 -> assertAll, assertThrows 메서드 추가
- 가정문
	- Assume 클래스 -> Assumptions 클래스
	- assumeNotNull, assumeNoException 메서드 -> 사용 불가
- JUnit 5로 넘어오면서 테스트 메서드에 대한 기본 접근 제어 수준이 public에서 디폴트로 완화

### 4.3.2 JUnit 4의 @Category와 JUnit 5의 @Tag
- 그룹화 작업을 위해 JUnit 4에서 @Category를 사용했다면, JUnit 5에서는 @Tag를 사용
- 카테고리 단점
	- 테스트 묶음을 위한 특별한 인터페이스 생성해야함
	- @Category의 파라미터에 들어갈 마커 인터페이스를 전부 따로 정의
- JUnit 5 태그를 사용하기 위해서는 미리 몇 가지 설정 작업 필요
	- Maven 설정 파일이나 IDE를 이용

### 4.3.4 JUnit 4 rule과 JUnit 5의 확장 모델
- JUnit 4 rule은 메서드가 실행될 때 호출을 가로채고 메서드 실행 전후에 추가 작업을 수행할 수 있는 JUnit 4 컴포넌트
- ExpectedException -> assertThrows 대체
- TemporaryFolder -> @TempDir 애노테이션으로 대체

### 4.3.5 사용자 정의 rule을 extension으로 전환하기
- JUnit 4
	- TestRule 인터페이스를 구현하는 클래스 생성
	- Statement 객체를 반환하는 apply 메서드를 재정의
- JUnit 5
	- AfterEachCallback, BeforeEachCallback 인터페이스 구현
	- @ExtendWith 추가
