# yum error(yumRepo Error)

- Redis를 설치하기 위하여 gcc를 설치하는 중에 에러가 발생하였다.
> `yum install -y gcc*`

![image](https://user-images.githubusercontent.com/43158502/128505274-4dbb582e-94d9-4a54-b4ba-ba2bed3a17c7.png)

> 해결 방법
- mirrorlist 생성.
```
$ echo "http://vault.centos.org/6.10/os/x86_64/" > /var/cache/yum/x86_64/6/base/mirrorlist.txt
$ echo "http://vault.centos.org/6.10/extras/x86_64/" > /var/cache/yum/x86_64/6/extras/mirrorlist.txt
$ echo "http://vault.centos.org/6.10/updates/x86_64/" > /var/cache/yum/x86_64/6/updates/mirrorlist.txt

$ echo "http://vault.centos.org/6.10/sclo/x86_64/rh" > /var/cache/yum/x86_64/6/centos-sclo-rh/mirrorlist.txt
$ echo "http://vault.centos.org/6.10/sclo/x86_64/sclo" > /var/cache/yum/x86_64/6/centos-sclo-sclo/mirrorlist.txt
```
