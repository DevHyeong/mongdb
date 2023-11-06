# mongdb

## NoSQL
- 장점
  - 데이터 접근성과 가시성이 좋다.
  - Join없이 조회가 가능해서 응답 속도가 일반적으로 빠르다.
  - 스키마 변경에 공수가 적다
  - 스키마가 유연해서 데이터 모델을 어플리케이션 요구사항에 맞게 데이터를 수용할 수 있다.
  - HA와 Sharding에 대한 솔루션을 자체적으로 지원하고 있어 Scale-out이 간편하다.
- 단점
  - 데이터 중복이 발생한다
  - 스키마가 자유롭지만 스키마 설계를 잘해야 성능 저하를 피할 수 있다.

## mongdb 구조
- Cluster (cluster)
- Database (database)
- Collection (table)
- Document (row)
- Field (column)

- admin, config, local 데이터베이스(default database)는 mongdb를 관리하는데 사용된다.

### Collection
- 동적 스키마를 갖는다.
- 동적 스키마를 갖지만 스키마는 어느정도 유지해야한다. (index, shard 등을 사용하기 위함)

### Document 
- mongdb는 저장할때 bjson(binary json)으로 저장한다. 표현은 json형태
- 고유한 _id 필드를 항상 갖고 있다.
- Document의 최대 크기는 16MB이다.

## 배포 형태

### Replica Set
- HA(고가용성)을 위한 솔루션
- 
- 데이터 들고 있는 멤버의 상태는 Primary와 Secondary가 있다.
- Oplog에 저장, 이후에 

### Shared Cluster
- 분산 처리를 위한 솔루션
- 모든 Shard는 Replica Set으로 구성되어 있다.
- sharding: 데이터를 분할하는 과정. shard: 분할된 모음, shard key: 분산의 기준, chunk: 데이터 분할 단위
- write에 대한 부하가 클 경우 해당 솔루션을 사용한다. (Replica set보다 성능이 좋지 않다. 이유: 데이터가 분산되어 있어서 shard를 조회하고 머지하는 과정이 있기 때문)
- 아키텍처의 구성: Config server(메타데이터 소유), mongos(router), Shard 3개의 컴포넌트로 구성
- 컬렉션을 생성 후 각각의 shard에 데이터를 분산하지 않고 하나의 shard에서 관리할 때도 있다. (빈도수가 잦은 데이터)
- 샤딩을 위한 전략
  - ranged sharding
  - Hashed sharding (가장 많이 사용)
  - zone sharding

## 일관성 제어
- Single Document : 원자성 보장
- Transaction: 여러 작업(multi document)에 대한 원자성을 보장, mongodb에서 권장하지 않음
- Replica Set member: 동일한 데이터를 여러 멤버에게 저장, 멤버 간의 데이터 일관성에 대한 제어가 필요
- Sharded Cluster Shard : shard간에 동일한 데이터가 갖지 않도록 제어가 필요




