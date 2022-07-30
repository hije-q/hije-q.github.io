---
layout: post
title: "백엔드를 위한 Django Rest Framework Chapter 2 - Django 기본 컨셉 익히기"
author: hije
categories: django
---
## DRF Chapter 2 - Django 기본 컨셉 익히기<br/><br>

* 가상 환경이 필요한 이유 - 프로젝트마다 필요한 패키지 버전이 다르기 때문<br/><br>
* 프로젝트와 앱을 구분하기 - $ django-admin startproject myweb .<br/><br>
* 위에서 . 은 현재 위치에 프로젝트를 만들라는 뜻이다.<br/><br>
* http://127.0.0.1:8000 - 8000 은 Django 가 사용하는 포트 번호이다.<br/><br>
* manage.py 파일은 우리가 건드릴 일이 없다. 그저 우리의 명령어를 처리해 주는 파일이라고 하자.<br/><br><br/><br>


### * settings.py 에서는 프로젝트에서 설정할 수 있는 옵션들이 있다.
 DEBUG = True<br/><br>
 True > 디버깅 모드 > 에러가 노출됨.<br/><br>
 배포할 땐 False 로 바꿔야 한다.<br/><br><br/><br>
 
### * ALLOWED_HOSTS = []
허용할 호스트 주소에 대한 내용을 넣는다.<br/><br>
지금은 127.0.0.1 이 호스트 주소가 된다.<br/><br>
프로젝트를 배포할 때는 배포하는 서버의 호스트 주소를 여기에 입력해야 외부에서 우리 프로젝트로 접속할 수 있게 된다.<br/><br><br/><br>

### * INSTALLED_APPS = []
말 그대로 설치된 앱들을 등록하는 옵션이다.<br/><br><br/><br>

### * url.py - 프로젝트의 url 주소를 등록해 놓는다. <br/><br><br/><br>

### * 장고 앱 구조로 알아보는 MTV 패턴 (개발 패턴)
M Model - 앱과 데이터와 관련된 부분을 다룬다.<br/><br>
T Template - 사용자에게 보이는 부분이다.<br/><br>
V View - Model의 데이터를 Template 으로 전달하고 Template 에서 발생하는 이벤트를 처리한다.<br/><br>

### * $ python manage.py createsuperuser
manage.py 의 기능으로 /admin을 입력했을때 관리자 화면으로 로그인할 수 있다.<br/><br><br/><br>

### model (모델)
* 데이터베이스에 저장될 데이터의 모양을 정의하고 관련된 일부 기능들을 설정해 주는 영역이다.<br/><br>
* 현실 세앙을 코드로 옮기는 과정이다.<br/><br>
* 햔실에 있는 개체의 특징을 뽑아서 이를 구성 요소로 하는 것을 모델링이라고 한다. 개체를 모델링한 결과물은 모델이다.<br/><br>
* 모델을 데이터베이스에 적용시키면 그것이 테이블이 된다.<br/><br>
* migration - 모델을 데이터베이스에 적용시키는 과정<br/><br>
* makemigrations - 모델을 변경한 내용을 기록하여 파일로 만들어주는 과정. 앱의 migrations 폴더 내에 파일이 생긴다.<br/><br>
* migrate - makemigrations 에서 생성된 파일을 실제로 실행시켜 실제 데이터베이스에 변경 사항을 적용시켜주는 과정이다.<br/><br>

```python
from django.db import models

class Photo(models.Model):
  title = models.CharField(max_length=50)
  author = models.Charfield(max_length=50)
  image = models.Charfield(max_length=200)
  description = models.TextField()
  price = models.IntegerField()
```
<br/><br>
* 모델을 만들 때 models.Model 이라는 클래스를 상속받아서 그 기능을 그대로 가져다 쓸 수 있으며 위에 나온 필드 설정도 그래로 쓸 수 있다.
쓸만한 필드 종류
```
CharField - 문자열(길이제한 필요)
IntegerField - 정수
TextField - 문자열(길이제한 필요 없음)
DateField - 날짜
DateTimeField - 날짜 + 시간
FileField - 파일
ImageField - 이미지 파일
ForiegnKey - 외래 키(관계)
OnetoOneField - 1대1 관계
ManyToManyField - 다대다 관계
```
<br/><br><br/><br>
### View 
* 템플릿과 모델 사이를 이어주는 다리와 같은 역할<br/><br>
* 코드에서 제일 많은 비중을 차지한다.<br/><br>
* 크게 함수형 뷰와 클래스형 뷰로 나눠볼 수 있다.<br/><br><br/><br>

모델 > 템플릿 > 뷰> url 순서로 작업할 것이나 개발하면서 본인에게 잘 맞는 직관적인 순서를 따라가면 된다.<br/><br><br/><br>


### JWT 토큰
* 토큰은 서버가 아닌 클라이언트에 저장된다.<br/><br>
* 토큰 자체에 사용자의 권한 정보나 서비스를 사용하기 위한 정보가 포함된다.<br/><br>

일반적으로 JWT를 사용하면 아래와 같은 순서로 진행된다.
1. 클라이언트 사용자가 아이디, 비밀번호를 통해 웹서비스 인증<br/><br>
2. 서버에서 서명된 JWT 를 생성하여 클라이어트에 응답으로 돌려주기<br/><br>
3. 클라리언트가 서버에 데이터를 추가적으로 요구할 때 JWT 를 HTTP Header 에 첨부<br/><br>
4. 서버에서 클라이언트로부터 온 JWT 를 검증<br/><br><br/><br>


### 라이브러리와 프레임워크의 차이
* 라이브러리는 톱, 망치, 삽 같은 도구<br/><br>
* 프레임워크는 차, 비행기, 선박 같은 운송수단, 탈 것<br/><br>
* 라이브러리와 다르게 프레임워크는 이미 프로그래밍 할 규칙이 정해져 있다.<br/><br>
* 프레임워크는 목적에 따라 효율적으로 구조를 짜놓는 개발 방식이다. 간편 마라탕 만들기 세트 같은..<br/><br><br/><br>


[출처](https://www.castingn.com/sourcing/kkultip_detail/110)
