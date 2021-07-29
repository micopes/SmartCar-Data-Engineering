## Cloudera Manager를 종료 및 시작 시에 발생한 문제
> FSImage 깨짐

![image](https://user-images.githubusercontent.com/43158502/127462233-8c7d63fa-8b28-4f09-b80e-c6fac737768a.png)

+) 추가 로그 메시지

![image](https://user-images.githubusercontent.com/43158502/127462266-b5eeab73-7da7-4b5f-a389-fd831b8f5bda.png)

### 문제
- FSImage가 깨진 것으로 보인다.

### 예상되는 원인
- 서버를 종료 및 시작하는 것을 숙지하기 전에 비정상적으로 종료 및 시작과정을 거쳐서 이 과정에서 문제가 발생한 것으로 보인다.

### 해결 방법
1. Namenode 포맷
> CM홈 > hdfs > 구성 에서 상단의 콤보박스를 선택해 네임노드 포맷
2. 처음부터 다시 설정
> 무식한 방법이지만 가장 확실하다. 아직 과정을 많이 진행하지 않았으므로 복습 겸 다시 환경을 설정해보는 것도 나쁘지 않을 듯하다.
