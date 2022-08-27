---
layout: post
title: "Maxwell's Equations from Special Relativity"
author-id: "Cornelii. G. Son"
tags: [Maxwell Equation, Special Relativity]
comments: true
mathjax: true
chapter: "1-2"
---

#### - 데코레이터?!

데코레이터는 함수입니다. **함수를 인수로 받아 함수를 반환하는 함수라고 말할 수 있습니다.** 
<br/><br/>
특정 상태의 데이터 X 를 Y로 바꾸는 함수 f가 있다고 해봅시다.
<br/><br/>
$$ 
f: X \rightarrow Y
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
다시 본론으로 돌아와서, 아래와 같이 상태 X 전에 특정한 기능을 수행하고, 또 Y 이후에 다른 특정한 기능을 수행하는 함수가 있다고 해봅시다.
<br/><br/>
이런 함수죠. 
$$ \begin{aligned} \tilde{f} = \tilde{X} \rightarrow X \rightarrow Y \rightarrow \tilde{Y}  \end{aligned}$$
<br/><br/>
<img src="/assets/img/programming/01/deco_scheme.png" alt="Decorator_Scheme" width="1000"/>
<br/><br/>
<br/><br/>
그렇다면, 데코레이터 d는  
$$ \begin{aligned} d : f \rightarrow \tilde{f}  \end{aligned}$$ 
<br/><br/>
$$ \begin{aligned} d(f) = \tilde{f} \end{aligned} $$
<br/><br/>
라고 말할 수 있습니다.
<br/><br/>
함수 앞 뒤에 다른 기능을 부과한 함수로 바꿔 반환해 주는 함수!
<br/><br/>
소스의 형태로 바꿔볼까요?
<br/><br/>
**Decorator** 

```python
def decorator_fcn(f):
    def f_tilde(X_tilde):
        X = g(X_tilde)
        Y = f(X)  # 기존 함수의 기능
        Y_tilde = h(Y)
        return Y_tilde
    return f_tilde
```

<br/><br/>
어떤 함수가 있다고 한다면 실행 전에 Hello World!, 실행 후에 Bye World! 를 출력하는 데코레이터를 예로 만들어 봅시다. 
<br/><br/>

```python
def decorator1(fcn):
    def wrapper(*arg, **kwargs): # 이름이 꼭 wrapper일 필요 없습니다.
        # 함수 실행 이전 동작
        print("Hello World!")
        
        fcn(*arg, **kwargs)
        
        # 함수 실행 이후 동작
        print("Bye World!")
    return wrapper
```

<br/><br/>
그러면 데코레이터를 어떻게 간단히 적용할까요?
<br/><br/>
당연히 함수니 함수를 쓰는것 처럼 쓸 수 있겠죠? 거기에 더해 **@** 문자를 사용하여 특정 함수에 쉽게 적용할 수 있습니다.
<br/><br/>
아래를 예로 보시죠.
<br/><br/>

```python
def some_fcn1(a):
    print(a)

def some_fcn2(a):
    print(a)

some_fcn1("Oops!")
# Oops!

some_fcn2("No way!")
# No way!
```

<br/><br/>
위와 같은 두 함수를 생각해 볼 때 데코레이터를 적용해 본다면,
<br/><br/>


```python
# 1.그냥 함수로써 사용하기
decorated_fcn = decorator1(some_fcn1)
decorated_fcn("Oops!")
# Hello World!
# Oops!
# Bye World!

# 2. Decorator 문법 사용하기
@decorator1
def some_fcn2(a):
    print(a)

some_fcn2("No way!")
# Hello World!
# No way!
# Bye World!

```

<br/><br/>
2번째 방법(@)을 사용하면 기존 함수명을 바꾸거나 새로 함수를 선언하지 않아도 함수 실행 전후에 기능을 쉽게 붙혀 실행시킬 수 있는 것을 확인할 수 있습니다.
<br/><br/>
여기서 한가지.
<br/><br/>
데코레이터 선언부 안의 wrapper 함수에 인수를 꼭 `*args, **kwargs`로 해야할까요?
<br/><br/>
사실, 그렇지는 않습니다. 적용할 함수가 받을 인수 형태가 들어가면 되는 것이죠. 
<br/><br/>
하지만, 데코레이터의 범용성을 위해서는 가변인수를 사용하는 것이 유용할 것입니다.
<br/><br/>
여기서 한 가지만 더~!
<br/><br/>
한 함수에 데코레이터를 여러 번 적용하면 어떻게 될까요?
<br/><br/>
선언한 함수에 가까운 데코레이터부터 순서대로 함수를 감싼다고 생각할 수 있습니다.
<br/><br/>
아래를 예로 보시죠.
<br/><br/>

```python
def decorator_level1(fcn):
    def wrapper(*args, **kwargs):
        print("level1")
        fcn(*args, **kwargs)
        print("level1")
        
    return wrapper

def decorator_level2(fcn):
    def wrapper(*args, **kwargs):
        print("level2")
        fcn(*args, **kwargs)
        print("level2")
        
    return wrapper

def decorator_level3(fcn):
    def wrapper(*args, **kwargs):
        print("level3")
        fcn(*args, **kwargs)
        print("level3")
        
    return wrapper

@decorator_level3
@decorator_level2
@decorator_level1
def some_fcn1(a):
    print(a)
    
some_fcn1("Decorator order test1")

#level3
#level2
#level1
#Decorator order test1
#level1
#level2
#level3

@decorator_level1
@decorator_level2
@decorator_level3
def some_fcn2(a):
    print(a)
    
some_fcn2("Decorator order test2")

#level1
#level2
#level3
#Decorator order test2
#level3
#level2
#level1

```

<br/><br/>
#### Decorator는 어디에 유용하게 쓰일 수 있을까요?
<br/><br/>
한 가지 상황을 가정해봅시다.
<br/><br/>
수천 개의 함수가 포함되어 있는 라이브러리와 프로그램이 있습니다.
<br/><br/>
그런데, 함수들의 호출 전후의 기능이 다 바뀐다고 합니다.
<br/><br/>
그렇다면, 해당하는 모든 함수를 고쳐서 새로운 함수를 만들거나,
<br/><br/>
그 함수를 호출하는 모든 부분을 고쳐야 되는 경우가 생길 수 있습니다.
<br/><br/>
그러나, 데코레이터가 출동한다면? 데! 코! 레! 이! 터!?
<br/><br/>
데코레이터를 선언하고, 각 함수의 선언부에 `@`를 통해 함수를 바꿔줌으로써, 
<br/><br/>
함수의 이름을 바꾸지 않고, 상대적으로 빠르게 변경을 적용시킬 수 있다는 것~! 예히.
<br/><br/>
<br/><br/>

#### 정리하면,
1. Python의 Decorator는 함수를 받아 함수를 반환하는 함수이다.
2. 특정 함수의 호출 전과 후에 기능을 추가적으로 넣을 수 있다.
3. @문법으로 완성합시닷


<br/><br/>
냠냠.