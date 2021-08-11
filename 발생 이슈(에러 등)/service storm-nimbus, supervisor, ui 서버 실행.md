# Storm 서버 실행(storm-nimbus, storm-supervisor, storm-ui)

server02
```
$ service storm-nimbus status
$ service storm-supervisor status
$ service storm-ui status
```
세 가지 명령을 통해 상태를 확인하자, 실행이 되고 있지 않은 것을 발견하고

```
$ service storm-nimbus start
$ service storm-supervisor start
$ service storm-ui start
```
세 명령을 실행하여 서버를 실행시키고

상태를 확인하는 명령을 다시 실행하였다.

> NOT running이라고 출력이 되는 것을 확인하고 해결책을 찾아보았다.

> **사실은 서버를 실행하는데 일정 시간이 걸린다는 것을 알았다. 이런 사실을 확인하고 `service ... status`로 상태를 확인하자 할당된 포트와 함께 실행 중인 것을 확인할 수 있었다.**

![image](https://user-images.githubusercontent.com/43158502/129020606-f89b9213-ed6b-486d-9fa9-f74a71b57a0d.png)

