# Apache Impala

- 메모리 사용률이 높다.
- 많은 자원을 사용한다.
- 빠르다(실시간, **대화형(Interactive)** 가능)
- Hive에 비해 Fault Tolerance 측면에서 약하다.
- 업무 시간에 적합하다

## cf) Hive
- Disk 사용률이 높다.
- 안정성이 높다.
- Fault Tolerance가 보장된다.
- 업무 마감 후 적합.

## 임팔라 구성 요소

#### Impalad
> Hadoop datanode에 설치되어 임팔라 실행쿼리에 대한 계획, 스케줄링, 엔진을 관리하는 코어 영역

#### Query Planner
> 임팔라 쿼리 실행 계획 수립

#### Query Coordinator
> 임팔라 job request 및 스케줄링 관리

#### Query Exec Engine
> 임팔라 쿼리를 최적화하여 실행, 쿼리 결과 제공

#### Statestored
> 분산 환경에 설치되어 있는 Impalad 설정 정보 및 서비스를 관리

#### Catalogd
> 작업 이력 관리, 필요 시 이를 제공

![image](https://user-images.githubusercontent.com/43158502/135643237-9672fc5f-68ac-4568-a88b-6b0365daaafe.png)

