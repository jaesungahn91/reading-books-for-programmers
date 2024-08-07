## 1단계 문제 이해 및 설계 범위 확정
- 시스템 설계 면접 문제는 의도적으로 어떤 정해진 결말을 갖지 않도록 만들어진다.
- 시스템을 성공적으로 설계해 내려면 질문을 통해 모호함을 줄이고 요구사항을 알아내야 한다.

## 개략적 추정
- 쓰기 연산 : 매일 1억 개의 단축 URL 생성
- 초당 쓰기 연산 1억/24/3600 = 1160
- 읽기 연산 : 초당 11,600회
- 3650억 개의 레코드
- 축약 전 URL의 평균 길이는 100
- 10년 동안 필요한 저장 용량은 36.5TB

## 2단계 개략적 설계안 제시 및 동의 구하기
### API 엔드포인트
- 두 개의 엔드포인트 필요
	- URL 단축용 엔드포인트
	- URL 리디렉션용 엔드포인트

### URL 리디렉션
- 301 Permanently Moved : 해당 URL에 대한 HTTP 요청의 처리 책임이 영구적으로 Location 헤더에 반환된 URL로 이전되었다는 응답.
- 302 Found : '일시적으로' Location 헤더가 지정하는 URL에 의해 처리되어야 한다는 응답

### URL 단축
- 요구 사항
	- 입력으로 주어지는 긴 URL이 다른 값이면 해시 값도 달라야 한다.
	- 계산된 해시 값은 원래 입력으로 주어졌던 긴 URL로 복원될 수 있어야 한다.

## 3단계 상세 설계
### 데이터 모델
- <단축 URL, 원래 URL>의 순서쌍을 관계형 데이터베이스에 저장

### 해시 함수
- 해시 값 길이 : hashValue는 62개의 문자 개수 길이를 위해 62^7 = 3.5조 개 URL
- 해시 함수 구현에 쓰일 기술
	- 해시 후 충돌 해소
	- base-62 변환

## 4단계 마무리
- 추가 설계에 생각해 볼 것
	- 처리율 제한 장치
	- 웹 서버의 규모 확장
	- 데이터베이스의 규모 확장
	- 데이터 분석 솔루션
	- 가용성, 데이터 일관성, 안정성