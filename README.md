# 스마트카 로그 데이터 이용 데이터 엔지니어링

## 주요 목표
- **운전자의 정보**가 담긴 로그 데이터 **배치** 수집 및 활용
- 차량의 다양한 장치로부터 발생하는 로그 데이터(**운행 정보**)를 수집하여 기능별 상태 **실시간** 점검

### 가상 머신 설정
- Oracle Virtual Box : 2대 (hostname : server01, server02)
- OS : CentOS 6
- RAM : (server01 : 4GB, server02 : 4GB)

### Cloudera Manager
- Hadoop 모니터링 서비스
- CDH 설치 (Cloudera에서 제공하는 Hadoop Ecosystem)
- 설치 및 환경 구성(Flume, Kafka, Spark 등)

#### [사용 기술](https://github.com/micopes/SmartCar-Data-Engineering/tree/main/%EC%82%AC%EC%9A%A9%20%EA%B8%B0%EC%88%A0)
#### [진행 과정](https://github.com/micopes/SmartCar-Data-Engineering/tree/main/%EC%A7%84%ED%96%89%20%EB%82%B4%EC%9A%A9)
#### [발생 이슈](https://github.com/micopes/SmartCar-Data-Engineering/issues)

### 최종 구성
![전체 구성](https://user-images.githubusercontent.com/43158502/138586361-279e4523-95f1-4c01-b62c-5ab12d6c8135.jpg)


## 수집
- 데이터 생성을 위한 로그 시뮬레이터 가동

- Flume
> Source -> Channel -> Sink의 구조를 가지며, 데이터를 수집하기 위한 기능을 담당

- Kafka 
> 대규모 메시지성 데이터 중계. Producer(데이터를 전송)와 Consumer(데이터를 소비)로 나뉘며 이를 중계하는 Broker가 중간에 존재

- Storm
> 데이터를 인메모리 상에서 병렬 처리하기 위한 소프트웨어
> 
> Kafka로부터 받은 데이터를 각각 HBase, Redis로 나누어서 전달

- Esper 
> 실시간 스트리밍 데이터의 복잡한 이벤트 처리가 필요할 때 사용하는 룰 엔진

## 적재

#### 배치성 수집 - 적재

![수집-적재(배치)](https://user-images.githubusercontent.com/43158502/138586366-c8dc5c7e-0ac4-4991-900a-bfb28b125261.jpg)

<hr>

#### 실시간 수집 - 적재

![수집-적재(실시간)](https://user-images.githubusercontent.com/43158502/138586368-52281d41-2d49-4a59-baf9-54b0264c10ef.jpg)

-  실시간 수집의 경우 **Flume**에서 수집이후 바로 적재를 진행하게 되면, `Fault Tolerance`를 보장하지 못한다. 적재 시 HBase와 같은 곳에 오류가 발생하면, 실시간으로 수집되고 있는 데이터들이 손실될 수 있다.    
  - 이런 점을 해결하기 위해서 중간에 **Kafka**의 높은 처리량, 신뢰성, 즉각적인 피드백을 통해 수집되고 있는 데이터들이 손실되지 않고, 즉각적으로 장애에 대응할 수 있도록 구성하였다.



- HDFS
> 파일을 블록 단위로 나누어서 각 클러스터에 분산 저장

- Zookeeper : 분산 코디네이터
> 분산 환경에서 작동되는 작업들을 감시, 감독(Supervisor)

- HBase
  - Hadoop 기반 Colume 지향 NoSQL
  - Schema 변경이 자유롭다.
  - Region이라는 분산 서버로 샤딩(같은 테이블 스키마를 가진 데이터를 다수의 데이터베이스에 분산하여 저장하는 방법)과 복제 지원 -> 성능/안정성 향상

- Redis
  - 분산 Cache
  - Key-Value 구조
  - In-memory Data grid Software
  - 실시간성 데이터 중 일부만 HBase에 저장하기도 전에 Redis에 저장할 필요 있어서 사용(가속 데이터)

## 탐색

- Hive
  - 기존 방식) 적재된 데이터를 탐색/분석하기 위해 Map-Reduce를 주로 사용(복잡도 커짐, Java 이용 필요)
  - Hive를 이용(SQL on Hadoop) Map-Reduce로 변환 및 실행 가능
    - Query Engine : 사용자가 입력한 Hive Query를 분석하여 실행 계획을 수립, Hive Query를 Map-Reduce Code로 변환 및 실행
  - Interactive(대화형)한 방식에는 적합하지 않다. 추후 Impala 사용

- Spark
> In-memory 방식을 통해 Map-Reduce보다 데이터를 더욱 효율적으로 처리(적은 데이터의 경우 Spark나 Impala가 Hive보다 유용)
- Oozie 
> Workflow 구성 가능
- Hue 
> *Web UI*를 이용하여 HDFS 및 Query를 간편하게 이용 가능

##### 기존의 Hive Table 이용 추가 주제영역 테이블 생성
- 스마트카 상태 모니터링 정보(`managed_smartcar_status_info`)
  - `smartcar_master_over18`, `smartcar_status_info` 이용
- 스마트카 운전자 운행기록 정보(`managed_smartcar_drive_info`)
  - `smartcar_master_over18`, `smartcar_drive_info_2` 이용
- 이상 운전 패턴 스마트카 정보(`managed_smartcar_symptom_info`)
  - `managed_smartcar_drive_info` 이용
- 긴급 점검이 필요한 스마트카 정보(`managed_smartcar_emergency_check_info`)
  - `managed_smartcar_status_info` 이용
- 운전자의 차량 용품 구매 이력정보(`managed_smartcar_item_buylist_info`)
  - `smartcar_master_over18`, `smartcar_item_buylist` 이용

##### 추가 주제 영역 테이블 확인

![image](https://user-images.githubusercontent.com/43158502/137740820-cc56337f-d41b-48da-a600-1262e8e8ce9e.png)

- 제대로 생성된 것을 확인할 수 있다.

<hr>


## 분석
- Impala
> Hive 쿼리보다 빠른 실시간 분석(대화형 쿼리)을 위한 쿼리엔진. 대용량 배치처리보다는 ad-hoc 쿼리를 통한 빠른 질의결과를 요구
- Zeppelin
> R과 HDFS를 서로 연결하여 원활한 데이터 분석 작업을 진행하기위한 툴. Spark를 기반으로 한다.
- Sqoop
> HDFS에 저장된 분석 결과를 외부에 있는 DB(Oracle, MySQL, PostgreSQL 등)에 전달


## 추가 작업
- **Python**을 **Hive Data Warehouse**에 **연결**하여 분석 및 응용
- **SparkML**를 이용하여 분석 및 응용

> [참고 자료] [실무로 배우는 빅데이터 기술](https://github.com/wikibook/bigdata2nd)


