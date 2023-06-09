# 02. 이상한 나라의 객체
> 객체지향 패러다임은 지식을 추상화하고 추상화한 지식을 객체 안에 캡슐화함으로써 실세계 문제에 내제된 복잡성을 관리하려고 한다. 객체를 발견하고 창조하는 것은 지식과 행동을 구조화하는 문제다.
> - 레베카 워프스브록

## 객체지향과 인지 능력
- 인간은 선천적으로 타고난 인지 능력을 이용해 세상에 존재하는 다양한 객체를 식별하고 분류함으로써 세상을 이해한다.
- 인간은 본능적으로 세상을 독립적이고 식별 가능한 객체의 집합으로 바라본다.
- 이러한 이유로 많은 사람들이 객체 지향을 직관적이고 이해하기 쉬운 패러다임이라고 말한다.
- 인간의 인지 능력은 물리적인 한계를 넘어 개념적으로 경계 지을 수 있는 추상적인 사물까지도 객체로 인식할 수 있게 한다.

- 객체란 인간이 분명하게 인지하고 구별할 수 있는 물리적인 또는 개념적인 결계를 지닌 어떤 것이다.
- 객체지향 패러다임의 목적은 현실 세계를 모방하는 것이 아니라 현실 세계를 기반으로 새로운 세계를 창조하는 것
- 겉으로는 우리가 알고 있는 세계와 유사해 보이지만 본질적으로는 매우 이질적인 모습을 지닌 세계와 마주치게 될 것이다.

## 객체, 그리고 이상한 나라
### 앨리스 객체
```text
- 앨리스는 상태를 가지며 상태는 변경 가능하다.
- 앨리스의 상태를 변경시키는 것은 앨리스의 행동이다.
	- 행동의 결과는 상태에 의존적이며 상태를 이용해 서술할 수 있다.
	- 행동의 순서가 결과에 영향을 미친다.
- 앨리스는 어떤 상태에 있더라도 유일하게 식별 가능하다.
```

## 객체, 그리고 소프트웨어 나라
> 객체란 식별 가능한 개체 또는 사물이다. 객체는 자동차처럼 만질 수 있는 구체적인 사물일 수도 있고, 시간처럼 추상적인 개념일 수도 있다. 객체는 구별 가능한 식별자, 특징적인 행동, 변경가능한 상태를 가진다. 소프트 웨어 안에서 객체는 저장된 상태와 실행 가능한 코드를 통해 구현된다.

### 상태
#### 상태가 왜 필요한가
- 어떤 행동의 결과는 과거에 어떤 행동들이 일어났었느냐에 의존
- 발생한 행동의 이력을 통해 현재 발생한 행동의 결과를 판단하는 방식은 복잡하고 번거로우며 이해하기 어려움
- 따라서 인간은 행동의 과정과 결과를 단순하게 기술하기 위해 상태라는 개념을 고안
- 상태를 이용하면 과거에 얽매이지 않고 현재를 기반으로 객체의 행동 방식을 이해할 수 있다.
- 상태는 근본적으로 세상의 복잡성을 완하하고 인지 과부하를 줄일 수 있는 중요한 개념

#### 상태와 프로퍼티
- 단순한 값들은 그 자체로 독립적인 의미를 가지기보다는 다른 객체의 특성을 표현하는데 사용된다. 다시 말해 다른 객체의 상태를 표현하기 위해 사용
- 객체의 상태를 구성하는 모든 특징을 통틀어 객체의 프로퍼티라고 한다.
	- 프로퍼티는 변경되지 않고 고정되기 때문에 '정적'
	- 프로퍼티 값은 시간이 흐름에 따라 변경되기 때문에 '동적'
- 객체와 객체 사이의 의미 있는 연결을 '링크'라고 한다.
- 객체의 프로퍼티는 단순한 값인 속성과 다른 객체를 가리키는 링크라는 두 가지 종류의 조합으로 표현할 수 있다.

> 상태는 특정 시점에 객체가 가지고 있는 정보의 집합으로 객체의 구조적 특징을 표현한다. 객체의 상태는 객체에 존재하는 정적인 프로퍼티와 동적인 프로퍼티 값으로 구성된다. 객체의 프로퍼티는 단순한 값과 다른 객체를 참조하는 링크로 구분할 수 있다.

### 행동
#### 상태와 행동
- 행동이 부수 효과(side effect)를 초래 -> 행동은 객체 자신의 상태를 변경
- 행동의 결과는 객체의 상태에 의존적이다.
- 객체의 행동은 상태에 영향을 받는다.
- 객체의 행동은 상태를 변경시킨다.
- 상태를 이용하면 복잡한 객체의 행동을 쉽게 이해할 수 있다.

#### 협력과 행동
- 객체의 행동은 객체가 협력에 참여할 수 있는 유일한 방법이다.
- 객체의 행동으로 인행 발생하는 결과
	- 객체 자신의 상태 변경
	- 행동 내에서 협력하는 다른 객체에 대한 메시지 전송

> 행동이란 외부의 요청 또는 수신된 메시지에 응답하기 위해 동작하고 반응하는 활동이다. 행동의 결과로 객체는 자신의 상태를 변경하거나 다른 객체에게 메시지를 전달할 수 있다. 객체는 행동을 통해 다른 객체와의 협력에 참여하므로 외부에 가시적이어야 한다.

#### 상태 캡슐화
- 현실 세계의 객체와 객체지향 세계의 객체사이의 중요한 차이점
	- 객체지향의 세계에서는 모든 객체는 자신의 상태를 스스로 관리하는 자율적인 존재
- 객체는 상태를 캡슐 안에 감춰둔 채 외부로 노출하지 않는다 -> 캡슐화
	- 객체가 외부에 노출하는 것은 행동뿐이며, 외부에서 객체에 접근할 수 있는 유일한 방법 역시 행동뿐

> 캡슐화는 객체의 자율성을 높임 -> 객체의 지능이 높아짐 -> 협력은 유연하고 간결해짐

### 식별자
- 객체안에 존재하는 객체를 구별할 수 있는 특정한 프로퍼티를 식별자라고 한다.
- 객체는 식별자를 가진다.
- 값의 경우 두 인스턴스의 상태가 같다면 같은 인스턴스로 판단
	- 동등성
- 객체의 경우 식별자가 같다면 같은 객체로 판단
	- 동일성

> 식별자란 어떤 객체를 다른 객체와 구분하는 데 사용하는 객체의 프로퍼티다. 값은 식별자를 가지지 않기 때문에 상태를 이용한 동등성 검사를 통해 두 인스턴스를 비교해야 한다. 객체는 상태가 변경될 수 있기 때문에 식별자를 이용한 동일성 검사를 통해 두 인스턴스를 비교할 수 있다.

- 참조객체(reference object), 엔티티(entity) -> 식별자를 지닌 객체를 가리키는 용어
- 값 객체(value object) -> 식별자를 가지지 않는 값을 가리키는 용어

엘리스 -> 객체
```text
- 객체는 상태를 가지며 상태는 변경 가능하다.
- 객체의 상태를 변경시키는 것은 객체의 행동이다.
	- 행동의 결과는 상태에 의존적이며 상태를 이용해 서술할 수 있다.
	- 행동의 순서가 결과에 영향을 미친다.
- 객체는 어떤 상태에 있더라도 유일하게 식별 가능하다.
```

## 기계로서의 객체
- 객체의 상태를 조회하는 작업 -> 쿼리(query)
- 객체의 상태를 변경하는 작업 -> 명령(command)

```text
- 사각형 버튼 : 상태를 변경하는 명령
- 둥근 버튼 : 상태를 조회하는 쿼리
```

> 기계를 예로들어 전달된 메시지에 따라 스스로 판단하고 결정하는 자율적인 객체의 특성을 묘사

## 행동이 상태를 결정한다
- 상태를 먼저 결정하고 행동을 나중에 결정하는 방법은 설계에 나쁜영향을 끼침
	- 상태를 먼저 결정할 경우 캡슐화 저하
	- 객체를 협력자가 아닌 고립된 섬으로 만듦
	- 객체의 재사용성이 저하
- 객체의 적합성을 결정하는 것은 상태가 아니라 객체의 행동
	- 따라서 행동에 초점을 맞춰야함
- 책임-주도 설계는 응집도가 높고 재사용 가능한 객체를 만들 수 있게 한다.

> 행동이 상태를 결정한다

## 은유와 객체
### 두 번째 도시전설
- 객체지향 세계는 현실 세계의 단순한 모방이 아니다.
- 객체지향이 현실을 오롯이 모방하기만 한다는 것은 오해일 뿐이다.

### 의인화
- 현실 속에서는 수동적인 존재가 소프트웨어 객체로 구현될 때는 능동적으로 변한다.
- 현실의 객체보다 더 많은 일을 할 수 있는 소프트웨어 객체의 특징을 의인화(antheropomorphism)이라고 부른다.

### 은유
- 객체지향 분석/설계에 관한 전통적인 관점은 객체지향 애플리케이션이 현실의 구조를 정확하게 반영해야 한다는 오해만 심어준다.
- 현실 세계와 객체지향 세계 사이의 관계를 좀 더 정확하게 설명할 수 있는 단어는 은유(metaphor)다.
- 현실 객체의 은유를 효과적으로 사용 -> 표현적 차이를 줄임 -> 이해하기 쉽고 유지보수가 용이한 소프트웨어를 만들 수 있다.