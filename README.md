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
