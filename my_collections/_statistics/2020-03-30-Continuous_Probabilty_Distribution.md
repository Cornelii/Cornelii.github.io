---
layout: post
title: "연속확률분포 균일분포와 정규분포"
author-id: "Cornelii. G. Son"
tags: [study, statistic]
updated: "2020-03-30"
chapter: "3-1"
en_title: "Continuous Probability Distribution: Uniform & Normal Distribution"
---

## 연속확률분포
연속확률분포는 확률변수를 특정한 길이의 직선 내의 무수한 점에 대응 시킬 수 있는 실수인 확률변수로 나타낸 확률분포입니다.
<br/><br/>
중요한 것은 연속확률분포 값 자체가 확률을 의미하지는 않는다는 것입니다.
<br/><br/>
<br/><br/>

## 균일분포
<br/>
균일 분포는 확률변수의 `구간`에서 같은 값을 가지는 확률분포입니다. 즉 `구간`에 의해 값이 결정되게 되죠.
<br/><br/>
$$ \begin{aligned} f(x) = \frac{1}{B-A} \end{aligned} \space \space \space where \space X \in (A,B) $$
<br/><br/>
균일 분포의 기댓값과 분산은 아래와 같습니다.
<br/><br/>
$$ \begin{aligned} \mu_X = \int_A^Bx\frac{1}{B-A}dx = \frac{1}{B-A}\int_A^Bxdx = \frac{A+B}{2} \end{aligned} $$
<br/><br/>
$$ \begin{aligned} \sigma_x^2 = \int^B_A(x - \frac{A+B}{2})^2\frac{1}{B-A}dx = \frac{(B-A)^2}{12}\end{aligned} $$
<br/><br/>

#### 균일분포의 적률생성함수
<br/>
균일분포의 적률생성함수는 아래와 같이 구할 수 있습니다.
<br/><br/>
$$ \begin{aligned} M_X(t) = \int^B_Ae^{xt}\frac{1}{B-A} dx= \frac{1}{t(B-A)}(e^{Bt} - e^{At})  \end{aligned} $$
<br/><br/>
위 식으로 적률(Moment)를 구하기 힘들어 보인다면, 지수함수의 다항식(Polynomial) 형태를 생각하면서 접근하시면 될 것 같습니다.
<br/><br/>
<br/><br/>

## 정규분포
<br/>
가장 중요한 분포를 하나 꼽으라면 당연히 정규분포 (Normal Distribution or Gaussian Distribution)일 것입니다.
<br/><br/>
좌우 대칭의 종모양을 가지고 있고, 평균과 분산에 의에 모양이 결정됩니다. 식의 형태는 아래와 같습니다.
<br/><br/>
$$ \begin{aligned} n(x;\mu, \sigma) = \frac{1}{\sqrt{2\pi}\sigma}exp({-\frac{(x-\mu)^2}{2\sigma^2}}) \space  \end{aligned} $$
<br/><br/>
$$ -\infty < x < \infty $$
<br/><br/>
평균과 분산은 계산해보면, 당연히
$$\mu, \sigma^2$$
가 나오게 되겠지요.
<br/><br/>

#### 정규분포의 적률생성함수
<br/>
그러면 정규분포의 적률생성함수를 구해보도록 하겠습니다.
<br/><br/>
$$ \begin{aligned} M_X(t) &= \int^\infty_{-\infty}exp(xt) \frac{1}{\sqrt{2\pi}\sigma}exp({-\frac{(x-\mu)^2}{2\sigma^2}})dx \\ \\
&= \int^\infty_{-\infty}\frac{1}{\sqrt{2\pi}\sigma}exp({-\frac{(x-\mu)^2}{2\sigma^2}}+xt)dx \\ \\
&= \int^\infty_{-\infty}\frac{1}{\sqrt{2\pi}\sigma}exp({-\frac{(x-\mu)^2-2\sigma^2tx}{2\sigma^2}})dx \\ \\
&= \int^\infty_{-\infty}\frac{1}{\sqrt{2\pi}\sigma}exp({-\frac{x^2-2\mu x+\mu^2-2\sigma^2tx}{2\sigma^2}})dx \\ \\
&= \int^\infty_{-\infty}\frac{1}{\sqrt{2\pi}\sigma}exp({-\frac{x^2-2(\mu +\sigma^2t)x+(\mu +\sigma^2t)^2 - (\mu +\sigma^2t)^2 + \mu^2}{2\sigma^2}})dx \\ \\
&= \int^\infty_{-\infty}\frac{1}{\sqrt{2\pi}\sigma}exp({-\frac{(x-(\mu +\sigma^2t))^2 - (\mu +\sigma^2t)^2 + \mu^2}{2\sigma^2}})dx \\ \\
&= \int^\infty_{-\infty}\frac{1}{\sqrt{2\pi}\sigma}exp({-\frac{(x-(\mu +\sigma^2t))^2}{2\sigma^2}})exp(\frac{ (\mu +\sigma^2t)^2 - \mu^2}{2\sigma^2})dx \\ \\
&= exp(\frac{ \mu^2 + 2\mu \sigma^2t+ \sigma^4t^2 - \mu^2}{2\sigma^2})\int^\infty_{-\infty}\frac{1}{\sqrt{2\pi}\sigma}exp({-\frac{(x-(\mu +\sigma^2t))^2}{2\sigma^2}})dx \\ \\
&= exp(\frac{ 2\mu \sigma^2t+ \sigma^4t^2 }{2\sigma^2}) = exp(\mu t+ \frac{\sigma^2t^2}{2})
\end{aligned} $$
<br/><br/>
나름 깔끔하게 나오게 되는군요. 정규분포가 짱이네.. 가우스님... 
<br/><br/>
여기서 적률생성함수를 이용해서 서로 독립인 서로 다른 정규분포를 따르는 두 확률변수의 합에 대해서 잠깐 살펴볼까 합니다.
<br/><br/>
$$ Y = X_1 + X_2 $$
<br/><br/>
여기서
$$ X_1 $$
는
$$ n(x_1;\mu_1,\sigma_1) $$
를 따르고,
$$ X_2 $$
는
$$ n(x_2;\mu_2,\sigma_2) $$
를 따른다고 해봅시다.
<br/><br/>
서로 독립인 확률변수의 합을 적률생성함수에서 나타내면 어떻게 되는지 기억하시나요?(Ch 1-5 확률변수 변환과 적률생성함수)
<br/><br/>
$$M_{X_1 + X_2}(t) = M_{X_1}(t) \times M_{X_2}(t)$$
<br/><br/>
위 처럼 곱의 형태가 되게 됩니다. 이를 그대로 적용하면,
<br/><br/>
$$ \begin{aligned} M_Y(t) = M_{X_1}(t) \times M_{X_2}(t) &= exp(\mu_1t+\frac{\sigma_1^2t^2}{2}) \times exp(\mu_2t+\frac{\sigma_2^2t^2}{2}) \\ \\
&= exp((\mu_1+\mu_2)t+\frac{(\sigma_1^2+\sigma_2^2)t^2}{2})
\end{aligned} $$
<br/><br/>
여기서, 
$$ \mu_1 + \mu_2 = \mu_Y $$
<br/>
$$ \sigma_1^2 + \sigma_2^2 = \sigma_Y^2$$
이라 하면, 최종적으로
<br/><br/>
$$ \begin{aligned} exp(\mu_Yt+\frac{\sigma_Y^2t^2}{2})  \end{aligned} $$
<br/><br/>
$$ \mu_Y $$
와
$$ \sigma_Y^2 = $$
를 따르는 또 다른 정규분포가 되는 걸 알 수 있습니다.
<br/><br/>
정리하면, 서로 독립인 각각 정규분포를 따르는 확률변수의 합은 또 정규분포를 따르게 된다는 것입니다. 2개도 되니, 3개, ... n개도 되겠지요.
<br/><br/>
<br/><br/>

## 표준정규분포
<br/>
확률 변수에 적절한 계산을 더해 확률분포를 변화시킬 수 있는 것을 알고 있습니다.
<br/><br/>
정규분포를 따르는 확률변수에 대해, 평균 0과 분산이 1인 정규분포를 따르도록 확률변수를 변화시킬 수 있습니다. 그리고, 이 확률분포를 표준정규분포라고 합니다.
<br/><br/>
확률변수 X가 
$$n(x;\mu,\sigma)$$
인 정규분포를 따른다고 가정하고,
<br/><br/>
새로운 확률변수 Z를 아래와 같이 나타내 보겠습니다.
<br/><br/>
$$ Z = aX + b$$
<br/><br/>
여기서 a와 b는 상수입니다.
<br/><br/>
확률분포의 변화 기억나시나요? 여기서 핵심은 확률이 같다는거!
<br/><br/>
$$ n(x)dx = g(z)dz  $$
<br/><br/>
$$ g(z) = n(x)\frac{dx}{dz} $$
<br/><br/>
$$ \begin{aligned} g(z) &= \frac{1}{\sqrt{2\pi}\sigma}exp({-\frac{(x-\mu)^2}{2\sigma^2}})\frac{1}{a} \\ \\
&= \frac{1}{\sqrt{2\pi}\sigma}exp({-\frac{(\frac{z-b}{a}-\mu)^2}{2\sigma^2}})\frac{1}{a} \\ \\
&= \frac{1}{\sqrt{2\pi}\sigma a}exp({-\frac{(z-b-a\mu)^2}{2a^2\sigma^2}})
\end{aligned} $$
<br/><br/>
우리가 하고 싶은 것은 위의 확률분포가 평균은 0, 분산은 1을 가지게 하고 싶은 것이죠. 그러기 위해서 정규분포식과 비교해서 볼 때, 
<br/><br/>
$$ a\sigma = 1$$
,
$$ -b -a\mu = 0$$
이 되어야 할 것입니다. 
<br/><br/>
위 두 식을 통해,
<br/><br/>
$$ \begin{aligned} a = \frac{1}{\sigma}, \space b = -\frac{\mu}{\sigma} \end{aligned} $$
가 되는 것을 알 수 있습니다.
<br/><br/>
$$ \begin{aligned} Z = aX + b = \frac{X-\mu}{\sigma} \end{aligned} $$
<br/><br/>
이런 확률변수의 변환을 통해 표준 정규분포를 얻어 낼 수 있네요.
<br/><br/>

#### 표준정규분포의 적률생성함수
<br/>
위에서 구한 식에 평균에 0, 분산에 1을 대입해 쉽게 구해낼 수 있습니다.
<br/><br/>

$$ \begin{aligned} exp(\mu t+ \frac{\sigma^2t^2}{2}) = exp(\frac{t^2}{2})  \end{aligned} $$
<br/><br/>



