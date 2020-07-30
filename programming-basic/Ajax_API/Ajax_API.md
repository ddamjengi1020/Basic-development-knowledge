Ajax 출처 - [https://developer.mozilla.org/en-US/docs/Web/Guide/AJAX](https://developer.mozilla.org/en-US/docs/Web/Guide/AJAX)  
API 출처 - [https://www.altexsoft.com/blog/engineering/what-is-api-definition-types-specifications-documentation/](https://www.altexsoft.com/blog/engineering/what-is-api-definition-types-specifications-documentation/)


## **Ajax & API**

그래서 Ajax가 뭐고 API는 뭐야?? 라는걸 배우면서도, 쓰면서도 많이 생각하게 된다.<br/>
그래서 이곳저곳에서 찾아서 기록해본다😎 언젠간 완전히 이해하는 날이 오겠지..

<br/>

***
<br/>

### **Asynchronous Javascript And XML(Ajax)란 ?**

비동기 JavaScript와 XML은 기술 자체는 아니지만 2005년 제시 제임스 개럿이 만든 용어로서 HTML 또는 XHTML, CSS, 자바스크립트, DOM, XML, XSLT, 가장 중요한 **XMLHtpRequest** 객체를 포함한 다수의 기존 기술을 함께 사용하는 "새로운" 접근법을 설명한다.<br/>
이러한 기술이 Ajax 모델에 결합되면 **웹 애플리케이션은 전체 브라우저 페이지를 재로드하지 않고도** 사용자 인터페이스에 대한 빠른 업데이트를 할 수 있다. 이것은 애플리케이션을 더 빠르고 사용자 행동에 더 잘 반응하게 한다.

Ajax의 X는 XML을 의미하지만, JSON은 가볍고 자바스크립트의 일부라는 장점 때문에 오늘날 XML보다 더 많이 사용되고 있다. JSON과 XML 모두 Ajax 모델의 포장 정보에 사용된다.

> AJAX는 백그라운드에서 웹 서버와 데이터를 교환하여 웹 페이지를 비동기식으로 업데이트할 수 있도록 하고<br/>
전체 페이지를 다시 로드하지 않고 웹 페이지의 일부를 업데이트할 수 있게하는 기술이다.

##### 👉`'비동기식으로 통신해서 빠르게 업데이트한다'가 핵심`

<br/>
<br/>

### **그럼 XMLHtpRequest는 뭘까**

HTTP 요청을 보내려면 XMLHtpRequest 개체를 생성하고 URL을 연 다음 요청을 보내라. 트랜잭션이 완료된 후 오브젝트는 응답 본문 및 결과의 HTTP 상태와 같은 유용한 정보를 포함할 것이다.

```javascript
function reqListener () {
  console.log(this.responseText);
}

var oReq = new XMLHttpRequest();
oReq.addEventListener("load", reqListener);
oReq.open("GET", "http://www.example.org/example.txt");
oReq.send();
```

XMLHttpRequest를 통해 만들어진 요청은 **비동기식 또는 동기식으로 데이터를 가져올 수** 있다. 요청 유형은 [XMLHtpRequest.open()](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/open) 방법에 설정된 선택적 비동기 인수(세 번째 인수)에 의해 지정된다. 이 인수가 참이거나 지정되지 않은 경우 XMLHtpRequest는 비동기적으로 처리되며 그렇지 않은 경우 프로세스가 동기적으로 처리된다.

#### 🤔 그럼 Ajax를 구현하기 위해선 꼭 `XMLHttpRequest` 객체를 사용해야할까?? > 자바스크립트에선 [fetch api](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)를 통해서 비동기 통신을 구현할 수 있다!!

<br/>
<br/>

### **Ajax의 작업흐름**

![](https://www.w3schools.com/whatis/img_ajax.gif)

1. 웹 페이지에서 이벤트 발생(페이지 로드, 단추 클릭)
2. XMLHttpRequest 개체가 JavaScript에 의해 생성됨
3. XMLHttpRequest 개체가 웹 서버로 요청을 전송함
4. 서버가 요청을 처리함
5. 서버가 웹 페이지로 응답을 전송함
6. JavaScript에서 응답을 읽음
7. JavaScript에서 페이지 업데이트와 같은 적절한 작업이 수행됨

<br/>

***
<br/>

### **웹 통신 기본 흐름**

`Client <-----> Front-end Sever <----> Back-end Server <---> DB`

1. browser와 Front-end Server 간 통신은 http(Ajax 비동기 or 동기)

2. Front-end Server와 Back-end Server 간 통신은 http(동기)

3. Back-end Server와 DB 간 통신은 tcp/ip

- WEB 서버와 WAS 분리 포인트
    - DB 접근은 Rest API 서버 만 접근 가능해야함(보안 이슈)
    - Rest API는 WEB Server에서 만 접근 가능해야함(보안 이슈)

<br/>

***
<br/>

### **API 란..??**

API는 한 소프트웨어 제품과 다른 소프트웨어 제품 간의 데이터 전송을 가능하게 하는 프로그래밍 코드 세트다.
```
View없이 프론트단과 서버단이 통신하는 것이고,
api 주소는 사용자가 주소입력창으로 접근할 수 없도록 해야 함.
(feat. 니꼬)
```
#####   👆 위 설명이 모든걸 이해하게 만든다... 묘해..💕..

<br/>
<br/>

### **API 들의 타입들**

![](https://content.altexsoft.com/media/2019/06/https-lh6-googleusercontent-com-gwdr_ml7gwkq7sex.png)


- **Private APIs**

    이러한 응용 소프트웨어 인터페이스는 조직 내의 솔루션과 서비스를 개선하기 위해 설계된다. 사내 개발자나 계약자는 이 API를 사용하여 회사의 IT 시스템이나 애플리케이션을 통합하고, 기존 시스템을 활용하여 새로운 시스템이나 고객 대면 앱을 구축할 수 있다. 앱을 공개적으로 사용할 수 있더라도 인터페이스 자체는 API 게시자와 직접 작업하는 경우에만 사용할 수 있다. 민간 전략은 기업이 API 사용을 완전히 통제할 수 있도록 한다.

- **Partner APIs**

    파트너 API는 공개적으로 홍보하지만 게시자와 협약을 맺은 비즈니스 파트너와 공유한다. 파트너 API의 일반적인 사용 사례는 양 당사자 간의 소프트웨어 통합이다. 파트너에게 추가 수익 흐름으로부터 데이터 액세스 또는 기능 혜택을 부여한 회사. 동시에 노출된 디지털 자산이 어떻게 사용되는지 모니터링하고, API를 사용하는 타사 솔루션이 적절한 사용자 경험을 제공하는지 확인하고, 앱에서 기업 정체성을 유지할 수 있다.

- **Public APIs**

    개발자 대면 또는 외부로도 알려진 이러한 API는 모든 타사 개발자가 사용할 수 있다. 공공 API 프로그램은 브랜드 인지도를 높이고 적절하게 실행될 때 추가적인 수입원을 받을 수 있도록 한다.<br/>
    <br/>
    공개 API에는 오픈(무료)과 상용(무료) 두 종류가 있다. Open API Definition은 그러한 API의 모든 기능이 공개적이며 제한적인 약관 없이 사용할 수 있다고 제안한다. 예를 들어 API 공급업체의 명시적인 승인이나 의무적인 라이센스 수수료 없이 API를 활용하는 애플리케이션을 구축할 수 있다. 정의에는 API 설명서와 모든 관련 문서를 공개적으로 사용할 수 있어야 하며, API를 자유롭게 사용하여 응용프로그램을 만들고 테스트할 수 있다고 명시되어 있다.<br/>
    <br/>
    상용 API 사용자는 가입비를 지불하거나 종량제 방식으로 API를 사용한다. 출판사들 사이에서 인기 있는 접근법은 무료 체험판을 제공하는 것으로, 사용자들은 구독을 구입하기 전에 API를 평가할 수 있다.<br/>

<br/>
<br/>

### **사용 사례별 API**

`API는 설계된 시스템에 따라 분류될 수 있다`

- **Database APIs**

    데이터베이스 API는 응용프로그램과 데이터베이스 관리 시스템 간의 통신을 가능하게 한다. 개발자는 데이터 액세스, 테이블 변경 등을 위해 쿼리를 작성함으로써 데이터베이스와 함께 작업한다. 예를 들어 [Drupal 7 Database API](https://www.drupal.org/docs/7/api/database-api/database-api-overview)는 사용자가 독점 및 오픈 소스의 서로 다른 데이터베이스에 대한 통합 쿼리를 작성할 수 있도록 한다.(Oracle, MongoDB, PostgreSQL, MySQL, CouchDB 및 MSSQL). 또 다른 예로는 Oracle REST Data Services에 내장된 [ORDS 데이터베이스 API](https://docs.oracle.com/en/database/oracle/oracle-rest-data-services/19.1/aelig/enabling-ords-database-api.html#GUID-8730051B-7C03-487B-954A-7D6786B7EC74)가 있다.

- **Operating systems APIs**

    이 API 그룹은 애플리케이션이 운영 체제의 리소스와 서비스를 사용하는 방법을 정의한다. 모든 OS에는 Windows API 또는 Linux API(커널-사용자 공간 API 및 커널 내부 API)와 같은 API 집합이 있다.<br/>
    <br/>
    애플은 개발자 설명서에서 macOS와 iOS에 대한 API 레퍼런스를 제공한다. Apple의 MacOS 데스크탑 운영 체제용 응용 프로그램을 구축하기 위한 API는 코코아 개발 도구 세트에 포함되어 있다. iOS 모바일 운영 체제용 구축 앱은 코코아의 변형 버전인 코코아 터치를 사용한다.

- **Remote APIs**

    원격 API는 서로 다른 컴퓨터에서 실행되는 응용 프로그램에 대한 상호 작용 표준을 정의한다. 즉, 한 소프트웨어 제품이 이를 요청하는 기기 외부에 위치한 자원에 접근하는 것으로, 이것이 그 이름을 설명한다. 두 개의 원격 위치 응용 프로그램이 통신 네트워크, 특히 인터넷을 통해 연결되기 때문에, 대부분의 원격 API는 웹 표준을 기반으로 작성된다. Java Database Connectivity API와 Java Remote Method Invocation API는 원격 애플리케이션 프로그래밍 인터페이스의 두 가지 예다.

- **[Web APIs](https://developer.mozilla.org/en-US/docs/Web/API)**

    가장 일반적이다. 웹 API는 클라이언트-서버 아키텍처를 대표하는 웹 기반 시스템 간에 기계 판독이 가능한 데이터와 기능 전송을 제공한다. 이들 API는 주로 웹 애플리케이션의 요청과 HTTP(Hypertext Transfer Protocol)를 사용하는 서버의 응답을 전달한다.<br/>
    <br/>
    개발자들은 웹 API를 사용하여 그들의 앱이나 사이트의 기능을 확장할 수 있다. 예를 들어 핀터레스트 API에는 보드나 핀과 같은 사용자의 핀터레스트 데이터를 웹사이트에 추가하기 위한 도구가 함께 제공된다. 구글 맵스 API는 조직의 위치가 포함된 맵을 추가할 수 있다.