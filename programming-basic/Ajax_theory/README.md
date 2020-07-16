## **Ajax Theory**

`Client <-----> Front-end Sever <----> Back-end Server <---> DB`

1. browser와 Front-end Server 간 통신은 http(Ajax 비동기 or 동기)

2. Front-end Server와 Back-end Server 간 통신은 http(동기)

3. Back-end Server와 DB 간 통신은 tcp/ip

- WEB 서버와 WAS 분리 포인트
    - DB 접근은 Rest API 서버 만 접근 가능해야함(보안 이슈)
    - Rest API는 WEB Server에서 만 접근 가능해야함(보안 이슈)