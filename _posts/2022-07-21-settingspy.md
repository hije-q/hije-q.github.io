---
layout: post
title: "장고 settings.py에 대해"
categories: django
author: hije
tags: settings.py
---
# <장고 settings.py>
### 장고 프레임워크의 모든 개발환경 세팅은 settings.py 파일에서 설정한다.
* 로그 설정, app등록, Templates 설정, DB 설정, 다국어 및 지역 시간 설정, 정적파일 설정 등을 관리한다.<br/><br/>

## 1. 로그 설정
* 기본은 True 로 되어있어 개발시 로그를 남기게 된다. 
운영시 꼭 False 로 변경을 해줘야 한다.
```python
DEBUG = True
``` 
<br/><br/>
<br/><br/>

## 2. APP 등록
* 생성한 어플리케이션 들을 모드 등록해준다.
$ python manage.py startapp apple 로 apple이라는 앱을 만들었다면 
INSTALLED_APPS 부분에 추가해야 한다.<br/><br/>
```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    ...
    'apple',
]
```
참고로 마지막에 , 를 빠뜨려선 안된다.<br/><br/><br/><br/>

## 3. Templates 설정
* 공통적으로 들어가는 html 코드를 관리하기 위한 확장형 template들의 경로를 설정할 수 있다.
```python
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [os.path.join(BASE_DIR, 'templates')],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]
```
음 이건 뭔소린지 잘 모르겠다.. template 이 뭔지 알아보도록 하자<br/><br/>
* template 은 html 파일로서 django app 폴더 밑에 templates 라는 서브폴더를 만들고 그 안에 템플릿 파일(.html)을 생성한다. 이는 단일 app이거나 동일 템플릿명이 없는 경우 사용할 수 있다.<br/><br/>

* 즉 settings.py 에선 이런 template 들의 경로를 설정할 수 있다는 거다.<br/><br/><br/><br/>

## 4. DB 설정
* default로 sqllite를 사용한다.
``` python
# Database
# https://docs.djangoproject.com/en/2.1/ref/settings/#databases

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
    }
}
```
<br/><br/> <br/><br/>

## 5. 다국어 및 지역 시간 설정
* 기본 설정은 LANGUAGE_CODE= "en-us", TIME_ZONE = "UTC"로 되어 있다.
```python
# Internationalization
# https://docs.djangoproject.com/en/2.1/topics/i18n/

# 한글, 한국 표기는 kor-kr, Asia/Seoul
LANGUAGE_CODE = 'ko-kr'

TIME_ZONE = 'Asia/Seoul'

USE_I18N = True

USE_L10N = True

USE_TZ = True
```

<br/><br/><br/><br/>

## 6. 정적파일 설정
```python
# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/2.1/howto/static-files/

STATIC_URL = '/static/'
```
<br/><br/>

* 정적 파일(static file)이란 움직이지 않는 파일이다.  
우리가 페이지를 만들 때 쓰임이 정해져있는 파일들이기 때문에 개발하는 단계에서 이러한 파일들을 관리하는 것이다.  
css, jpg, javascript 파일 같은 것들이다.<br/><br/><br/><br/>

이렇게 settings.py 에 있는 코드들이 어떤 역할을 하는지 알아보았다.  
다음엔 내 코드에 적용시키며 뭐가 무엇인지 알아보도록 하자.<br/><br/>

* 참고로 markdown 문법에서 줄바꿈은 스페이스바 2번이다..<br/><br/>

[내용 출처](https://myjamong.tistory.com/101)




