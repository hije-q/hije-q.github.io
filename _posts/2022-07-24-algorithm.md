---
layout: post
categories: [algorithm]
title: "순차구조와 선택구조"
author: hije
---
정수 a,b,c 를 입력 받아 최댓값을 출력한다고 했을 때,  
나는 조건문을 중첩해 max 함수를 쓰거나 <, > 로 단순히 비교하여 코드를 작성했었다.  
하지만 더 좋은 해답이 여기에 있다.
<br/><br/>

```python
# a,b,c 를 입력받고

maximum = a
if b > maximum: maximum = b
if c > maximum: maximum = c

print(f'최댓값은 {maximum} 입니다')
```
<br/><br/>

이 코드는 순차적으로 실행된다. 
<br/><br/>
이렇게 한 문장씩 순서대로 처리되는 구조를 **순차구조** 라고 한다.

<br/><br/>

또한 if와 콜론(:) 사이에 있는 식을 조건식이라고 한다.
<br/><br/>

조건식으로 평가한 결과에 따라 프로그램의 실행 흐름이 변경되는데 이러한 구조를 **선택 구조** 라고 한다.
<br/><br/>
* 순차구조
* 선택구조
