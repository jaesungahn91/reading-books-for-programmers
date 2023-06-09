# 03. 타입과 추상화
> 일단 컴퓨터를 조작하는 것이 추상화를 구축하고, 조작하고, 추론하는 것에 관한 모든 것이라는 것을 깨닫고 나면 (훌륭한) 컴퓨터 프로그램을 작성하기 위한 중요한 전제 조건은 추상화를 정확하게 다루는 능력이라는 것이 명확해진다.
> - 키스 데블린

## 추상화를 통한 복잡성 극복
- 현실은 복잡 + 예측 불가능 -> 현실을 분해하고 단순화하는 전략이 필요
- 헤리 벡의 지하철 노선도는 불필요한 지형 정보를 제거함으로써 단순함을 달성한 추상화의 훌륭한 예
	- 지하철 노선도를 이용하는 승객들의 목적에 맞게 현실을 단순화
- 추상화란 현실에서 출발하되 불필요한 부분을 도려내가면서 사물의 놀라운 본질을 드라나게 하는 과정
```text
추상화
어떤 양상, 세부 사항, 구조를 좀 더 명확하게 이해하기 위해 특정 절차나 물체를 의도적으로 생략하거나 감춤으로써 복잡도를 극복하는 방법

복장섭을 다루기 위해 추상화는 두 차원에서 이뤄진다
- 구체적인 사물들 간의 공통점은 취하고 차이점은 버리는 일반화를 통해 단순하게 만듦
- 중요한 부분을 강조하기 위해 불필요한 세부 사항을 제거함으로써 단순하게 만듦

추상화의 목적은 복잡성을 이해하기 쉬운 수준으로 단순화하는 것
```
> 객체지향 패러다임은 객체라는 추상화를 통해 현실의 복잡성을 극복

## 객체지향과 추상화
### 모두 트럼프일 뿐
- 앨리스는 '트럼프'라는 하나의 개념으로 단순화함
	- 인물들을 계급, 나이, 성격 등의 차이점은 무시한 채 '트럼프'라는 유사성을 기반으로 추상화

### 그룹으로 나누어 단순화하기
- 공통적으로 '트럼프'라고 했을 때 떠오르는 일반적인 외형과 행동 방식으로 묶고 차이점을 무시하면 '트럼프'라는 그룹으로 나눌 수 있다.
	- 그룹으로 나누면 복잡성을 효과적으로 감소

### 개념 
- 공통점을 기반으로 객체들을 묶기 위한 그릇을 개념(concept)이라고 한다.
- 개념이란 일반적으로 우리가 인식하고 있는 다양한 사물이나 객체에 적용할 수 있는 아이디어나 관념을 뜻한다.
- 객체에 어떤 개념을 적용하는 것이 가능해서 개념 그룹의 일원이 될 때 객체를 그 개념의 인스턴스(instance)라고 한다.
> 객체란 특정한 개념을 적용할 수 있는 구체적인 사물을 의미한다. 개념이 객체에 적용됐을 때 객체를 개념의 인스턴스라고 한다.

### 개념의 세 가지 관점
```text
- 심볼(symbol) : 개념을 가리키는 간략한 이름이나 명칭
- 내연(intension) : 개념의 완전한 정의를 나타내며 내연의 의미를 이용해 객체가 개념에 속하는지 여부를 확인할 수 있다.
- 외연(extension) : 개념에 속하는 모든 객체의 집합(set)
```
- 분류(classification) -> 클래스(class)

### 객체를 분류하기 위한 틀
> 분류란 객체에 특정한 개념을 적용하는 작업이다. 객체에 특정한 개념을 적용하기로 결심했을 때 우리는 그 객체를 특정한 집합의 멤버로 분류하고 있는 것이다.
- 객체를 적절한 개념에 따라 분류한 애플리케이션은 유지보수가 용이하고 변경에 유연하게 대처할 수 있다.
	- 직관적으로 분류

### 분류는 추상화를 위한 도구다
- 개념을 통해 객체르 분류하는 과정은 추상화의 두 가지 차원을 모두 사용
- 개념은 객체들의 복잡성을 극복하기 위한 추상화 도구
- 추상화를 사용함으로써 복잡한 이 세상을 제어 가능한 수준으로 단순화할 수 있음

## 타입
### 타입은 개념이다
> 타입은 개념과 동일하다. 따라서 타입이란 우리가 인식하고 있는 다양한 사물이나 객체에 적용할 수 있는 아이디어나 관념을 의미한다. 어떤 객체에 타입을 적용할 수 있을 때 그 객체를 타입의 인스턴스라고 한다. 타입의 인스턴스는 타입을 구성하는 외연인 객체 집합의 일원이 된다.

### 데이터 타입
- 컴퓨터 안에 살아가는 데이터를 목적에 따라 분류하기 시작하면서 프로그래밍 언어 안에서 서서히 타입 시스템이(type system)이 자라남
- 타입 시스템의 목적은 데이터가 잘못 사용되지 않도록 제약사항을 부과하는 것
- 타입은 데이터가 어떻게 사용되느냐에 관한 것
- 타입에 속한 데이터를 메모리에 어떻게 표현하는지는 외부로부터 철저하게 감춰진다
> 데이터 타입은 메모리 안에 저장된 데이터의 종류를 분류하는 데 사용하는 메모리 집합에 관한 메타데이터이다. 데이터에 대한 분류는 암시적으로 어떤 종류의 연산이 해당 데이터에 대해 수행될 수 있는지를 결정한다.

### 객체와 타입
- 전통적인 데이터 타입, 객체지향 타입 사이에는 깊은 연관성
	- 객체를 일종의 데이터처럼 사용
	- 객체를 타입에 따라 분류하고 그 타입에 이름을 붙이는 것 -> 프로그램에서 사용할 새로운 데이터 타입을 선언하는 것과 같음
- 어떤 객체가 어떤 타입에 속하는지를 결정하는 것은 객체가 수행하는 행동이다.
- 객체의 내부적인 표현은 외부로부터 철저하게 감춰진다.

### 행동이 우선이다.
- 객체가 어떤 행동을 하느냐에 따라 객체의 타입이 결정
	- 객체 내부 표현과는 아무런 상관이 없다
-> 동일한 책임을 수행하는 일련의 객체는 동일한 타입에 속한다라고 말할 수 있다.
> 동일한 타입으로 분류하는 기준 = 동일한 행동 / 다른 행동 -> 다른 타입

- 다형성이란 동일한 요청에 대해 서로 다른 방식으로 응답할 수 있는 능력
	- 동일한 메시지를 서로 다른 방식으로 처리 -> 동일한 메시지를 수신 -> 다형적인 객체들은 동일한 타입
- 행동만이 고려 대상이라는 사실은 외부에 데이터를 감춰야 한다는 것을 의미
	- 훌륭한 객체지향 설계는 외부에 행동만을 제공하고 데이터는 행동 뒤로 감춰야 한다.
	- 이 원칙을 흔히 캡슐화라고 한다.
- 책임-주도 설계는 데이터-주도 설계방법의 단점을 개선하기 위해 고안
> 객체를 결정하는 것은 행동이다. 데이터는 단지 행동을 따를 뿐이다. 이것이 객체를 객체답게 만드는 가장 핵심적인 원칙

## 타입의 계층
### 트럼프 계층
- 트럼프 인간은 트럼프보다 좀 더 특화된 행동을 하는 특수한 개념.
- 이 두 개념 사이의 관계를 일반화/특수화(seneralization/specialization) 관계라고 한다.

### 일반화/특수화 관계
- 더 특수하다는 것은 일반적인 개념보다 범위가 더 좁다는 것을 의미
- 객체지향에서 일반화/특수화 관계를 결정하는 것은 객체의 상태를 표현하는 데이터가 아니라 행동이라는 것
- 객체의 일반화/특수화 관계에 있어서도 중요한 것은 객체가 내부에 보관한 데이터가 아니라 객체가 외부에 제공하는 행동
> 일반화/특수화는 행동에 관한 것이다. 일반적인 타입은 특수한 타입에 비해 더 적은 수의 행동을 가지며 특수한 타입은 일반적인 타입에 비해 더 많은 행동을 가진다. 단. 특수한 타입은 일반적인 타입이 할 수 있는 모든 행동을 동일하게 수행할 수 있어야 한다.
- 행동의 가짓수와 외연을 의미하는 집합의 크기는 서로 반대

### 슈퍼타입과 서브타입
- 일반적인 타입을 슈퍼타입(Supertype), 좀 더 특수한 타입을 서브타입(Subtype)이라고 한다.
- 서브타입은 슈퍼타입의 행위와 호환되기 때문에 서브타입은 슈퍼타입을 대체할 수 있어야 한다.
- 일반화/특수화 관계 표기법
	- 슈퍼타입을 상단에, 좀 더 특수한 타입인 서브타입을 하단에 위치시키고 속이 빈 삼각형으로 연결해서 표현

### 일반화는 추상화를 위한 도구다
- 두 가지 추상화 기법이 함께 사용
	- 공통점만 강조
	- 더 단순한 관점에서 바라보기 위해 불필요한 특성을 배제하고 일반화

## 정적 모델
### 타입의 목적
- 타입을 사용하는 이유는 인간의 인지 능력으로 시간에 따라 동적으로 변하는 객체의 복잡성을 극복하기가 너무 어렵기 때문
- 객체의 상태는 변하지만 식별성은 동일하게 유지
- 상태에 복잡성을 부과하는 시간이라는 요소를 제거 -> 시간에 독집적인 정적인 모습

### 그래서 결국 타입은 추상화다
- 타입은 추상화다. 타입을 이용하면 객체의 동적인 특성을 추상화할 수 있다. 결국 타입은 시간에 따른 객체의 상태 변경이라는 복잡성을 단순화할 수 있는 효과적인 방법이다.

### 동적 모델과 정적 모델
- 객체가 특정 시점에 구체적으로 어떤 상태를 가지냐를 스냅샷이라고 한다.
	- UML에서는 스냅샷(snapshot)을 객체 다이어그램(object diagram)이라고도 부른다.
- 객체가 살아 움직이는 동안 상태가 어떻게 변하고 어떻게 행동하는지를 포착하는 것을 동적 모델(dynamic model)이라고 한다.
- 객체가 가질 수 있는 모든 상태와 모든 행동을 시간에 독립적으로 표현한 모델을 타입 모델(type diagram)이라고 한다.
	- 정적 모델(static model)이라고도 한다.

### 클래스
- 객체지향에서 중요한 것은 동적으로 변하는 객체의 '상태'와 상태를 변경하는 '행위'다. 클래스는 타입을 구현하기 위해 프로그래밍 언어에서 제공하는 구현 메커니즘이다.