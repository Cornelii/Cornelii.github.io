---
layout: post
title: "Python 데코레이터"
author-id: "Cornelii. G. Son"
tags: [code, python]
mathjax: true
---

#### - 데코레이터?!

데코레이터는 함수를 인수로 받아 함수를 반환하는 함수라고 말할 수 있습니다. 
<br/><br/>
특정 상태의 데이터 X 를 Y로 바꾸는 함수 f가 있다고 해봅시다.
<br/><br/>
$$ 
f: X -> Y
$$
<br/><br/>
물론, 특정한 기능을 수행하고 반환값이 없는 함수가 있을 수 있습니다. 그런 경우는 아래처럼 생각해볼 수 있는데요.
<br/><br/>
아래의 기능을 하는 함수를 생각해보면, <br/>

```python
def hello():
    print("Hello!")
```
<br/>
n-1 번 Hello!를 출력한 상태(X)에서 n 번 Hello!를 출력한 상태로(Y) 만들어주는 함수 **hello** 라고 생각할 수 있겠지요.
<br/><br/>
다시 본론으로 돌아와서, 아래와 같이 상태 X 전에 특정한 기능을 수행하고 또 Y 이후에 특정한 기능을 수행하도록 한 함수가 있다고 해봅시다.
<br/><br/>

<br/><br/>

<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
