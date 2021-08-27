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

## Hive의 특징
- Hive는 하둡에 적재되어 있는 파일의 메타정보(파일의 위치, 이름, 포맷 등) 테이블의 스키마 정보와 함께 메타 스토어에 등록, **RDBMS에서 데이터를 조회 및 탐색하는 것 같은 기능**(SQL on Hadoop. 내부 매커니즘은 RDBMS와 전혀 다르다)을 제공

1. **하이브 쿼리는 맵리듀스로 변환하여 실행**
  - 복잡도에 따라 여러 job이 순차적으로 만들어진다.
  - 데이터의 크기와 조건에 따라 여러 Map과 Reduce 작업이 생성되어 실행된다.
2. **대화형 온라인 쿼리 사용에 부적합**
  - MapReduce로 변환되어 실행되기 까지 최소 10~30초 이상의 준비시간이 필요 -> **대규모 Batch에 적합.** 
  - 극단적으로 RDBMS에서는 0.5초면 가능한 가벼운 쿼리가 Hive에선 50초 이상 걸릴 수 있다. 하지만 반대로, RDBMS에서는 50여 분 수행되던 무거운 쿼리가 Hive에서 단 50초만에 수행이 완료될 수 있다.
3. **데이터의 부분적인 수정 불가(Update/Delete) 불가**
  - HDFS의 특징. 이 특징을 물려받았으므로 Hive 또한 부분적인 수정 불가. 전체 데이터만 관리할 수 있다(partition)
  - 그래서 partition 단위를 어떻게 잘 설정하는 지가 중요하다.
  - 0.14부터는 UPDATE, DELETE, MERGE가 ORG Stored 형식에서 가능하지만 지양된다.
4. **대규모 병렬분산 처리가 불가능한 경우**
  - Hive는 대규모 병렬 분산 처리에 최적화되어있지만, 일부 요건에 따라 대규모 분산 처리가 어려울 수 있다.
  - ex) 대규모 join이나 grouping이 발생하면 분산된 노드끼리 대량의 데이터를 주고받으면서 network latency가 높아져 응답 속도가 크게 떨어질 수 있다.
  - 대용량 Hive QL을 수행하는 경우 데이터의 분산과 로컬리티를 고려하여 쿼리 플랜을 세워야 한다.
5. **트랜잭션 관리 기능이 없어 롤백 처리 불가**
  - 하나의 Hive Query는 여러 개의 job과 MapReduce 프로그램이 실행된다.
  - Fault Tolerance가 수행될 뿐, 롤백은 불가하다.
  - 0.14부터는 ACID가 부분적으로 지원되지만 제약사항이 많고, 권장되지 않는다.

> Inmemory, DAG 등의 기술을 이용한 기술들로 Hive가 대체되고 있지만 함께 사용되는 식으로 계속 사용되고 있다.

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




