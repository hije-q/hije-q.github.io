---
layout: post
title: "Serializer 에 대해"
author: hije
categories: backend
---
Django Rest Framework 를 사용하면 serializer 라는 개념이 새롭게 등장한다.<br/><br/>
serializer - 직렬화<br/><br/>

django에 저장되어 있는 모델 인스턴스를 Rest API 에서 사용하는 JSON 의 형태로 바꿔주는 것을 말한다.<br/><br/><br/><br/>

```python
# models.py
class Journalist(models.Model):
    first_name = models.CharField(max_length=60)
    last_name = models.CharField(max_length=60)
    
class Article(models.Model):
    author = models.ForeignKey(Journalist, on_delete=models.CASCADE)
    title = models.CharField(max_length=120)
    description = models.CharField(max_length=120)
    body = models.TextField(max_length=500)
    location = models.CharField(max_length=50)
    publication_date = models.DateField()

    active = models.BooleanField(default=False)

    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
```
<br/><br/><br/><br/>
```python
# serializers.py
from rest_framework import serializers
from news.models import Article, Journalist


class ArticleSerializer(serializers.ModelSerializer):

    class Meta:
        model = Article
        exclude = ('id',)


class JournalistSerializer(serializers.ModelSerializer):

    article_set = serializers.HyperlinkedRelatedField(many=True, read_only=True, view_name='article-detail')

    class Meta:
        model = Journalist
        fields = '__all__'
 ```
 <br/><br/><br/><br/>
 한 줄 정리 - model을 rest api 에서 사용하는 json 형태로 바꿔주는 것이다.
 <br/><br/><br/><br/>
 [출처](https://hangjastar.tistory.com/m/206)
