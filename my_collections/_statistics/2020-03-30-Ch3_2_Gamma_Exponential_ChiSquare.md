---
layout: post
title: "감마, 지수, 그리고 카이제곱분포"
author-id: "Cornelii. G. Son"
tags: [study, statistic]
updated: "2020-03-31"
chapter: "3-2"
en_title: "Gamma, Exponential, and Chi-square Distribution"
---

## 감마분포
<br/>
연속확률분포 중 하나인 감마분포는 감마함수에서 자연스럽게 유도됩니다. 살펴봅시닷!

<br/><br/>

#### 감마함수
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
에 1을 넣으면,
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

#### 감마분포
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

#### 감마분포의 기댓값과 분산

#### 감마분포의 적률생성함수

## 지수분포
지수분포는 감마분포에서 간단히
$$ \alpha = 1$$
을 대입하므로 얻을 수 있고 아래와 같습니다.
<br/><br/>
$$ \begin{aligned} \frac{1}{\beta}e^{-x/\beta} \end{aligned} $$
<br/><br/>
<br/><br/>

#### 지수분포의 기댓값과 분산

#### 지수분포의 적률생성함수


## 카이 제곱 분포
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
역학이나 기구학등 여러 학문에서 쓰이는 용어이지만, 여기서는 일단 하나의 조절할 수 있는 파라미터라고 생각하고 넘어가봅시다.
<br/><br/>
<br/><br/>



#### 카이 제곱 분포의 기댓값과 분산

#### 카이 제곱 분포의 적률생성함수

<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>