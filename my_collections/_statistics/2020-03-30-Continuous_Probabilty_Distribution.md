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
$$ \begin{aligned}   \end{aligned} $$
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


<br/><br/>
<br/><br/>
<br/><br/>

## 표준정규분포

<br/><br/>
<br/><br/>
<br/><br/>


