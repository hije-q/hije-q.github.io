---
layout: post
title: "API 명세서와 HTTP Method"
author: hije
categories: backend
---
### API 란?
* 서버와 클라이언트가 데이터를 주고 받을 수 있도록 도움을 주는 매개체<br/><br/>
* API 를 사용하기 위해서 사용자는 서버와 클라이언트 사이에 존재하는 몇 가지 약속을 따라야 한다.<br/><br/>
* 메세지의 데이터 형식이 무엇인지, 글자수 제한이 있는지, 어떤 방식으로 데이터가 전달되어야 하는지 등의 약속이 있다.<br/><br/>
* 그럼 이 약속들을 어디서 확인할 수 있을까? 바로 API 문서(명세서)에서 확인할 수 있다.<br/><br/>
[출처](https://tech.kakaoenterprise.com/127)<br/><br/>

### Notion ?
* 노션은 메모, 데이터베이스, 알림과 같은 기능을 지원하는 소프트웨어로, 프로젝트를 진행하면서 필요한 관리 공간을 만들어 준다.
<br/><br/><br/><br/>
### 순서
1. 우선 기능들을 뽑아서 우선순위가 높은 기능들부터 작성한다.<br/><br/>
2. Post/Get/Put/Delete<br/><br/>
3. Request 형식을 적는다<br/><br/>
4. Response 형식을 적는다.<br/><br/>

![api 명세서](https://t1.daumcdn.net/cfile/tistory/9920EB4B5A83490B03)
[출처](https://chickenpaella.tistory.com/31)


이렇게 말이다..

<br/><br/>
<br/><br/>
### Http Method
* 서버와 클라이언트가 소통을 하기 위해서 보통 http를 이용을 한다.<br/><br/>
* http method 에는 GET, POST, PUT, DELETE 가 대표적이며 8개의 메서드가 있다.<br/><br/>
<br/><br/>
### GET: 조회
* 데이터를 읽거나 검색할때 사용된다.<br/><br/>
* GET 요청이 성공적으로 이루어지면 XML이나 JSON 과 함께 200 (Ok) HTTP 응답 코드를 리턴한다.<br/><br/>
* 에러가 발생하면 주로 404 (Not found) 에러나 400 (Bad request) 에러가 발생한다.<br/><br/>
* GET 요청은 오로지 데이터를 읽을 때만 사용되고 수정할 때는 사용하지 않는다.<br/><br/>
* GET 요청은 idempotent 하다. (여러번 수행해도 결과가 같다/ 호출로 인하여 데이터가 변형되지 않는다.)<br/><br/>
* 같은 요청을 여러 번 하더라도 변함없이 항상 같은 응답을 받을 수 있다.<br/><br/>
* 데이터를 변경하는 연산에 사용하면 안 된다.<br/><br/>

```
GET /USER/1
```

* 데이터를 조회하는 것이기 때문에 요청시에 Body 값과 Content-Type 이 비워져있다.<br/><br/>
* 조회할 데이터에 대한 정보는 url을 통해서 파라메터를 받고 있는 모습을 볼 수 있다.<br/><br/>
* 데이터 조회에 성공한다면 Body 값에 데이터 값을 저장하여 성공 응답을 보낸다.<br/><br/><br/><br/>

### POST: 등록
* POST 는 주로 새로운 리소스를 생성할 때 사용된다. <br/><br/>
* 성공적으로 creation을 완료하면 201 (Created) HTTP 응답을 반환한다.<br/><br/>
* POST 요청은 idempotent 하지 않다.<br/><br/>
* 같은 POST 요청을 반복해서 했을 때 항상 같은 결과물이 나오는 것을 보장하지 않는다.<br/><br/>
* 두 개의 같은 POST 요청을 보내면 같은 정보를 담은 두 개의 다른 resource를 반환할 가능성이 높다.<br/><br/>

```
POST /user
body : {date : "example"}
Content-Type : "application/json"
```

* 데이터를 생성하는 것이기 때문에 요청시에 Body 값고 Content-Type 값을 작성해야한다.<br/><br/>
* url 을 통해서 데이터를 받지 않고, Body 값을 통해서 받는다.<br/><br/>
* 데이터 조회에 성공한다면 Body 값에 저장한 데이터 값을 저장하여 서옹 응답을 보낸다.<br/><br/>

### PUT: 수정
* PUT 은 리소스를 생성/ 업데이트 하기 위해 서버로 데이터를 보내는 데 사용된다.<br/><br/>
* PUT 요청은 idempotent 하다.<br/><br/>
* 동일한 PUT 요청을 여러번 호출하면 항상 동일한 결과가 생성된다.<br/><br/>

```
PUT /user/1
body : {date : "update example"}
Content-Type : "application/json"
```


* 데이터를 수정하는 것이기 때문에 요청시에 Body 값과 Content-Type 값을 작성해야 한다.<br/><br/>
* URL 을 통해서 어떤 데이터를 수정할지 파라메터를 받는다.<br/><br/>
* 그리고 수정할 데이터 값을 Body 값을 통해서 받는다.<br/><br/>
* 데이터 조회에 성공한다면 Body 값에 저장한 데이터 값을 저장하여 성공 응답을 보낸다.<br/><br/><br/><br/>

### DELETE: 삭제
* 지정된 리소스를 삭제한다.<br/><br/>

```
DELETE /user/1
```

* 데이터를 삭제하는 것이기 때문에 요청시에 Body 값과 Content-Type 값이 비워져있다.<br/><br/>
* url 을 통해서 어떠한 데이터를 삭제할지 파라메터를 받는다.<br/><br/>
* 데이터 삭제에 성공한다면 Body 값 없이 성공 응답만 보내게 된다.<br/><br/><br/><br/>

### POST vs PUT
둘은 구분해서 사용해야 한다.  <br/><br/>
POST는 새로운 데이터를 계속 생성하기 때문에 요청할 때마다 데이터를 생성하지만, PUT 은 사용자가 데이터를 지정하고 수정하는 것이기 때문에 같은 요청을 계속 하더라도 데이터가 계속 생성되지는 않는다.<br/><br/>
<br/><br/>
[출처](https://velog.io/@yh20studio/CS-Http-Method-%EB%9E%80-GET-POST-PUT-DELETE)

