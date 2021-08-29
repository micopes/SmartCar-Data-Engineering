# Storm

- 역할
  - Kafka의 **Consumer로써 대규모 Stream data를 병렬** 처리 -> 영구 저장소 적재
  - 영구 저장소 적재 **이전에** 전처리/집계/분석 가능

## 구성 요소
- Spout : 외부로부터 데이터를 유입받아 가공 처리해서 튜플 생성 -> Bolt에 전송
- Bolt : 튜플을 받아 필터링/집계/join 등을 병렬로 실행
- Topology : Spout-Bolt의 데이터 흐름을 정의, 하나의 Spout와 다수의 Volt로 구성
- Nimbus : Topology를 받아 Supervisor에 배포
- Supervisor : 
  - 1개의 supervisor는 1개의 분산 노드
  - Topology를 실행할 Worker를 구동시키며 Topology를 Worker에 할당 및 관리
- Worker
  - Supervisor 상에서 실행 중인 Spout과 Bolt를 실행
- Executor : Worker 내에서 실행되는 Java Thread
- Tasker : Executor 내에서 Spout 및 Bolt 객체가 할당

> Spark와 유사한 역할
>
> Storm은 **Realtime**, but Spark **Micro-Batch**

## 예시
![image](https://user-images.githubusercontent.com/43158502/131253013-6c5b1b6e-f813-4cd6-8639-e67f2a776e35.png)

## 활용 방식
![image](https://user-images.githubusercontent.com/43158502/131253023-0d42dc0c-bc05-46e1-b289-28606ed173ac.png)

