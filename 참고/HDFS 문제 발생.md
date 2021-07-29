### 기능 및 설치에 문제가 발생한다면
> 파일/블록 깨짐, Safe 모드 전환 여부 점검 필요

#### Check 사항
- HDFS 파일 시스템 검사
> `$ hdfs fsck /`
- HDFS에 Safe 모드 발생 후 빠져나오지 못하는 경우
> `$ hdfs dfsadmin -safemode leave`
- HDFS에 CORRUPT BLOCKS/FILES 등이 발생하여 복구가 불가능한 경우
  - 손상된 파일 강제 삭제
  > `$ hdfs fsck / -delete` # 손상된 파일 강제 삭제
  - 손상된 파일을 /lost + found 디렉토리로 이동
  > `$ hdfs fsck / -move` # 진행 중인 작업이 있어서 안되는 것일 수 있으므로 안전하게 옮겨만 둔다.
