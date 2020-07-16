출처-[https://nesoy.github.io/articles/2017-02/REST](https://nesoy.github.io/articles/2017-02/REST)

## **RESTful (Representational state transfer)**

![메인이미지](https://gmlwjd9405.github.io/images/network/restful.png)


### **RESTful 과 REST의 차이점**

Representational state transfer (REST)은 소프트웨어 아키텍처의 한 스타일이다. 로이 필딩의 논문에서 기술한 바와 같이,<br/>
REST는 웹의 기존 기술과 프로토콜을 기본적으로 이용하는 「아키텍쳐 스타일」이다.

RESTful은 일반적으로 그러한 아키텍처를 구현하는 웹 서비스를 지칭하는 데 사용된다.

<br/>

***
<br/>

### **특징**

1. Uniform (유니폼 인터페이스)
    - Uniform Interface는 URI로 지정한 리소스에 대한 조작을 통일되고 한정적인 인터페이스로 수행하는 아키텍처 스타일

2. Stateless (무상태성)
    - 상태가 있다 없다는 의미는 사용자나 클라이언트의 컨택스트를 서버쪽에 유지 하지 않는다는 의미한다.
    - 세션이나 쿠키등을 별도로 관리하지 않기 때문에 API서버는 요청만을 들어오는 메시지로만 처리하기 때문에 구현이 단순하다.

3. Cacheable (캐시 처리 가능)
    - REST의 가장 큰 특징 중 하나는 HTTP라는 기존 웹표준을 그대로 사용한다.
    - HTTP가 가진 캐싱 기능이 적용 가능하다. HTTP 프로토콜 표준에서 사용하는 Last-Modified태그나 E-Tag를 이용하면 캐싱 구현이 가능하다.

4. Self-descriptiveness (자체 표현 구조)
    - REST의 또 다른 큰 특징 중 하나는 REST API 메시지만 보고도 이를 쉽게 이해 할 수 있는 자체 표현 구조로 되어 있다는 것

5. Client - Server Architecture (클라이언트 - 서버 구조)
    - REST 서버는 API를 제공하고, 제공된 API를 이용해서 비즈니스 로직 처리 및 저장을 책임진다.
    - 클라이언트의 경우 사용자 인증이나 컨택스트(세션,로그인 정보)등을 직접 관리하고 책임진다.
    - 서로간의 의존성이 줄어들게 된다.

6. 계층형 구조
    - 클라이언트 입장에서는 REST ApI 서버만 호출한다.
    - REST 서버는 다중 계층으로 구성될 수 있다. 예를 들어 보안, 로드 밸런싱, 암호화, 사용자 인증등등 추가하여 구조상의 유연성을 줄 수 있다.

<br/>

***
<br/>

### **구성**

- 자원 - URI
- 행위 - HTTP Methods (GET, PUT, POST, DELETE등등)
- 표현

    ```
    'URI'와 'URL'이라는 용어는 서로 교환해서 사용하는 경우가 많지만 정확히 같은 용어는 아니다. 여기 차이점이 있다.

    1. URI는 특정 리소스의 식별자다. 페이지, 책, 문서 같은 것.
    2. URL은 HTTP, FTP 등과 같이 URL에 액세스하는 방법을 알려주는 특수 유형의 식별자 입니다.
    3. 프로토콜(https, ftp 등)이 도메인에 대해 존재하거나 암시되어 있는 경우, URL이라고 해야 하며, URI라고도 한다.(그럼 왜 나누는거지;;)
    ```
    ![](https://danielmiessler.com/images/url-uri-miessler-2019-white-e1576768407702.png.webp)
    ![](https://res.cloudinary.com/practicaldev/image/fetch/s--lrbx3qNQ--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://thepracticaldev.s3.amazonaws.com/i/j4bka41nypm4do1f3e5b.JPG)

<br/>

***
<br/>

### **가이드**

`URI는 자원을 표현해야 한다.`<br/>
`자원에 대한 행위는 GET, PUT, POST, DELETE 등으로 표현한다.`

1. REST API 중심 규칙
    ```
    GET /course/insert/inform -- X
    GET /course/inform -- O
    ```
    - URI는 정보의 자원을 표현해야 한다.
    - HTTP Method (GET, PUT, POST, DELETE등등)의 행위가 URI 표현으로 들어가서는 안된다.
    <br/>
    ```
    DELETE /members/1
    ```
    - 자원에 대한 행위는 HTTP Method (GET, PUT, POST, DELETE등등)로 표현
    - HTTP Method(GET, PUT, POST, DELETE등등)로 행위로 CRUD를 할 수 있다.

2. URI 설계 시 주의할 점
    ```
    http://test.com/Test -- 서로 다른 Resource : Test
    http://test.com/test -- 서로 다른 Resource : test
    ```
    - 소문자를 되도록이면 사용하자
        - 예를 들어 test.com의 자원(Resource) Test와 test가 있지만 **대소문자에 따라 구분**하기 때문에 다른 자원(Resource)으로 인식하게 된다.
        - RFC 3986(URI 문법 형식)은 URI 스키마와 호스트를 제외하고는 대소문자를 구별하도록 규정하고 있다.

    - 하이픈(-)은 URI 가독성을 높이는데 사용하자
        - 경로(Path)에 띄어쓰기가 들어가는 경우 "%20"이 들어가 가독성이 매우 떨어진다.
        - 하이픈(-)을 사용하여 띄어쓰기를 대체하고 가독성을 높일 수 있다.
    <br/>
    ```
    http://test.com/test.jpg -- X
    http://test.com/test -- O
    GET /test HTTP/1.1
    Host: test.com
    Accept: image/jpg
    ```
    - 확장자를 사용하지 말자
        - REST API에서는 확장자를 사용하지 않으면서 자원(Resource)을 다루는 데 더 유연해 진다.
        - 확장자 대신에 **Accept Header**를 사용하여 문제를 해결한다.

        ##### 참고이미지(HTTP 프로토콜 통신)
        ![](https://mdn.mozillademos.org/files/13827/HTTPMsgStructure2.png)
        ![](https://mdn.mozillademos.org/files/13821/HTTP_Request_Headers2.png)

3. 자원을 표현하는 Collection과 Document

    ```
    http://test.com/citys/seoul/gangnam
    ```
    - 도큐먼트(Document)는 단순한 문서와 같은 존재
    - 컬렉션(Collection) 문서들의 집합, 객체들의 집합같은 존재(그룹같은..?)
    - **위에 예제 중 citys가 컬렉션에 해당되며 복수로 표현을 하고 있는 점이 중요하다.**

4. HTTP 응답코드

||상태코드|의미|
|:--:|:-----:|:--:|
|성공|200|정상수행|
||201|자원생성 요청 > 성공적으로 수행|
|클라이언트 에러|400|클라 요청이 부적절할 경우|
||401|클라가 권한없는 자원을 요청했을 때|
||403|보호되는 자원을 요청했을때|
||405|클라가 요청한 자원에 사용불가능한 메소드를 사용했을 때|
|기타|301|클라가 요청한 자원에 대한 URI가 변경되었을 때|
||500|서버에 문제가 있을 때|
||404|Not Found|

[HTTP 응답코드 - MDN](https://developer.mozilla.org/ko/docs/Web/HTTP/Status")