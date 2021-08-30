# Hadoop
- 대용량 데이터 **분산 저장**
- 분산 저장된 데이터 **가공/분석 처리**

- 여러 Server에 큰 데이터를 분산 저장
- 분산 저장된 data 가공 및 처리

## 주요 구성 요소

#### DataNode
> 대용량 data를 저장하는 Node(Server)

#### NameNode
> DataNode의 meta 정보

#### EditsLog
> 파일들의 변경 이력 등이 저장되는 로그 파일

#### FsImage 
> NameNode의 meta 정보를 snapshot 이미지로 만들어 생성한 파일

### ver 1.x

#### Secondary NameNode
> NameNode의 EditsLog, FsImage 파일을 주기적으로 유지/관리해주는 체크포인팅 노드

#### MapReduce
> 분산 저장된 data들을 분산 처리
- Map : 어떻게 효율적으로 일을 나눠서 실행
- Reduce : 여러 컴퓨터가 나눠서 실행한 결과를 하나로 모음

#### JobTracker
> 여러 MapReduce, Job들을 관리

#### TaskTracker
> MapReduce의 작업들을 실행

### ver 2.x

#### Active/Standby NameNode

#### MapReduce v2/YARN

#### ResourceManager

#### NodeManager

#### Container

#### ApplicationMaster

#### JournalNode
