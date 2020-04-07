---
layout: post
title: "감마, 지수, 그리고 카이제곱분포"
author-id: "Cornelii. G. Son"
tags: [study, statistic]
updated: "2020-03-22"
chapter: "3-2"
en_title: "Gamma, Exponential, and Chi-square Distribution"
---

## I. 감마분포
<br/>
연속확률분포 중 하나인 감마분포는 감마함수에서 자연스럽게 유도됩니다. 살펴봅시닷!

<br/><br/>

#### i. 감마함수
<br/>
감마함수의 형태는 다음과 같습니다.
<br/><br/>
$$ \begin{aligned} \Gamma(\alpha) = \int^\infty_0x^{\alpha-1}e^{-x}dx \end{aligned} $$
<br/><br/>
이 함수를 적분하다보면 재밌는 성질을 발견할 수 있는데요.
<br/><br/>
$$ \begin{aligned} \Gamma(\alpha) = \int^\infty_0x^{\alpha-1}e^{-x}dx 
&= -e^{-x}x^{\alpha-1} |^{\infty}_0 + (\alpha-1) \int^\infty_0x^{\alpha-2}e^{-x}dx \\ \\
&= (\alpha-1) \int^\infty_0x^{\alpha-2}e^{-x}dx \\ \\
&= (\alpha-1)\Gamma(\alpha-1)
\end{aligned} $$
<br/><br/>
게다가 감마함수의
$$ \alpha $$
에 1을 넣고 값을 구해보면,
<br/><br/>
$$ \begin{aligned} \Gamma(1) = \int^\infty_0e^{-x}dx = -e^{-x} |^\infty_0 = 0 - (-1) = 1    \end{aligned} $$
<br/><br/>
1이 되는 것을 알 수 있습니다.
<br/><br/>
$$ \Gamma(1) = 1$$
<br/>
$$ \Gamma(2) = 1 \times \Gamma(1) = 1$$
<br/>
$$ \Gamma(3) = 2 \times \Gamma(2) = 2$$
<br/>
$$ \Gamma(4) = 3 \times \Gamma(3) = 3 \times 2 = 6 $$
<br/>
$$ \Gamma(n) = (n-1) \times \Gamma(n-2) = (n-1) \times (n-2) \times ... \times \Gamma(1) = (n-1)! $$
<br/><br/>
마지막 처럼 팩토리얼(Factorial) 연산을 감마함수로 나타낼 수 있습니다.
<br/><br/>
한 가지 더! 감마함수에 0.5를 넣은 값
<br/>
$$ \begin{aligned} \Gamma(1/2) \end{aligned}$$
를 구해볼 수 있습니다.
<br/><br/>
감마함수 
$$ \begin{aligned} \Gamma(\alpha) = \int^\infty_0x^{\alpha-1}e^{-x}dx \end{aligned} $$
에서, 변수 x를 아래의 관계를 가진 y로 변환시켜 봅시다.
<br/>
$$ y = \sqrt{2x}$$
<br/><br/>
$$ \begin{aligned} \frac{dy}{dx} = \frac{1}{\sqrt{2x}} = \frac{1}{y} \end{aligned}$$
,
$$ \begin{aligned} x = \frac{y^2}{2} \end{aligned}$$
이기에,
<br/><br/>
$$ \begin{aligned} \Gamma(\alpha) = \int^\infty_0(\frac{y^2}{2})^{\alpha-1}e^{-y^2/2} y \frac{1}{y} dx = \int^\infty_0(\frac{y^2}{2})^{\alpha-1}e^{-y^2/2} y \frac{dy}{dx} dx
&= \int^\infty_0(\frac{y^2}{2})^{\alpha-1}e^{-y^2/2} y dy \\ \\
&= 2^{1-\alpha}\int^\infty_0y^{2\alpha-1}e^{-y^2/2}dy
\end{aligned} $$
<br/><br/>
이렇게 됩니다. 이제 
$$ \alpha $$
에 0.5를 넣으면,
<br/><br/>
$$ \begin{aligned} \Gamma(1/2) = \sqrt{2}\int^\infty_0e^{-y^2/2} dy = \frac{2\sqrt{\pi}}{\sqrt{2\pi}}\int^\infty_0e^{-y^2/2} dy = 2\sqrt{\pi} \times \frac{1}{\sqrt{2\pi}}\int^\infty_0e^{-y^2/2} dy
\end{aligned} $$
<br/><br/>
우변의 맨 오른쪽 항은 형태가 익숙한 느낌이 듭니다! 바로, 평균이 0이고 분산이 1인 표준정규분포를 오른쪽 반만 적분한 0.5의 확률 입니다! 그러므로,
<br/><br/>
$$ \begin{aligned} \Gamma(1/2) = 2\sqrt{\pi} \times \frac{1}{2} = \sqrt{\pi} \end{aligned}$$
<br/><br/>
이렇게 됩니다. 와웃.
<br/><br/>

#### ii. 감마분포
<br/>
감마분포는 어떻게 구해낼 수 있을 까요?
<br/><br/>
이번에도 감마함수의 형태를 변화시켜 봅시다.
<br/><br/>
$$ \begin{aligned} \Gamma(\alpha) = \int^\infty_0x^{\alpha-1}e^{-x}dx \end{aligned} $$
에서,
$$ \begin{aligned} x = \frac{y}{\beta} \end{aligned} $$
라고 치환해봅시다.
<br/><br/>
$$ \begin{aligned} \frac{dy}{dx} = \beta \end{aligned} $$
이기 때문에,
<br/><br/>
$$ \begin{aligned} \Gamma(\alpha) = \int^\infty_0(\frac{y}{\beta})^{\alpha-1}e^{-y/\beta}\beta\frac{1}{\beta}dx = \int^\infty_0(\frac{y}{\beta})^{\alpha-1}e^{-y/\beta}\frac{1}{\beta}\frac{dy}{dx}dx &= \int^\infty_0(\frac{y}{\beta})^{\alpha-1}e^{-y/\beta}\frac{1}{\beta} dy \\ \\
&= \frac{1}{\beta^\alpha}\int^\infty_0(y)^{\alpha-1}e^{-y/\beta} dy
\end{aligned} $$
<br/><br/>
이제 위식에서 양변을 감마함수로 나누어 봅시다.
<br/><br/>
$$ \begin{aligned} 1 &= \frac{1}{\beta^\alpha\Gamma(\alpha)}\int^\infty_0(y)^{\alpha-1}e^{-y/\beta} dy
\end{aligned} $$
<br/><br/>
물론 감마함수는 0이지 말아야겠죠.
<br/><br/>
적분했더니 1이 나왔습니다. y는 dummy variable이니 x로 바꿔주면, 아래와 같은 확률분포를 얻어낼 수 있습니다.
<br/><br/>
$$ \begin{aligned} \frac{1}{\beta^\alpha\Gamma(\alpha)}(x)^{\alpha-1}e^{-x/\beta}
\end{aligned} $$
<br/><br/>
이것이 바로 감마분포입니다. 유의할 점이 있다면, 대칭이 아니고, 확률변수 x의 범위가 0부터 양의 무한대에 있는 확률분포라는 것입니다.
<br/><br/>
또 한가지, 이 감마분포는 조절할 수 있는 파라미터가
$$ \alpha, \beta $$
두 개가 있습니다.
<br/><br/>

#### iii. 감마분포의 기댓값과 분산
감마분포의 기댓값과 분산을 구해보겠습니다.
<br/><br/>
먼저 기댓값을 구해보면,
<br/><br/>
$$ \begin{aligned} E[x] &= \int^\infty_0\frac{1}{\beta^\alpha\Gamma(\alpha)}xx^{\alpha-1}e^{-x/\beta}dx \\ \\
&= \frac{1}{\beta^\alpha\Gamma(\alpha)}\int^\infty_0x^{\alpha}e^{-x/\beta}dx
\end{aligned} $$
<br/><br/>
여기서 우변의 
$$ \begin{aligned} \int^\infty_0x^{\alpha}e^{-x/\beta}dx
\end{aligned} $$
만 따로 놓고 정적분을 풀어보면, (Integrate by Part)
<br/><br/>
$$ \begin{aligned} \int^\infty_0x^{\alpha}e^{-x/\beta}dx &=
-\beta e^{-x/\beta}x^\alpha |^\infty_0 + \alpha \beta \int^\infty_0x^{\alpha-1}e^{-x/\beta}dx \\ \\
&= \alpha \beta \int^\infty_0x^{\alpha-1}e^{-x/\beta}dx
\end{aligned} $$
<br/><br/>
여기서 처음의 
$$ \begin{aligned} \int^\infty_0x^{\alpha}e^{-x/\beta}dx
\end{aligned} $$
이 항을 
$$ G(\alpha, \beta)$$
라고 표현 하면, 위의 식을 통해,
<br/><br/>
$$  G(\alpha, \beta) = \alpha \beta G(\alpha-1, \beta) $$
<br/><br/>
가 성립하는 것을 알 수 있습니다.
<br/><br/>
$$ \alpha $$
가 0이 될 때까지 위 식을 반복하면!
<br/><br/>
$$ \begin{aligned} G(\alpha, \beta) = \alpha \beta G(\alpha-1, \beta) &= \alpha (\alpha - 1) \beta^2 G(\alpha-2,\beta)... \\ \\
&= \alpha ! \beta^\alpha G(0, \beta) \end{aligned} $$
<br/><br/>
가 됩니다. 그렇다면, 
$$  G(0, \beta) $$
는 어떻게 될까요? 식으로 바로 대입해서 구해보면,
<br/><br/>
$$ \begin{aligned} G(0, \beta) = \int^\infty_0e^{-x/\beta}dx = -\beta e^{-y/\beta}|^\infty_0 = \beta
\end{aligned} $$
<br/><br/>
결국, 
$$ G(\alpha, \beta) = \alpha ! \beta^{\alpha + 1}$$
이 됩니다.
<br/><br/>
이것을 다시 위의 기댓값식에 대입해 볼까요?
<br/><br/>
$$ \begin{aligned} E[x] = \frac{1}{\beta^\alpha\Gamma(\alpha)}\int^\infty_0x^{\alpha}e^{-x/\beta}dx = \frac{1}{\beta^\alpha\Gamma(\alpha)}G(\alpha, \beta) &= \frac{1}{\beta^\alpha\Gamma(\alpha)}\alpha ! \beta^{\alpha+1} \\ \\
&= \frac{\alpha!}{(\alpha-1)!} \beta \\ \\ 
&=  \alpha \beta \end{aligned}$$
<br/><br/>
참 고맙게도 단순한 형태를 띄네요.
<br/><br/>
<br/><br/>
이어서 감마분포의 분산을 구해보도록 하죠.
<br/><br/>
$$ \begin{aligned} V[x] = E[x^2] - \mu_X^2 = \frac{1}{\beta^\alpha\Gamma(\alpha)}\int^\infty_0x^{\alpha+1}e^{-x/\beta}dx - (\alpha \beta)^2\end{aligned}$$
<br/><br/>
위에서의 식을 이용해서,
<br/><br/>
$$ \begin{aligned} V[x] = \frac{1}{\beta^\alpha\Gamma(\alpha)}G(\alpha+1, \beta) - (\alpha \beta)^2 &= \frac{1}{\beta^\alpha\Gamma(\alpha)}(\alpha+1)\beta G(\alpha, \beta) - (\alpha \beta)^2 \\ \\
&= \frac{1}{\beta^\alpha\Gamma(\alpha)}(\alpha+1)\beta \alpha ! \beta^{\alpha + 1} - (\alpha \beta)^2 \\ \\
&= (\alpha + 1)\alpha \beta^2 - \alpha^2\beta^2 \\ \\
&= \alpha^2\beta^2 + \alpha \beta^2 -\alpha^2 \beta^2 \\ \\
&= \alpha \beta^2 \end{aligned}$$
<br/><br/>
분산도 감사하게도 아주 간단한 형태로 나오게 됩니다. 휴우
<br/><br/>
<br/><br/>

#### iv. 감마분포의 적률생성함수
이제 감마분포의 적률생성함수를 구해봐야겠죠? 적률생성함수의 정의에 따라
<br/><br/>
$$ \begin{aligned} M_X(t) = \frac{1}{\beta^\alpha\Gamma(\alpha)}\int^\infty_0e^{xt}x^{\alpha-1}e^{-x/\beta}dx &= \frac{1}{\beta^\alpha\Gamma(\alpha)}\int^\infty_0x^{\alpha-1}e^{-x(1/\beta-t)}dx \\ \\
&=  \frac{1}{\beta^\alpha\Gamma(\alpha)}G(\alpha-1,\frac{1}{1/\beta - t}) \\ \\
&= \frac{1}{\beta^\alpha\Gamma(\alpha)}(\alpha -1)!(\frac{1}{1/\beta - t})^{\alpha-1} G(0, \frac{1}{1/\beta - t})
\end{aligned}$$
<br/><br/>
$$ \begin{aligned} G(0, \frac{1}{1/\beta - t}) \end{aligned}$$
는 위에서 적분을 통해 풀었던 것처럼 그대로 따라가면,
$$ \begin{aligned} \frac{1}{1/\beta - t} \end{aligned}$$
이 되는 것을 알 수 있습니다. 최종적으로,
<br/><br/>
$$ \begin{aligned}
M_X(t) = \frac{1}{\beta^\alpha\Gamma(\alpha)}(\alpha -1)!(\frac{1}{1/\beta - t})^{\alpha} = \frac{1}{\beta^\alpha}(\frac{1}{1/\beta - t})^{\alpha} &= \frac{1}{\beta^\alpha}(\frac{\beta}{1- \beta t})^{\alpha} \\ \\
&= (\frac{1}{1-\beta t})^{\alpha}
\end{aligned} $$
<br/><br/>
위와 같이 적률 생성함수가 나오게 됩니다.
<br/><br/>
<br/><br/>

## II. 지수분포
지수분포는 감마분포에서 간단히
$$ \alpha = 1$$
을 대입해서 얻을 수 있고 아래와 같습니다.
<br/><br/>
$$ \begin{aligned} \frac{1}{\beta}e^{-x/\beta} \end{aligned} $$
<br/><br/>

#### i. 지수분포의 기댓값과 분산
지수분포의 기댓값과 분산 역시 앞에서 구한 감마분포의 기댓값과 분산을 이용하면 바로 구할 수 있겠네요.
<br/><br/>
$$ \begin{aligned} E[X] = \alpha \beta = \beta  \end{aligned}$$
<br/><br/>
$$ \begin{aligned} V[X] = \alpha \beta^2 = \beta^2  \end{aligned}$$
<br/><br/>
<br/><br/>

#### ii. 지수분포의 적률생성함수
지수분포의 적률생성함수 역시,
<br/><br/>
$$ \begin{aligned} M_X(t) = (\frac{1}{1-\beta t})^{\alpha} =  (\frac{1}{1-\beta t}) \end{aligned}$$
<br/><br/>
바로 구할 수 있습니다.
<br/><br/>
<br/><br/>


## III. 카이 제곱 분포
<br/>
카이제곱 분포도 지수 분포와 마찬가지로 감마분포를 통해 얻을 수 있는데요.
<br/><br/>
감마분포에 
$$ \alpha = \nu/2, \beta = 2 $$
를 대입하면 됩니다.
<br/><br/>
$$ \begin{aligned} \frac{1}{2^{\nu/2}\Gamma(\nu/2)}(x)^{\nu/2-1}e^{-x/2}
\end{aligned} $$
<br/><br/>
여기서 
$$ \nu $$
는 자유도 (Degree of Freedom)이라고 부르는데, 좀 더 정확히 말하면 카이제곱분포의 자유도라고 해야겠군요.
<br/><br/>
역학이나 기구학 등 여러 학문에서 쓰이는 용어이지만, 여기서는 일단 하나의 조절할 수 있는 파라미터라고 생각하고 넘어가봅시다.
<br/><br/>
<br/><br/>

#### i. 카이 제곱 분포의 기댓값과 분산
<br/>
카이 제곱 분포의 기댓값과 분산도 쏵쏵 구해볼까요. 앞 선 감마분포를 참고해서.
<br/><br/>
$$ \begin{aligned} E[X] = \alpha \beta = \nu  \end{aligned}$$
<br/><br/>
$$ \begin{aligned} V[X] = \alpha \beta^2 = 2\nu  \end{aligned}$$
<br/><br/>

#### ii. 카이 제곱 분포의 적률생성함수
$$ \begin{aligned} M_X(t) = (\frac{1}{1-\beta t})^{\alpha} =  (\frac{1}{1-2t})^{\nu/2} \end{aligned}$$

<br/><br/>
여기서 카이제곱 분포의 중요한 성질을 2가지만 짚어보려 하는데요. 왜 카이`제곱`분포라고 이름이 붙게되었는지도 알 수 있습니다.
<br/><br/>
적률생성함수의 성질 기억하시나요?
<br/><br/>
서로다른 확률 변수가 서로 독립일 때, 그 확률변수들의 합은 적률생성함수의 곱으로 표현되게 됩니다.
<br/><br/>
서로 독립인
$$ X_1, X_2, ... ,X_n$$
이 있을 때,
<br/><br/>
$$ Y = X_1 + X_2 + ... , X_n $$
인 Y에 대해 적률생성함수를 구하게 되면,
<br/><br/>
$$ M_Y(t) = M_{X_1}(t) M_{X_2}(t) ... M_{X_n}(t)$$
<br/><br/>
곱의 형태로 바뀝니다. 
<br/><br/>
카이제곱 분포에 적용해볼까요.
<br/><br/>
각각 자유도가
$$ \nu_1, \nu_2, ... , \nu_3$$
이고 각각 서로 독립인 카이제곱분포를 따르는 확률변수
$$ \chi_1, \chi_2, ... , \chi_n $$
이 있다고 해봅시다.
<br/><br/>
이들의 합으로 나타낸 새로운 확률변수 Y
<br/><br/>
$$ Y = \chi_1 + \chi_2 + ... + \chi_n $$
의 적률생성함수를 구해보면
<br/><br/>
$$ \begin{aligned} M_Y(t) &= M_{\chi_1}(t)M_{\chi_2}(t) ... M_{\chi_3}(t) \\ \\ 
&= (\frac{1}{1-2t})^{\nu_1/2} (\frac{1}{1-2t})^{\nu_2/2} ... (\frac{1}{1-2t})^{\nu_n/2} \\ \\
&= (\frac{1}{1-2t})^{(\nu_1 + \nu_2 + ... +\nu_n)/2}
\end{aligned}$$
<br/><br/>
마지막 최종형태는 자유도가
$$ \nu_1 + \nu_2 +... +\nu_n $$
인 카이제곱분포의 적률생성함수와 동일한 것을 알 수 있습니다.
<br/><br/>
적률생성함수의 유일성 정리(Uniqueness Theorem)에 의해서 Y는 위 카이제곱 분포를 따르게 되는 것을 확정지을 수 있습니다.
<br/><br/>
정리하면, 서로 독립인 카이제곱분포를 따르는 확률변수들을 더한 새로운 확률변수는 각각의 자유도를 다 더한 카이제곱분포를 따르게 된다는 것입니다.
<br/><br/>
<br/><br/>
두 가지라 하였으니, 한 가지만 더 생각해보죠.
<br/><br/>
평균과 분산이
$$ \mu, \sigma^2$$
인 정규분포를 따르는 확률변수 X가 있다고 할 때,
<br/><br/>
$$ Z = \frac{X-\mu}{\sigma} $$
는 표준정규분포를 따르게 되는 것을 이전에 확인하였습니다. 
<br/><br/>
그렇다면,
$$ \begin{aligned} Y = (\frac{X-\mu}{\sigma})^2 \end{aligned} $$
는 어떤 분포를 따르게 될까요?
<br/><br/>
먼저,
$$ y = z^2$$
으로 나타낼 수 있는 걸 볼 수 있습니다.
<br/><br/>
 y의 분포를 그대로 구해보면, (z는 평균이 0이고, 분산이 1인 표준정규분포를 따르죠.)
<br/><br/>
$$ \begin{aligned} g(y) = n(z)|\frac{d(\sqrt{y})}{dy}| + n(z)|\frac{d(-\sqrt{y})}{dy}| 
&= \frac{1}{\sqrt{2\pi}}e^{-z^2/2}(\frac{1}{2\sqrt{y}}+\frac{1}{2\sqrt{y}}) \\ \\
&= \frac{1}{\sqrt{2\pi}}e^{-y/2}\frac{1}{\sqrt{y}} \\ \\
&= \frac{1}{y^{1/2}2^{1/2}\Gamma(1/2)}e^{-y/2}
\end{aligned} $$
<br/><br/>
마지막에는 자유도가 1인 카이제곱분포가 된 것을 알 수 있습니다.
<br/><br/>
이것으로 
$$ \mu, \sigma^2$$
인 정규분포를 따르는 확률변수 X가 있을 때,
<br/><br/>
$$ \begin{aligned} Y = (\frac{X-\mu}{\sigma})^2 \end{aligned} $$
<br/><br/>
위와 같이 정의된 확률 변수 Y는 자유도가 1인 카이제곱 분포를 따르게 되는 것이 보여졌습니다.
<br/><br/>
<br/><br/>
정리하면, 감마분포, 지수분포, 카이제곱분포에 대해 살펴보았고
<br/><br/>
1. 서로 독립인 카이제곱 분포를 따르는 `확률변수의 합으로 표현된` 확률변수는 각 자유도를 더한 카이제곱 분포를 따르게 된다는 것
<br/><br/>
2. 위에서 보인 그 특정한 확률변수는 자유도가 1인 카이제곱 분포를 따른 다는 것!
<br/><br/>
<br/><br/>
통계 검정에 적용되는 점을 생각해볼까요? 모집단이 정규분포를 따른다고 가정하고 모집단의 평균과 분산이 정해지면(정확하든, 아니든) n개의 표본을 뽑는다 할 때,
<br/><br/>
$$ \begin{aligned} Y = \sum^n_i(\frac{X_i-\mu}{\sigma})^2 \end{aligned}$$
<br/><br/>
는 자유도가 n인 카이제곱 분포를 따르게 될 것이라고 생각할 수 있습니다.
<br/>
(각 자유도가 1인 카이제곱 분포를 따르고 n개를 더했으니, 자유도가 n인 카이제곱 분포를 따르게 됨.)
<br/><br/>
<br/><br/>

## IV. 표본분산의 분포와 카이제곱분포
<br/>
표본 평균의 분포는 이미 Ch1_6에서 살펴보았습니다. 평균만으로는 표본집합을 대표하는데 부족하기에 분산이 필요할 것입니다. 이번에는 표본분산의 분포에 대해 알아봅시다.
아래의 식을 살펴봅시다. 
<br/><br/>
$$ \begin{aligned} \sum^n_{i=1}(X_i - \mu)^2 &= \sum^n_{i=1}(X_i - \overline{X} + \overline{X} - \mu)^2 \\ \\
&=  \sum^n_{i=1}\{(X_i - \overline{X})^2 + (\overline{X} - \mu)^2 + 2(X_i - \overline{X})(\overline{X} - \mu)\} \\ \\
&= \sum^n_{i=1}(X_i - \overline{X})^2 + \sum^n_{i=1}(\overline{X} - \mu)^2 + 2(\overline{X} - \mu)\sum^n_{i=1}(X_i - \overline{X}) \\ \\
&= \sum^n_{i=1}(X_i - \overline{X})^2 + \sum^n_{i=1}(\overline{X} - \mu)^2 + 2(\overline{X} - \mu)(n\overline{X} - n\overline{X}) \\ \\
&= \sum^n_{i=1}(X_i - \overline{X})^2 + n(\overline{X} - \mu)^2
 \end{aligned}$$
<br/><br/>
$$ \begin{aligned} \sum^n_{i=1}(X_i - \mu)^2
&= \sum^n_{i=1}(X_i - \overline{X})^2 + n(\overline{X} - \mu)^2
 \end{aligned}$$
<br/><br/>
$$ \begin{aligned} \sum^n_{i=1}\frac{(X_i - \mu)^2}{\sigma^2}
&= \sum^n_{i=1}\frac{(X_i - \overline{X})^2}{\sigma^2} + \frac{n(\overline{X} - \mu)^2}{\sigma^2}
 \end{aligned}$$
<br/><br/>
좌변은 자유도 n의 카이제곱분포를 따르고, 우변의 오른쪽항은 표본평균의 정규화된 확률변수의 제곱이므로 자유도 1의 카이제곱 분포를 따르게 됩니다.
<br/><br/>
표본분포의 분산을 아래와 같이 정의하고 우변의 우측 항을 정규분포 Z로 나타내면
<br/><br/>
$$ \begin{aligned} S^2 =\frac{1}{n-1}\sum^n_{i=1}(X_i - \overline{X})^2 \end{aligned}$$
<br/><br/>
위 식은 다음과 같이 나타낼 수 있습니다.
<br/><br/>
$$ \begin{aligned} \sum^n_{i=1}\frac{(X_i - \mu)^2}{\sigma^2}
&= \frac{(n-1)S^2}{\sigma^2} + Z^2
 \end{aligned}$$
<br/><br/>
이제 좌변과 우변의 적률생성함수를 생각해봅시다.
<br/><br/>
먼저 좌변은, 위의 i.카이제곱분포의 기댓값과 분산에서 다뤘듯이 자유도가 n인 카이제곱 분포를 따르게 되니 적률생성함수는 다음과 같이 됩니다.
<br/><br/>
$$ \begin{aligned} M_{우변}(t) = M_{\sum^n_{i=1}\frac{(X_i - \mu)^2}{\sigma^2}}(t) = (\frac{1}{1-2t})^{n/2} \end{aligned} $$
<br/><br/>
이제, 우변의 적률생성함수를 간단히 구해봅시다.
<br/><br/>

$$ \begin{aligned} M_{좌변}(t) = M_{\frac{(n-1)S^2}{\sigma^2} + Z^2}(t) \end{aligned} $$
<br/><br/>
여기서 
$$ Z^2 $$
과
$$ \frac{S^2(n-1)}{\sigma^2} $$
은 서로 독립입니다. (이것은 따로 포스팅을 해보도록 하겠습니다.)
<br/><br/>
그러면 아래와 같이 적률생성함수의 성질을 이용해 나눠질 수 있을 것입니다.
<br/><br/>
$$ \begin{aligned} M_{\frac{(n-1)S^2}{\sigma^2} + Z^2}(t) = M_{\frac{(n-1)S^2}{\sigma^2}}(t) M_{Z^2}(t) \end{aligned} $$
<br/><br/>
여기서 
$$ Z^2 $$
은 아래와 같이 자유도가 1인 카이제곱 분포를 따르게 됩니다.
<br/><br/>
$$ \begin{aligned} M_{Z^2}(t) = (\frac{1}{1-2t})^{1/2}  \end{aligned} $$
<br/><br/>
식을 다시 정리해서 보면,
<br/><br/>
$$ \begin{aligned} (\frac{1}{1-2t})^{n/2} = M_{\frac{(n-1)S^2}{\sigma^2}}(t) (\frac{1}{1-2t})^{1/2}  \end{aligned} $$
<br/><br/>
$$ \begin{aligned} M_{\frac{(n-1)S^2}{\sigma^2}}(t) = (\frac{1}{1-2t})^{(n-1)/2}  \end{aligned} $$
<br/><br/>
$$ \begin{aligned} M_{\frac{(n-1)S^2}{\sigma^2}}(t) \end{aligned}  $$
는 자유도가 n-1인 카이제곱분포의 적률생성함수 형태를 가지고 있죠. 유일성 정리(Uniqueness Theorem)에 의해, 
<br/><br/>
$$ \begin{aligned} \frac{(n-1)S^2}{\sigma^2} \end{aligned}  $$
는 자유도가 n-1인 카이제곱 분포를 따르게 됩니다.
<br/><br/>
좀 돌아온 것 같지만, 표본 분산 
$$ S^2 $$
을 정의하고, 
$$ \begin{aligned} \frac{(n-1)S^2}{\sigma^2} \end{aligned}  $$
는 자유도 n-1인 카이제곱 분포를 따르게 된다!를 알게 되었네요.
<br/><br/>
<br/><br/>

통계검정을 위한 재료들이 하나씩 모이고 있네요. 냠냠..