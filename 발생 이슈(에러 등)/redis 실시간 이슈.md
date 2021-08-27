## [진행내용 13에서 발생](https://github.com/micopes/SmartCar-Data-Engineering/blob/main/%EC%A7%84%ED%96%89%20%EB%82%B4%EC%9A%A9/13_%ED%83%90%EC%83%89%20%EC%A3%BC%EC%A0%9C%20%EC%98%81%EC%97%AD.md)

- 실시간 로그 발생 시키고, 진행 중에 과속 데이터 발생 시 실시간으로 redis에 적재되도록 하였다.

> `redis-cli`
>
> `smembers 20210801`

를 수행하였는데, 과속 시 실시간으로 적재가 되지 않음. 시간이 흐른 후에 적재가 되는데 이 속도가 매우 늦다.

<br><hr>

- 실시간 과속 데이터 적재 파악 및 해결 필요
