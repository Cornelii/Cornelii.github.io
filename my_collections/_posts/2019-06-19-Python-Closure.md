---
layout: post
title: "Python 클로져"
author-id: "Cornelii. G. Son"
tags: [code, python]
---

#### - 클로져란?

- 정의되어 있는 스코프 안에 있는 변수를 참조하는 함수 (이 함수는 일급객체)

- 해당 변수와 바인딩 되어 있는 함수가 클로져.

<br>
##### -스코프

- 스코프, 즉 범위를 4개로 나눌 수 있다.
  1. 현재 함수의 스코프
  2. 현재 함수를 감싸고 있는 스코프
  3. 전역 스코프
  4. 내장 스코프

##### - 일급 객체 함수
- 일급객체 함수란?!
  1.  변수에 할당할 수 있고,
  2. 다른 함수의 인자로 전달할 수 있고,
  3. 표현식에서 사용될 수 있는 함수.

<br>
파이썬은 일급객체함수를 지원한다. 일급객체는 아래와 같이 크게 3가지 특성을 가진다고 정의할 수 있다. 


```python
def func1():
    print('1st-class function')
    
a = func1 # 변수에 할당할 수 있고,

print(func1) # 다른 함수의 인자로 전달할 수 있고,

if func1:
    print('expressive') 
    # 표현식으로 쓰일 수 있다. 
    # (return 될 수 있고, if문 등에 쓰일 수 있다.)
```

<br>
일급객체함수가 어떤 것인지를 이해했다면, 이제 클로져를 살펴보자.<br>
밑의 함수를 보면,

```python
def outer_func(a, b, *args, **kwargs):
    def inner_func(x):
        result = []
        for val in x:
            result.append((val+a)*b)
        return result
    return inner_func
```

`outer_func` 함수안의 스코프에 정의된 `inner_func`함수를 일급객체로서 리턴하고 있다. 
<br>또한,



해당 `inner_func`함수는 `outer_func`에서 전달 받은 인자 `a`와 `b`를 사용하고 있다.

그렇다면, <span style="color:blue;">여기서 가질 수 있는 한 가지 궁금증이 있다면!</span>

<span style="color:red;">a와 b는  `outer_func`가 끝나면, 즉 `outer_func` 스코프 안에서만 역할하는 변수일텐데? 그 a와 b를 안에 품고, 리턴된 `inner_func`에서는 어떻게 될까?!!!</span>

**이 궁금증에 대한 답이 바로 클로져이다!**


<br>
이어서 밑의 예제를 보면,

```python
myfunc1 = outer_func(2,10)

print(myfunc1)
# <function outer_func.<locals>.inner_func at 0x~~~~~~~~ >
print(myfunc1([1,2,3,4,5]))
# [30, 40, 50, 60, 70]
```

`a` 로 2를, `b`로 10을 넘겨주었다.  `myfunc1`는 잘 작동을 한다???! 왜?!

넘겨주었던, 2와 10을 찾아보면,

```python
print(myfunc1.__closure__[0].cell_contents)
# 2
print(myfunc1.__closure__[1].cell_contents)
# 10
```

해당 함수의 `__closure__` 의 리스트에서 `cell_contents`로 접근할 수 있다.



이 처럼, 참조된 변수와 함께 바인딩 되어 있는 함수를 **클로져**라 한다.

(다시 기억해보자, 일급객체함수도 변수가 될 수 있다. 이 말은?! 함수자체도 함께 바인딩 될 수 있다.)
<br><br><br><br>




조금 더 생각해보자~

클로져는

마치, 함수가 상태를 가지고 있는 것 같다.



어디서 들어본 듯 하지 않는가??...

상태 + 행동, 거의 클래스네?!!



클로져를 활용해서~!

```python
def outer_func(a, b, *args, **kwargs):
    def inner_func1():
        print("yeah")
    
    def inner_func(x):
        result = []
        for val in x:
            result.append((val+a)*b)
        inner_func1()
        return result
    return inner_func

myfunc1 = outer_func(2,10)
print(myfunc1([1,2,3,4,5]))
# yeah
# [30, 40, 50, 60, 70]
```



클래스를 활용해서~!

```python
class Inner_func:
    def __init__(self, a, b):
        self.a = a
        self.b = b
        
    def inner_func(self):
        print("yeah")
    
    def __call__(self, x):
        result = []
        for val in x:
            result.append((val+self.a)*self.b)
        self.inner_func()
        return result

myfunc2 = Inner_func(2,10)
print(myfunc2([1,2,3,4,5]))
# yeah
# [30, 40, 50, 60, 70]
```



그렇네.... 물론 직접적으로 멤버변수, 메소드에 접근하는 `.`의 활용 등은 안되지만,



클로져를 활용하면 어느 면에서는 마치 클래스처럼 상태 또는 메소드를 가지고 있듯이 함수를 사용할 수 있다.

이정도로만 일단 알아두자~!
<br>
<br>


**결론,**

**클로져는 클래스의 객체와 비슷한 함수이다.**
