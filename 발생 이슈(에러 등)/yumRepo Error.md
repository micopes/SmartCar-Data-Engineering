# yum error(yumRepo Error)

- Redis를 설치하기 위하여 gcc를 설치하는 중에 에러가 발생하였다.
> `yum install -y gcc*`

![image](https://user-images.githubusercontent.com/43158502/128505274-4dbb582e-94d9-4a54-b4ba-ba2bed3a17c7.png)

> 해결 방법
- mirrorlist 생성.
  - mirrorlist란 ? 
    - 공식 repo 서버와 동일하게 만든 사이트
    - 공식 사이트에서 Mirrorlist를 클릭하면 전세계의 미러사이트가 출력된다.
    - 전세계의 수많은 미러사이트 중에 가장 빠른 사이트를 찾아서 저장소 url을 변환해준다(fastestMirror) 이 미러사이트는 계속 실행할 때마다 바뀐다.
```
$ echo "http://vault.centos.org/6.10/os/x86_64/" > /var/cache/yum/x86_64/6/base/mirrorlist.txt
$ echo "http://vault.centos.org/6.10/extras/x86_64/" > /var/cache/yum/x86_64/6/extras/mirrorlist.txt
$ echo "http://vault.centos.org/6.10/updates/x86_64/" > /var/cache/yum/x86_64/6/updates/mirrorlist.txt
$ echo "http://vault.centos.org/6.10/sclo/x86_64/rh" > /var/cache/yum/x86_64/6/centos-sclo-rh/mirrorlist.txt
$ echo "http://vault.centos.org/6.10/sclo/x86_64/sclo" > /var/cache/yum/x86_64/6/centos-sclo-sclo/mirrorlist.txt
```
