---
layout: post
title: "F 분포"
author-id: "Cornelii. G. Son"
tags: [study, statistics]
updated: "2020-03-24"
chapter: "3-4"
comments: true
en_title: "F Distribution"
---

## F 분포
<br/>
F분포는 서로 독립인 카이제곱분포를 따르는 두 변수의 비 형태로 확률변수를 가질 때 따르게 되는 분포입니다.
<br/><br/>
$$ \begin{aligned} F = \frac{U/n_1}{V/n_2} \end{aligned}$$
<br/><br/>
여기서 U,V는 각각 자유도가
$$n_1, n_2$$
인 카이제곱 분포를 따르는 확률변수입니다.
<br/><br/>
바로 확률분포를 구해볼까요?
<br/><br/>
f분포의 확률분포는 t분포를 구했을 때와 마찬가지로 아래와 같이 나타낼 수 있고,
<br/><br/>
$$ \begin{aligned} g(f) = \int^{\infty}_{-\infty}\int^{\infty}_{-\infty}\delta(f - \frac{Un_2}{Vn_1})h(u,v)dudv \end{aligned}$$
<br/><br/>
(확률변수 F를 분자에 자유도
$$ n_1$$
의 카이제곱분포를 따르는 U로, 분모를 V로 두었다는 것을 기억해주세요.)
<br/><br/>
$$ \begin{aligned} y = \frac{un_2}{vn_1} \end{aligned}$$
이라하면,
<br/><br/>
$$ \begin{aligned} g(f) &= \int^{\infty}_{0}\int^{\infty}_{0}\delta(f - \frac{un_2}{vn_1})h(u,v)dudv \\ \\
&= \int^{\infty}_{0}\int^{\infty}_{0}\delta(f - y)h(\frac{vn_1y}{n_2},v)dudv \\ \\
&= \int^{\infty}_{0}\int^{\infty}_{0}\delta(f - y)\chi^2_{n_1}(\frac{vn_1y}{n_2})\chi^2_{n_2}(v) \frac{vn_1}{n_2} dydv \\ \\
&=  \int^{\infty}_{0} \{ \int^{\infty}_{0}\delta(f - y)\chi^2_{n_1}(\frac{vn_1y}{n_2})du \} \chi^2_{n_2}(v) \frac{vn_1}{n_2} dv \\ \\
&= \int^{\infty}_{0} \chi^2_{n_1}(\frac{vn_1f}{n_2}) \chi^2_{n_2}(v) \frac{vn_1}{n_2} dv \\ \\
&= \int^{\infty}_{0} \frac{1}{2^{n_1/2}\Gamma(n_1/2)} (\frac{vn_1f}{n_2})^{n_1/2-1} e^{-fvn_1/(2n_2)} \space   \frac{1}{2^{n_2/2}\Gamma(n_2/2)} v^{n_2/2-1}e^{-v/2} \frac{vn_1}{n_2} dv \\ \\
&= \frac{1}{2^{n_1/2}\Gamma(n_1/2)} \frac{1}{2^{n_2/2}\Gamma(n_2/2)} (\frac{n_1}{n_2})^{n_1/2} f^{n_1/2-1} \int^{\infty}_{0} v^{(n_1+n_2)/2-1} e^{-\frac{v}{2}(1+\frac{n_1f}{n_2})}  dv \\ \\
 \end{aligned} $$
<br/><br/>
여기서 감마분포의 형태를 떠올리며,
<br/><br/>
$$ \begin{aligned} \alpha = \frac{n_1+n_2}{2},\space \beta = \frac{2}{1+\frac{n_1}{n_2}f} \end{aligned}$$
라고 해봅시다.
<br/><br/>
$$ \begin{aligned} 
g(f) &= \frac{1}{2^{n_1/2}\Gamma(n_1/2)} \frac{1}{2^{n_2/2}\Gamma(n_2/2)} (\frac{n_1}{n_2})^{n_1/2} f^{n_1/2-1} \int^{\infty}_{0} v^{(n_1+n_2)/2-1} e^{-\frac{v}{2}(1+\frac{n_1f}{n_2})}  dv \\ \\
&= \frac{1}{2^{n_1/2}\Gamma(n_1/2)} \frac{1}{2^{n_2/2}\Gamma(n_2/2)} (\frac{n_1}{n_2})^{n_1/2} f^{n_1/2-1} \int^{\infty}_{0} v^{\alpha-1} e^{-v/\beta}  dv \\ \\
&= \frac{1}{2^{n_1/2}\Gamma(n_1/2)} \frac{1}{2^{n_2/2}\Gamma(n_2/2)} (\frac{n_1}{n_2})^{n_1/2} f^{n_1/2-1} \int^{\infty}_{0} \frac{\beta^{\alpha}\Gamma(\alpha)}{\beta^{\alpha}\Gamma(\alpha)} v^{\alpha-1} e^{-v/\beta} dv \\ \\
&= \frac{1}{2^{n_1/2}\Gamma(n_1/2)} \frac{1}{2^{n_2/2}\Gamma(n_2/2)} (\frac{n_1}{n_2})^{n_1/2} f^{n_1/2-1} \beta^{\alpha}\Gamma(\alpha) \int^{\infty}_{0} \frac{1}{\beta^{\alpha}\Gamma(\alpha)} v^{\alpha-1} e^{-v/\beta} dv \\ \\
&= \frac{1}{2^{n_1/2}\Gamma(n_1/2)} \frac{1}{2^{n_2/2}\Gamma(n_2/2)} (\frac{n_1}{n_2})^{n_1/2} f^{n_1/2-1} \beta^{\alpha}\Gamma(\alpha) \times 1 \\ \\
&= \frac{1}{2^{n_1/2}\Gamma(n_1/2)} \frac{1}{2^{n_2/2}\Gamma(n_2/2)} (\frac{n_1}{n_2})^{n_1/2} f^{n_1/2-1} (\frac{2}{1+\frac{n_1}{n_2}f})^{(n_1+n_2)/2}\Gamma(\frac{n_1+n_2}{2}) \\ \\
&= \frac{\Gamma(\frac{n_1+n_2}{2})(n_1/n_2)^{n_1/2}}{\Gamma(n_1/2)\Gamma(n_2/2)} f^{n_1/2-1} 2^{-(n_1+n_2)/2} 2^{(n_1+n_2)/2} (1+\frac{n_1}{n_2}f)^{-(n_1+n_2)/2} \\ \\
&= \frac{\Gamma(\frac{n_1+n_2}{2})(n_1/n_2)^{n_1/2}}{\Gamma(n_1/2)\Gamma(n_2/2)} f^{n_1/2-1} (1+\frac{n_1}{n_2}f)^{-(n_1+n_2)/2} \\ \\
 \end{aligned} $$
<br/><br/>
이렇게 F분포가 유도되었습니다.
<br/><br/>
다시 강조하면,
<br/><br/>
$$ 자유도: n_1$$
인 카이제곱분포를 따르는 확률변수가 분자
<br/><br/>
$$ 자유도: n_2$$
인 카이제곱분포를 따르는 확률변수가 분모
<br/><br/>
로 구성된 확률변수 F에 대해 구한 것입니다.
<br/><br/>
그러면, 확률분포까지 구해본 확률변수 F를 어떻게 활용할 수 있을 까요?
<br/><br/>
F의 정의에 따라 카이제곱분포를 따르는 두 확률변수를 생각해보면 됩니다.
<br/><br/>
혹시, 
<br/><br/>
$$\begin{aligned} \frac{(n-1)S^2}{\sigma^2} \end{aligned}$$
이 자유도가 n-1인 카이제곱분포를 따른 다는 것 기억하시나요?
<br/><br/>
두 모집단이 있고 각각
$$ \sigma_1^2, \sigma_2^2$$
의 모분산을 따른다고 가정해봅시다.
<br/><br/>
그리고, 각각의 모집단에서 
$$ n_1, n_2$$
개의 표본을 뽑을 때,
<br/><br/>
각각의 표본분산이
$$ S_1^2, S_2^2 $$
라고 해봅시다.
<br/><br/>
그러면, 
<br/><br/>
$$\begin{aligned} \frac{(n_1-1)S_1^2}{\sigma_1^2} \end{aligned}$$
은 자유도가 
$$ n_1-1$$
인 카이제곱분포를, 
<br/><br/>
$$\begin{aligned} \frac{(n_2-1)S_2^2}{\sigma_2^2} \end{aligned}$$
은 자유도가 
$$ n_2-1$$
인 카이제곱분포를 각각 따르게됩니다.
<br/><br/>
카이제곱분포를 따르는 두 확률변수가 나왔으니 확률변수 F를 만들 수 있겠죠? 밑첨자가 1인 확률변수를 분자에 두겠습니다. 그러면,
<br/><br/>
$$\begin{aligned} F = \frac{\frac{(n_1-1)S_1^2}{\sigma_1^2 (n_1-1)}}{\frac{(n_2-1)S_2^2}{\sigma_2^2 (n_2-1)}} = \frac{S_1^2/\sigma_1^2}{S_2^2/\sigma_2^2} = \frac{S_1^2\sigma_2^2}{S_2^2\sigma_1^2}
\end{aligned}$$
<br/><br/>
위와 같이 주어진 확률변수 F는 
<br/><br/>
자유도
$$ n_1-1, n_2-1$$
로 표현된 F-분포를 따르게 될 것입니다.
<br/><br/>
<br/><br/>


## F분포 in python

```python
import scipy.stats as sps

## F distribution
dfn, dfd = 11,9 ## degree of freedom of nominator and denominator, respectively.

f = sps.f(dfn, dfd, loc=0, scale=1)

#### mean & Variance
mean, var = f.mean(), f.var()

#### get some values from F-distribution
some_values = f.rvs(size=10, random_state=12345)
```