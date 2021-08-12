- 적재된 data를 탐색/분석하기 위해 기존에는 Map-Reduce를 주로 사용.
  - Map-Reduce를 사용할 시 복잡하며, Java를 이용해야 한다.

> 이를 해결하기 위해 Hive를 개발(SQL on Hadoop)

# Hive

## 구성 요소

- CLI
> 사용자가 Hive Query를 입력하고 실행할 수 있는 interface(Hive Server 1기반 CLI와 Hive Server 2기반 Beeline이 있다.)

- JDBC/ODBC Driver
> Hive Query를 다양한 DB와 연결하기 위한 Driver를 제공

- Query Engine
> 사용자가 입력한 Hive Query를 분석하며, 실행 계획을 수립
> **Hive Query를 Map-Reduce code로 변환 및 실행**

- Metastore
> Hive에서 사용하는 Table, Schema를 저장 및 관리
> file 구조를 Hive Metastore DB에 meta화하여 저장.


### External & managed

- external(data lake)
> schema 제약 X

- managed(data warehouse)
> schema 제약 O (규약을 잘 지키도록 구성해야할 필요성이 있다.)


## 추가

### Pig
- Map-Reduce의 복잡성을 해결하기 위한 것
- SQL 대신 Pig Latin이라는 언어를 사용. 절차적 요소를 많이 사용.

> Hive가 가공/적재/탐색 등에 최적화되었다면
> 
> Pig는 HDFS file에 직접 접근하여 복잡한 데이터 파이프라인을 처리하는데 적합하다.


#### Hive(SQL)와 Pig

- SQL은 interactive한 구조.
- Pig는 절차적으로 좀 더 복잡한 기능 구현 가능.
