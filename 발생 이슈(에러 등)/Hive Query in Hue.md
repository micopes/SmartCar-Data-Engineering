## 문제
- Hue에서 Hive Query 실행 시 다음과 같은 에러 발생

![image](https://user-images.githubusercontent.com/43158502/132225996-bb38c0c8-0cb1-494c-81f4-f30d87e9c17c.png)

## 해결 방법
1. yarn의 서버인 server01에서
```
hdfs dfs -chmod 755 /user/yarn
hdfs dfs -chmod 755 /user/yarn/mapreduce
```

2. 
> **CM > YARN (MR2 Included) > Action(작업) > Install YARN MapReduce frame jar**

## 결과(해결 완료)

![image](https://user-images.githubusercontent.com/43158502/132231773-cd6b8eda-9bf3-456c-8877-9dc844cae2fc.png)


[출처](https://community.cloudera.com/t5/Support-Questions/java-io-FileNotFoundException-File-does-not-exist-hdfs-ABC/td-p/286737)


