---
layout: post
title: "이산확률분포 균일분포와 이항분포"
author-id: "Cornelii. G. Son"
tags: [study, statistic]
updated: "2020-03-20"
chapter: "2-1"
en_title: "Descrete Probability Distribution: Uniform & Binary Distribution"
---

## 이산확률분포
이산형 확률변수 즉, 셀 수 있는 (Countable한, (자연수와 1:1 대응 시킬 수 있는) 유한한 또는 무한한 형태의 확률변수가 가지는 분포를 말합니다. 이산확률분포가 이산확률변수의 확률이 됩니다.
(연속확률분포의 경우, 확률분포 값 자체가 확률이 아닌 것과 대조)
<br/><br/>
<br/><br/>

## 균일분포 (Uniform Distribution)
<br/>
이산확률분포 중 균일 분포는 표본공간의 이산형 확률변수에 동일한 가중치를 주는 분포입니다. 
예를 들어 표본공가에 k개의 원소가 있다면, 1을 k로 나눈 값이 확률분포 즉 모든 확률변수의 균일한 확률이 되는 것이죠.
<br/><br/>
$$ \begin{aligned} f(x_i) = \frac{1}{k} \end{aligned} $$
<br/><br/>
균일 분포에서 기댓값은 간단히 아래와 같습니다.
<br/><br/>
$$ \begin{aligned} \mu = \frac{1}{k}\sum_i^Nx_i \end{aligned} $$
<br/><br/>
분산은 아래와 같습니다.
<br/><br/>
$$ \begin{aligned} \sigma^2 = \frac{1}{k}\sum_i^N(x_i-\mu)^2 \end{aligned} $$
<br/><br/>
다시 한 번 말하지만, 여기서의 기댓값과 분산은 표본공간의 기댓값과 분산입니다. (N은 표본공간의 원소의 갯수가 되는 것이죠.)
<br/><br/>

#### 균일분포의 적률생성함수
<br/>
균일분포의 적률생성함수를 구해봅시다.
<br/><br/>
$$ \begin{aligned} M_X(t) = \sum^N_ie^{x_it}f(x_i) = \frac{1}{N}\sum^N_ie^{x_it} \end{aligned} $$
<br/><br/>
위와 같은 형태가 되네요. 헤헤?!
<br/><br/>
<br/><br/>

## 이항분포 (Binomial Distribution)
<br/>
이항분포는 성공아니면 실패처럼 두 가지의 경우만을 가지는 시행을 여러번 반복했을 때, 몇 번 이나 발생할 지를 표현한 확률분포입니다.(성공 또는 실패 중 하나의 경우에 대해 몇 번 일어나는지 정해지면 다른 경우는 자동적으로 정해짐. N = n + N-n)
<br/><br/>
이항분포는 `베르누이 과정`이라는 시행의 특성을 전제하고 있는데요.
<br/><br/>
n번 반복 시행 중에, 각 시행의 결과는 두 가지의 경우 중 하나가 되고, 성공 또는 실패의 확률은 각 시행마다 동일해야 합니다. 그리고,각각의 시행은 모두 독립을 전제하고 있습니다.
<br/><br/>
가까운 적절한 예로는 동전 N번 던지기 등이 있겠네요.
<br/><br/>
편의 상 각 시행마다의 두 가지 경우가 성공과 실패라고 해봅시다.
<br/><br/>
성공의 확률을 p라 하면, 실패의 확률은 두 가지의 경우 밖에 없으므로 자연스럽게 1-p가 됩니다.
<br/><br/>
그러면, 이항분포는 아래와 같이 나타낼 수 있습니다.
<br/><br/>
$$ \begin{aligned} b(x;n,p) = \binom{n}{x} p^x(1-p)^{n-x} \end{aligned} $$
<br/><br/>
말로 풀어서 설명해보면, 시행의 횟수 n과 각 시행의 성공의 확률 p가 정해였을 때, x번 성공한 확률은 n번 중 x번을 조합으로 골라서 x번 p의 확률로 성공하고 나머지 n-x를 1-p의 확률로 실패하는 경우를 곱한 형태로 나타낸다는 것입니다.
<br/><br/>
여기서 단순하게 각 시행들의 확률을 단순 곱셈으로 나타낼 수 있었던 건, 베르누이 과정의 `각 시행은 독립`이라는 가정 때문에 할 수 있었던 것이죠.
<br/><br/>
n번 시행하고 p의 성공확률을 가지는 이항 분포의 기댓값과 분산은 아래와 같습니다.
<br/><br/>
$$ \mu = np $$
<br/><br/>
$$ \sigma^2 = np(1-p)$$
<br/><br/>
i번째 시행의 결과를 성공의 경우 1과 실패의 경우 0의 값을 가질 수 있는 
$$ A_i $$
라는 확률변수로 나타낸다면, n번 시행 중 x번 성공하는 확률변수를 아래와 같이 나타낼 수 있습니다.
<br/><br/>
$$ \begin{aligned} X = A_1 + A_2 + A_3 + ... + A_n = \sum_i^nA_i \end{aligned} $$
<br/><br/>
각 시행의 성공의 경우의 기댓값을 구해보면, 
<br/><br/>
$$ E[A_i] = 1 \times p + 0 \times (1-p) = p $$
<br/><br/>
가 됩니다. 자연스럽게 X의 기댓값은 아래와 같아집니다.
<br/><br/>
$$ \begin{aligned} E[X] = E[\sum_i^nA_i] = \sum_i^n E[A_i] = \sum_i^np = np \end{aligned} $$
<br/><br/>
분산도 같은 방법으로 구해보면,
<br/><br/>
각 시행의 성공의 경우를 분산으로 나타내면 아래와 같고,
<br/><br/>
$$ V[A_i] = (1-p)^2 \times p + (0-p)^2(1-p) = p(1-p) $$
<br/><br/>
X의 분산은 자연스럽게 아래처럼 나타낼 수 있게 됩니다.
<br/><br/>
$$ \begin{aligned} V[X] = V[\sum_i^nA_i] = \sum_i^n 1^2 \times V[A_i] = \sum_i^np(1-p) = np(1-p) \end{aligned} $$
<br/><br/>

#### 이항분포의 적률생성함수
<br/>
n번 시행하고, 각 시행에서 p의 성공확률을 가지는 이항분포의 적률생성함수도 구해봅시다.
<br/><br/>
$$ \begin{aligned} M_X(t) = \sum_{k=0}^n e^{kt} \binom{n}{k}p^k(1-p)^{n-k} \end{aligned} $$
<br/><br/>
여기서 더 전개하기가 쉽지 않네요 ㅎㅎ;
<br/><br/>
사실 이항분포가 있는 부분만 보면 아래와 같습니다.
<br/><br/>
$$ \begin{aligned} \sum_{k=0}^n \binom{n}{k}p^k(1-p)^{n-k} = (p + 1-p )^n  = 1 \end{aligned} $$
<br/><br/>
<br/><br/>

## 균일분포 & 이항분포 in Python

```python
import scipy.stats as sps

## 균일분포
disc_uniform = sps.randint(low = 1, high = 10)

## expectation, variance
mean, var = disc_uniform.mean(), disc_uniform.var()
print(f"Discrete Uniform Distribution's expectation : {mean}, variance : {var}")

## get some values from discrete uniform distribution
disc_uniform_values = disc_uniform.rvs(size=10, random_state=12345)



## 이항분포
binorm = sps.binom(10,0.2) # binom(n,p)

## expectation, variance
mean, var = binorm.mean(), binorm.var()
print(f"binormial distribution's expectation : {mean}, variance : {var}")

## get some values from binormial distribution
binom_values = binom.rsv(size=10, random_state=12345)

```
