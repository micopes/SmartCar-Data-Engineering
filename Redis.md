# Redis
- 분산 Cache이면서 NoSQL이면서 대규모 데이터 관리 
- **In-memory Data Grid Software**
- 실시간성 data들 중 일부만 HBase에 저장되기 전에 Redis에 저장. 필요 시 사용(이 프로젝트에서는 과속데이터 적재 위해 사용)

### 구성 요소
- Master : 분산 노드간의 데이터 복제가 Slave 서버 관리를 위한 Master 서버
- Slave : 주로 읽기 요청 처리. Master 서버는 쓰기 요청 처리
- Sentinel : Master 서버에 문제가 생길 시 새로운 Master 서버를 선출하는 기능
- Replication : Master 서버에 쓰인 내용을 Slave 서버로 복제하여 동기화 처리
- AOF/Snapshot : 데이터를 영구적으로 저장하는 기능. 명령어를 지원하는 AOF와 스냅샷 이미지 파일을 지원

### 구조 예시
![image](https://user-images.githubusercontent.com/43158502/131252517-ffdf51ce-8b16-4e76-a511-05d35d886c34.png)
