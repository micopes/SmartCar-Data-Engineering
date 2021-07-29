# Flume 수집

1) 
  - SmartCar Agent 생성
  - SmartCar Agent에 intercept 추가..
2) 
  - DriverCarInfo Agent.
  ...
  
### Cloudera Manager에서 Home > Flume > 구성 .
- 실시간
- 배치
> 로그 파일 받도록 코드 구성

# Kafka 수집
- Producer Console(Kafka Sink)
- Kafka Broker
- Consumer Console 1, 2

순서
> Producer Console(Kafka Sink) -> Kafka Broker(SmartCar-Topic) -> Consumer Console 1, 2

### 위의 과정 실습
1. Kafka Topic 생성
> `# kafka-topic --create --zookeeper server02.hadoop.com:2181 --replication-factor 1 --partitions 1 --topic SmartCar-Topic`
2. Kafka producer 사용
> `# kafka-console-producer --broker-list server02.hadoop.com:9092 -topic SmartCar-Topic`
3. Kafka consumer 사용
> `# kafka-console-consumer --bootstrap-server server02.hadoop.com:9092 --topic SmartCar-Topic --partition 0 --from-beginning`

