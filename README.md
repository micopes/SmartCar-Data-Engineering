# 스마트카 로그 데이터 이용 데이터 엔지니어링

## 주요 목표
- 차량의 다양한 장치로부터 발생하는 로그 파일을 수집하여 기능별 상태 점검(**배치**)
- 운전자의 운행 정보가 담긴 로그를 **실시간**으로 수집하여 주행 패턴 분석

### 가상 머신 설정
- Oracle Virtual Box : 2대 (hostname : server01, server02)
- OS : CentOS 6
- RAM : (server01 : 4GB, server02 : 4GB)

### Cloudera Manager
- Hadoop 모니터링 서비스
- CDH 설치 (Cloudera에서 제공하는 Hadoop Ecosystem)
- 설치 및 환경 구성(Flume, Kafka, Spark 등)

### 최종 구성
![image](https://user-images.githubusercontent.com/43158502/137731771-5fbe03b3-6305-4c36-b19f-09e11d51efca.png)


## 수집
- 데이터 생성을 위한 로그 시뮬레이터 가동

![image](https://user-images.githubusercontent.com/43158502/137732308-e15624da-8f62-4f04-a072-74f5bac5ca19.png)

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
> 
> 이 프로젝트에서는 가속 데이터를 Redis에 담는다. 배치성으로 처리하기 전에 실시간으로 가속 탐지된 데이터를 처리하기 위해 사용

## 적재
- 발생되는 데이터를 위의 수집과정을 거쳐 저장(적재)

- HDFS
> 파일을 블록 단위로 나누어서 각 클러스터에 분산 저장

- 

## 처리/탐색

## 분석/응용



### [발생 이슈](https://github.com/micopes/SmartCar-Data-Engineering/issues)

[참고] [실무로 배우는 빅데이터 기술 2nd](https://github.com/wikibook/bigdata2nd)


