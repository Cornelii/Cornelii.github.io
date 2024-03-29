---
layout: post
title: "평균와 분산, 그리고 확률변수의 선형 결합"
author-id: "Cornelii. G. Son"
tags: [study, statistics]
updated: "2020-02-29"
chapter: "1-4"
comments: true
en_title: "Expectation, Variance, and Linear Combination of Random Variable"
---

특정한 표본공간과 확률변수가 있습니다. 이 표본공간을 어떻게 간단하게 나타낼 수 있을까요?
<br/><br/>
비슷한 말로 Aggregate또는 Measure라고도 할 수 있는데, 집합을 실수 하나로 대응시키는 것을 의미합니다.
<br/><br/>
지금 하고 싶은 것이 그것입니다. 표본공간을 확률변수를 활용해 몇 가지 숫자로 나타내는 것.
<br/><br/>
<br/><br/> 

## 기댓값
<br/>
먼저, 왜 기댓값이라고 할까요? 무엇을 기대하는 걸까요? 예상하는 걸까요? 왜 이런 것을 정의했을까요?
<br/><br/>
확률변수가 정해진 표본공간이 있습니다. 
<br/>
확률 변수(Random Variable) 다시 말해,
<br/><br/>
해당 사건이 일어날 때마다, 값 (확률 변수 값)이 다릅니다. 
<br/><br/>
정확히 뭐다! 얘기할 순 없지만, 대충 어느정도 될 것이라고 말하고 싶습니다.
<br/><br/>
특정 사건이 발생한다면, 우리는 어떤 값을 가지게 될까를 합리적으로 예상하고 싶은 것입니다.
<br/><br/>
먼저 기댓값에 대한 식을 보기 전에, 일반적인 평균처럼 계산한 식은 아래와 같습니다.
<br/><br/>
표본공간 S에 확률변수가 n개의 값을 가질 때, 그 확률변수를 x로 표현하면
<br/><br/>
$$ mean = \frac{1}{n}\sum_{i=1}^{n} x_{i} $$
<br/><br/>
n번 더하고 n으로 나누는 산술평균은 굉장히 합리적으로 보입니다.
<br/><br/>
사실, 이것은 모든 경우에 
$$ \frac{1}{n} $$
의 가중치를 두고 계산한 기댓값이라고 생각할 수 있습니다.
<br/><br/>
하지만, 모든 확률변수가 같은 가중치를 가진 것은 아니지요. 각각의 대응되는 가중치(확률)이 있을 것입니다.
<br/><br/>
그래서, 기댓값은 아래와 같이 표현할 수 있습니다.
<br/><br/>
$$ E[X] = \mu = \sum_{i=1}^{n}x_{i}p(x_{i})$$
<br/><br/>
확률 또는 가중치를 곱하고 모든 항을 더해서 값을 구하는 것입니다.
<br/><br/>
여기서 유의해야 하는 것은 여기서 말하는 기댓값은 흔히 아는 표본평균을 말하는 것이 아니라, n개의 원소를 가진 표본공간이 있을 때 전체 표본공간의 기댓값을 의미합니다.
<br/><br/>
$$ S = (x_{1},x_{2},x_{3},...,x_{n})$$
표본공간 S의 기댓값!
<br/><br/>
연속표본공간에서는 아래와 같이 표현합니다.
<br/><br/>
$$ E[X] = \mu_{x} = \int x p(x) dx $$
<br/><br/>
<br/><br/>

## 분산
<br/>
기댓값 하나로는 표본공간을 적절히 대표하기 애매한 부분이 있습니다. 예를 들어,
<br/><br/>
두 표본공간 (-7, 0, 7), (100, 0, -100)은 확연히 달라 보이는데, 모든 가중치를 같게 한 기댓값은 0으로 동일하기 때문입니다.
<br/><br/>
그래서 얼마나 값들이 퍼져있나에 대한 척도의 필요성으로 분산 (Variance)이라는 값을 구하게 됩니다.
<br/><br/>
$$ V[X] = \sigma^2_{x} = \sum (x_{i} - \mu_{x})^2p(x_{i}) = E[(X - \mu)^2]$$
<br/><br/>
식에서 기댓값과의 차이 (편차)를 제곱하여 그것의 기댓값을 구하면, 분산이 되므로, 음수가 될 수 없고, 항상 0보다 크게 됩니다.
<br/><br/>
각 확률변수가 그 기댓값과의 차이가 커질 수록, 분산이 커지게 됨을 알 수 있고, 이를 이용해 얼마나 기댓값에서 떨어져 있나를 나타내게 됩니다.
<br/><br/>
여기서 기억해야 할 것은, 분산 값이 같다고해도, 분포가 같은 것은 아니라는 것입니다.
<br/><br/>
연속표본공간에서는 아래와 같이 표현합니다.
<br/><br/>
$$ V[X] = \int (x-\mu)^2p(x)dx$$
<br/><br/>
그리고, 분산의 제곱근
$$\sqrt{V} = \sigma$$
를 표준 편차 (Standard Deviation)라고 합니다.
<br/><br/>
<br/><br/>

## 공분산
<br/>
공분산(Covariance)은 두 확률변수 간의 선형관계가 있는지 확인해보기 위한 정의입니다.
<br/><br/>
여기서 선형관계라 함은, 확률변수 X와 Y가 있을 때,
<br/><br/>
$$ Y = aX + b$$
<br/><br/>
위와 같이 확률변수가 다른 확률변수의 이런 변환을 통해 표현될 수 있는가를 의미합니다.
<br/><br/>
공분산은 아래와 같이 정의됩니다. 확률 변수 X와 Y가 있을 때,
<br/><br/>
$$ Cov(X,Y) = \sum_{x} \sum_{y} (x_i - \mu_{x})(y_j - \mu_{y})p(x,y)$$
<br/><br/>
다음과 같이 나타낼 수 있고, 여기서 p(x,y)는 확률변수 X와 Y의 결합확률입니다.
<br/><br/>
여기서도, 유의할 것이 있습니다. 이것은 표본공간의 공분산입니다.
<br/><br/>
표본공간의 원소에 대해 구하는 것입니다. **표본이 아니라**
<br/><br/>
제곱항이 없는 것으로 보아서, 양수, 0, 음수 어떤 값도 가질 수 있습니다.
<br/><br/>
양수는 2차원 그래프에 그렸을 때, 기울기가 양수인 직선에서 흩어져있는 모습,
<br/><br/>
음수일 때는 기울기가 음수인 직선에서 흩어져 있는 모습,
<br/><br/>
0일 때는 그냥 고루 흩어져 있는 모습을 기대해 볼 수 있지만, 
<br/><br/>
**어디까지나 정도를 나타낼 뿐입니다.**
<br/><br/>
<br/><br/>

## 상관계수
<br/>
두 확률 변수가 있을 때, 표준편차와 공분산을 이용하여 적절한 숫자를 뽑아낼 수 있습니다.
<br/><br/>
그것이 상관계수입니다.
<br/><br/>
$$ \rho = \frac{Cov(X,Y)}{\sigma_{X}\sigma_{Y}}$$

기본적인 느낌은 공분산과 같지만, 값은 -1과 1사이의 값을 가지게 되므로, 공분산보다 좀 더 정규화된 값이라 할 수 있습니다.
<br/><br/>
이제 예시로 위에서 말했던,
<br/><br/>
$$ Y = aX + b $$
<br/><br/>
의 관계일 때 상관계수를 생각해봅시다.
<br/><br/>
확률변수 간에 위와 같은 관계가 있다면, 확률변수 X가 정해지면, Y가 결정된다는 것을 의미합니다.
<br/><br/>
결국 X가 일어나는 확률과 Y가 일어나는 P(X, Y) = P(X)가 됩니다.
<br/><br/>
X가 일어나면 특정한 그 X에 따른 Y가 결정되기 때문입니다. 
<br/><br/>
다시 말해, 두 확률 변수가 관계를 가진다는 의미는! 더이상 두 표본공간의 확률로써 고려되지 않는 다는 말입니다.
<br/><br/>
$$ S_{xy} = (x_i) X (y_j)    =>    S_{xy} = (x_i, y_i) $$
<br/><br/>
수식으로 그대로 나타내보면,
<br/><br/>
$$ \begin{aligned} 
\rho = \frac{Cov(X,Y)}{\sigma_{X}\sigma_{Y}} &= \frac{\sum_{x} \sum_{y} (x_i - \mu_{x})(y_j - \mu_{y})p(x_i,y_j)}{\sqrt{\sum (x_{i} - \mu_{x})^2p(x_{i})}\sqrt{\sum (y_{j} - \mu_{y})^2p(y_{j})}} \\ \\ &= \frac{\sum_{x} (x_i - \mu_{x})\sum_{y} (y_j - \mu_{y})p(x_i,y_j)}{\sqrt{\sum (x_{i} - \mu_{x})^2p(x_{i})}\sqrt{\sum (ax_{j} - a\mu_{x})^2p(x_{j})}} \\ \\ &= \frac{\sum_{x} (x_i - \mu_{x})(y_i - \mu_{y})p(x_i)}{a\sum (x_{i} - \mu_{x})^2p(x_{i})} \\ \\ &= \frac{\sum_{x} (x_i - \mu_{x})(ax_i - a\mu_{x})p(x_i)}{a\sum (x_{i} - \mu_{x})^2p(x_{i})} \\ \\ &= \frac{a\sum (x_i - \mu_{x})^2p(x_i)}{a\sum (x_{i} - \mu_{x})^2p(x_{i})} \\ \\ &= 1
\end{aligned} $$
<br/><br/>
1이 되게 됩니다! (a가 양수일 경우임, 음수일 경우에는 분모에서 -a로 나오게 되어 -1이 됨)
<br/><br/>
여기서 선형결합의 기댓값을 증명없이 사용하였지만, 이는 밑에서 살펴보려 합니다.
<br/><br/>
<br/><br/>

## 확률변수 선형결합에 따른 기댓값과 분산
<br/>
이번에는 확률변수의 선형 변환 및 결합에 따른 기댓값과 분산의 변화를 살펴보겠습니다.
<br/><br/>
여기서 헤깔리지 말아야 할 것이, 이번에는 `선형변환`입니다. X -> aX + b로 바꿧을 때, 기댓값과 분산에 생기는 변화를 살펴보려는 것입니다.
<br/><br/>
위의 공분산에서는 (X, Y)의 관계를 나타낸 것이었습니다. 혼동하지 마시길.
<br/><br/>
거두절미하고 식으로 보시죠.
<br/><br/>
먼저 기댓값을 먼저 보면
<br/><br/>
$$ E[X] = \sum xp(x)  = \mu_x $$
<br/><br/>
$$ E[aX+b] = \sum (ax+b)p(x) = a\sum xp(x) + b \sum p(x) = a \mu_x + b$$
<br/><br/>
마지막의 b는 표본공간의 원소에 대응하는 확률을 모두 더하면 1이 되는 성질을 이용한 것입니다.
<br/><br/>
그 다음 분산을 보면,
<br/><br/>
$$ V[x] = \sum (x-\mu_x)^2p(x) = \sigma_x^2  $$
<br/><br/>
$$ \begin{aligned} V[ax+b] = \sum(ax+b - \mu_{ax+b})^2p(x) &= \sum(ax+b -a\mu_x-b)^2p(x) \\ \\
&= a^2\sum(x-\mu_x)^2p(x) = a^2\sigma_x^2 
\end{aligned}$$
<br/><br/>
이번에는 한 걸음 더 나아가 Z = aX + bY + c와 같이, 두 확률변수 선형결합하고 상수를 더한 확률변수 Z의 기댓값과 분산을 살펴보겠습니다.
<br/><br/>
기댓값은
<br/><br/>
$$ \begin{aligned}E[Z] &= E[aX + bY + c] = \sum_x \sum_y (ax+by+c)p(x,y) \\ \\
&= a\sum_x x \sum_y p(x,y) + b\sum_y y \sum_x p(x,y) + c \sum_x \sum_y p(x,y) \\ \\
&= a\sum_x x p(x) + b\sum_y y p(y) + c\\ \\
& = a\mu_x + b\mu_y + c = aE[X] + bE[Y] + c
\end{aligned}$$
<br/><br/>
가 됩니다.
<br/><br/>
분산에 대해서 살펴보기 전에, 분산의 조금 더 간단한 표현을 보고 가도록 하겠습니다.
<br/><br/>
$$ \begin{aligned} V[x] = E[(X-\mu_x)^2] &= E[X^2 -2X\mu_x + \mu_x^2] \\ \\
&=  E[X^2] -2\mu_xE[X] + \mu_x^2 \\ \\
&= E[X^2] - 2\mu_x\mu_x + \mu_x^2 \\ \\
&= E[X^2] - \mu_x^2
\end{aligned}$$
<br/><br/>
위와 같이, 기댓값은 이미 구했고, 분산을 구하고자 하는 확률변수 제곱의 기댓값만 구하면 되는 식의 형태로 바꿀 수 있습니다.
<br/><br/>
참고로 공분산에 대해서는
<br/><br/>
$$ Cov(X,Y) = E[XY] - \mu_x\mu_y$$
<br/><br/>
가 되는 것을 비슷한 방법으로 유도할 수 있습니다.
<br/><br/>
자 이제 다시, 확률변수 Z의 분산으로 돌아가면, (위의 형태를 사용해서도 쉽게 유도할 수 있습니다.)
<br/><br/>
$$ \begin{aligned} V[Z] &= V[aX + bY + c] \\ \\
&= \sum_x \sum_y (ax+by+c - \mu_{aX+bY+c})^2p(x,y) \\ \\
&= \sum_x \sum_y (ax+by+c - a\mu_x - b\mu_y - c)^2p(x,y) \\ \\
&= \sum_x \sum_y (ax+by - a\mu_x - b\mu_y)^2p(x,y) \\ \\
&= \sum_x \sum_y ( (ax - a\mu_x) + (by- b\mu_y))^2p(x,y) \\ \\
&= \sum_x \sum_y (ax - a\mu_x)^2p(x,y) + \sum_x \sum_y (by- b\mu_y)^2p(x,y) + 2\sum_x \sum_y (ax - a\mu_x)(by - b\mu_y)p(x,y) \\ \\
&= \sum_x (ax - a\mu_x)^2 \sum_yp(x,y) + \sum_y(by- b\mu_y)^2\sum_xp(x,y) + 2ab\sum_x \sum_y (x - \mu_x)(y - \mu_y)p(x,y) \\ \\
&= a^2\sum_x (x - \mu_x)^2 p(x) + b^2\sum_y(y- \mu_y)^2 p(y) + 2ab \times Cov(X,Y) \\ \\
&= a^2V[X] + b^2V[Y] + 2ab \times Cov(X,Y) \\ \\
\end{aligned}$$
<br/><br/>
확률 변수 X, Y가 서로 독립일 경우에는 공분산이 0입니다.(역은 성립하지 않을 수 있음) 공분산의 분자항이
<br/><br/>
$$ \sum_x(x-\mu_x)p(x)\sum_y(y-\mu_y)p(y) = 0 $$ 다음과 같아지기 때문입니다.

<br/><br/>
그러므로, 확률변수 X, Y가 서로 독립일 때.
<br/><br/>
$$ V[Z] = \sigma_{aX + bY+ c}^2 = a^2\sigma_X^2 + b^2\sigma_Y^2 $$ 이 됩니다.

<br/><br/>
상수항 c가 사라진 것을 볼 수 있습니다. 확률변수의 전체적인 변화는 분산(분포)와는 상관없다고 말할 수 있습니다.
<br/><br/>
그리고, 앞으로 변수간의 합을 많이 가정할 텐데, 독립이 아니라면, 공분산 항이 실제로는 존재한다는 것을 기억해두면 좋습니다.
<br/><br/>
(표본을 통해 통계치를 구할 때, 확률 변수 X1, X2, X3, ... Xn 의 합으로 표현되는 표본평균도 한 예입니다.)

확률 변수의 변환이 왜 중요할까요?
현실과 통계에 가정의 다리를 나주는데에 일단 중요한 역할을 할 것입니다. 많은 경우, 정규 분포를 가정함으로 정규변환 등.

이제는 확률변수의 변화에 따른 확률분포의 변화를 알아봐야 할 것 같습니다.

지금까지 한 것은, 표본공간을 대표하는 Measure, Aggregate, 대표적인 수가 확률변수의 변화에 따라 어떻게 변하는지를 알아본 것이었습니다.

얌얌.


