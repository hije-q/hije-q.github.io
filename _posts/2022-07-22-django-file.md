---
layout: post
title: "django 각 파일의 역할에 대해"
author: hije
tags: init.py, django
categories: django
---
## < 프로젝트 폴더 내 파일 >
1. __init__.py
* 프로젝트 폴더를 하나의 패키지로 인식할 수 있게 해주는 파일 (비어있는 상태로 놔둔다)
<br/><br/>

2. asgi.py
* 장고 어플리케이션이 비동기식 웹 서버와 연결 및 소통하는 것을 돕는다.
* django 3 버전에서 새로 생긴 파일
<br/><br/>

3. settings.py
* django 웹 사이트의 모든 설정을 포함하고 있는 파일
* 앱 등록, 파일들의 위치, DB 세부사항, 보안 관련 사항 등
<br/><br/>

4. url.py
* 사이트의 url 과 view 의 연결을 지정
* 사용자의 http 요청을 받았을 때 요청을 적절한 view 로 포워드 해준다
<br/><br/>

5. wsgi.py
* 장고 앱이 웹서버와 연결 및 소통하는 것을 도음
* 배포할 때 사용
<br/><br/><br/><br/>

## < 어플리케이션 폴더 내 파일>
1. __init__.py
<br/><br/>

2. admin.py
* 관리자용 페이지 관련 기능을 작성하는 파일
<br/><br/>

3. apps.py
* 앱에 대한 정보를 담고 있는 파일 (수정할 일이 없다)
<br/><br/>

4. models.py
* 앱에서 사용하는 Model(database)를 정의하는 곳
<br/><br/>

5. test.py
* 테스트 코드를 작성하는 파일
<br/><br/>

6. views.py
* 중간 관리자 (V)
* View를 정의하는 파일
<br/><br/>
<br/><br/>

[내용 출처](https://velog.io/@gndan4/Django-%EC%9B%B9-%ED%94%84%EB%A0%88%EC%9E%84%EC%9B%8C%ED%81%AC-%EC%9E%A5%EA%B3%A0-%EA%B8%B0%EB%B3%B8-%EC%84%A4%EC%A0%95-Template-HTML-Form-URL)
