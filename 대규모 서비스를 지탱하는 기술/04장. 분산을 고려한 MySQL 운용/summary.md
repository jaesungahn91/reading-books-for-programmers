# CHAPTER 04. 분산을 고려한 MySQL 운용

## 분산된 시스템 알기
DB 스케일아웃 전략
- 인덱스의 중요성
- MySQL 분산
- 스케일아웃과 파티셔닝

## 강의11. 인덱스를 올바르게 운용하기 : 분산을 고려한 MySQL 운용의 대전제
### 분산을 고려한 MySQL 운용, 세 가지 포인트
- OS 캐시 활용
- 인덱스를 적절하게 설정하기
- 확장을 전제로 한 설계

### OS 캐시 활용
- 전체 데이터 크기에 주의
	- '데이터량 < 물리 메모리'를 유지 -> 메모리가 부족할 경우에는 증설 등
- 스키마 설계가 데이터 크기에 미치는 영향을 고려한다.

### 인덱스의 중요성 - B트리
- 인덱스 = 색인
- B+트리
	- 외부기억장치 탐색 시에 Seek 횟수를 최소화하는 트리 구조
	- 색인의 계산량: O(n) -> O(log n)

### 인덱스 효과
- 계산량 측면에서 개선될 뿐만 아니라 디스크 Seek 횟수면에서도 개선된다.
	- 같은 O(log n)이라도 B트리와 다른 트리 간에는 서로 다르다.
- MySQL은 레코드 총 건수를 보고 인덱스를 사용하지 않는 편이 더 빠르다라고 판단되면, 사용하지 않는 최적화 작업을 내부적으로 수행
- MySQL은 한 번의 쿼리에서 하나의 인덱스만 사용한다는 특성을 갖고 있다.
	- 복수 칼럼에 동시에 인덱스를 태우고자 할 경우는 복합 인덱스를 사용해야 한다.

### 인덱스가 작용하는지 확인하는 법 - explain 명령
- explain 명령
- possible_keys, key, rows 확인
- Extra 열도 중요
	- Using filesort, Using temporary -> 각각 레코드 정렬에 외부 정렬(외부 파일을 사용한 정렬)이나 임시 테이블이 필요하다는 의미
	- 기본적으로 그다지 틀이 좋은 쿼리라고 할 수 없다.

## 강의12. MySQL의 분산 : 확장을 전제로 한 시스템 설계
### MySQL의 레플리케이션 기능
- 마스터/슬레이브 구성
- 참조 쿼리는 슬레이브로, 갱신 쿼리는 마스터로
- O/R 매퍼로 제어한다.

### 마스터/슬레이브의 특징 - 참조계열은 확장하고 갱신계열은 확장하지 않는다.
- 참조계열 쿼리는 확장
	- 서버를 늘리기만 하면 된다.
	- 단, 대수를 늘리기보다도 메모리에 맞추는 것이 중요
- 마스터는 확장하지 않는다.
	- 갱신계열 쿼리가 늘어나면 험난해진다.
	- 단, 웹 애플리케이션은 대부분의 경우 90% 이상이 참조쿼리
	- 마스터 부하는 테이블 분할이나 다른 구현 등으로 연구

## 강의13. MySQL의 스케일아웃과 파티셔닝
### MySQL의 스케일아웃 전략
- 데이터가 메모리에 올라가는 크기? -> YES
- 메모리에 올린다. -> NO
- 메모리 증설
- 메모리 증설이 불가능하면 파티셔닝

### 파티셔닝(테이블 분할)에 관한 보충
- 파티셔닝은 국소성을 활용해서 분산할 수 있으므로 캐시가 유효하고 효과적이다.

### 파티셔닝을 전제로 한 설계
- 파티셔닝을 전제로한 설계가 중요
- 서로 다른 서버에 있는 테이블을 JOIN하는 기능이 기본적으로는 없다.(FEDERATEDB 테이블을 이용하면 가능)
- 따라서 기본적으로 JOIN 쿼리는 대상이 되는 테이블을 앞으로도 서버 분할하지 않을 것이라고 보장할 수 있을 때에만 사용한다.

### JOIN 배제 - where... in... 이용
- JOIN을 사용하지 않고 where... in...으로 결합하는 쿼리를 사용

### 파티셔닝의 상반관계
파티셔닝의 좋은 점은 부하가 내려가고 국소성이 늘어나서 캐시 효과가 높아진다는 점

#### 운용이 복잡해진다
- 서버가 늘어남 -> 운용이 복잡
- 운용이 복잡해지면 결국 복구에 시간이 더걸린다.

#### 고장률이 높아진다
- 대수가 늘어나는 만큼 고장확률이 높아지는 문제가 발생

#### 다중화에 필요한 서보 대수는 몇대?
- 기본은 4대가 1세트(마스터 1대 슬레이브 3대)
- 고장났을 시 승격과 데이터 복사 도중 문제가 발생(서비스를 정지해야함)
- 따라서 다중화를 완벽하게 고려하려면 4대를 1세트로 생각해야 함.