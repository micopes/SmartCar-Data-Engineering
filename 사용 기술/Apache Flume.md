# Apache Flume
[공식 문서 : https://flume.apache.org/FlumeUserGuide.html]

### Source
> file, DB, API, Socket과 같은 것들을 발생 주기, format 등을 고려하여 이벤트를 수집
### Channel
> *Source*가 이벤트를 수신하면  채널에 저장. 싱크가 이벤트를 다른 목적지로 전달할 때까지 파일이나 메모리 등에 저장.
### Sink
> *Channel*에서 이벤트를 제거하고 HDFS와 같은 외부 저장소나, 다른 Flume Agent로 소스를 전달
### Intercept
> *Source*에 들어온 이벤트를 수정하는 등의 작업 시 사용
### Agent
> 위의 과정을 통칭


### 예시

![image](https://user-images.githubusercontent.com/43158502/127336307-cdf06352-1d04-4321-b94b-54f1b7f659a8.png)



