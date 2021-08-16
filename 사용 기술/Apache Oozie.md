# Oozie

- `Data Lake(External)` -> `Data Warehouse(Managed)` -> `Data Mart`
> 위의 과정에서 발생하는 **job(task)들의 수많은 의존 관계, 스케줄링 등의 작업 흐름 정의 및 제어**

- Oozie Workflow
> 주요 Action에 대한 작업 규칙과 flow 정의

- Oozie Client
> 작업된 정의를 서버에 전송 및 관리

- Oozie Server
> Workflow 정보가 job으로 등록되어 job의 실행/중지/모니터링 관리

- Control node
> 작업의 흐름 제어 Start/End/Decision. Workflow의 구성요소.

- Action node
> Hive, Pig, Map-Reduce 등의 액션으로 실제 수행 task 정의

- Coordinator
> job 실행 위한 스케줄 정책 관리
  
  
## 실행 계획

- 단계 별 workflow 기능 제공
- coordinator 기능을 이용하여 workflow를 주기적으로 실행 및 관리
