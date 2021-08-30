# Apache Kafka
- **비동기**방식 처리(queue, topic 등을 활용하여 버퍼 역할)
- 대량의 Cluster로 buffer 역할, **ransaction** 등의 처리. Flume과 함께 사용할 시 **안정성**을 높일 수 있다.

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

## Kafka 사용의 좋은 예시

> Flume을 통해 바로 적재되면, 
> 
> 적재되는 곳에서 오류가 발생할 시, 대처할 수 없게 된다(Flume의 수집 영역과 적재 영역 모두에서.)

#### 해결책
- Flume > Kafka > 적재 

> 위의 과정을 거침으로써, 오류가 발생한 적재된 곳에서 대처할 시간을 벌어주게 되고, 수집된 데이터는 Kafka에서 임시 저장해서 추후에 처리할 수 있게 된다.

