# Apache Kafka
- **비동기**방식 처리(queue, topic 등을 활용하여 버퍼 역할)
- 대량의 Cluster로 buffer 역할, transaction 등의 처리. Flume과 함께 사용할 시 **안정성**을 높일 수 있다.

### Broker
> 서비스 instance
### Topic
> *Broker*에서 데이터의 발행/소비 처리를 위한 **중간 저장소**
### Provider(Producer)
> *Broker*의 *Topic*에서 데이터 **전송**
### Consumer
> *Broker*의 *Topic*에서 데이터 **수신**

> Provider와 Consumer는 분리되어 있다. 이로 인해 높은 확장성을 띠게 할 수 있다.


### 예시

![image](https://user-images.githubusercontent.com/43158502/127336212-d9101c1f-2dbb-4e2b-a08c-2571e8bf63b1.png)



