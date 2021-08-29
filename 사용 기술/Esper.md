# Esper
- 앞서 Storm에서는 과속을 처리한다고 했는데 **Esper는 이 과속을 판단하는 Query를 날림**

## 구성 요소
- Event : 실시간 Stream으로 발생하는 데이터들의 특정 흐름 및 패턴 정의
- EPL : **유사 SQL을 기반으로하는 Event data 처리 Script 언어**
- Input Adapter : 소스로부터 전송되는 데이터를 처리하기 위한 어댑터 제공
- Output Adapter : 타겟으로 전송되는 데이터를 처리하기 위한 어댑터 제공
- Window : 실시간 스트림 데이터로부터 특정 시간/개수를 설정한 Event를 메모리 상에 등록한 후 EPL을 통해 결과 추출

## 활용 방안
- Storm 의 Bolt 내에 Input Adapter > Esper Engine > Output Adapter를 통해 결과 
