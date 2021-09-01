# HBase

#### HTable 
> column 기반 데이터 구조를 정의한 테이블
#### HMaster 
> HRegion Server를 관리, HRegion이 속한 HRegionServer의 **meta** 정보를 관리
#### HRegion
> HTable의 크기에 따라 자동으로 수평 분할 발생
> 
> 분할된 Block을 HRegion 단위로 지정

#### HRegionServer
> 분산 노드별 HRegionServer가 구성되며, 하나의 HRegionServer에는 다수의 HRegion이 생성되어 HRegion을 관리

#### Store
> 하나의 Store에는 column family가 저장 및 관리되며, MemStore와 HFile로 구성됨
- MemStore: Store 내의 데이터를 **메모리**에 저장 및 관리하는 데이터 캐시 영역
- HFile: Store 내의 데이터를 **디스크**에 저장 및 관리하는 영구 저장 영역

