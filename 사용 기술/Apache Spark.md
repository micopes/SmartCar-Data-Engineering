# Spark

- In-memory에서 데이터 처리. Hive를 사용하면 Disk, Network I/O 시 Latency 발생하는데 이런 Latency를 줄여줄 수 있다.

## 구조

- RDD
> Spark 프로그래밍의 기초 데이터 셋 모델

- Spark Driver/Executors
  - Driver : RDD 프로그램을 분산 노드에서 실행하기 위한 Task의 구성/할당/계획 수립
  - Executor : Task 실행, 관리, 분산 노드의 Storage, 메모리 참조

- Spark Cluster Manager
> 스파크 실행 환경을 구성하는 Cluster Manager

- Spark SQL
> SQL 방식으로 Spark RDD 프로그래밍 지원

- Spark Streaming
> streaming data를 micro-batch로 나누어 실시간 처리

- Spark MLib
> Spark에서 머신러닝 프로그래밍 지원

- Spark GraphX
> 다양한 유형의 Network(SNS, Hyperlink 등) 구조 분석을 지원 

