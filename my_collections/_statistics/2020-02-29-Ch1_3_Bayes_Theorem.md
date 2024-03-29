---
layout: post
title: "베이즈 정리"
author-id: "Cornelii. G. Son"
tags: [study, statistics]
updated: "2020-02-29"
chapter: "1-3"
comments: true
en_title: "Bayes Theorem"
---

## 확률의 곱하기 정리 (조건부 확률, 독립)
베이즈 정리에 대해서 살펴보기 전에, 조건부확률과 독립에 대해서 먼저 이야기해볼까 합니다.

사상 A와 사상 B가 서로 독립 일때,  
$$  P(A \cap B) = P(A)P(B)$$
이고,  
<br/>
조건부확률로 표현한 사상 A와 사상 B가 동시에 만족하는 확률은  
$$ P(A \cap B) = P(B)P(A|B) $$
로 표현될 수 있습니다.  
<br/>

먼저, 두 개의 사상을 넘어서, 여러개의 사상을 동시에 만족하는 경우의 확률로  
일반화를 해봅시다.
<br/>
<br/>
$$ P(A_{1} \cap A_{2} \cap A_{3} \cap ... \cap A_{n})$$
에서
<br/>
$$ A_{1} \cap A_{2} \cap A_{3} \cap ... \cap A_{n-1} $$
을 B라고 치환하면,  

$$ \begin{aligned}  P(A_{1} \cap A_{2} \cap A_{3} \cap ... \cap A_{n}) &= P(B \cap A_{n}) \\
&= P(B)P(A_{n}|B) \\
&= P(A_{1} \cap A_{2} \cap ... \cap A_{n-1})P(A_{n}|A_{1} \cap A_{2} \cap ... \cap A_{n-1}) \\
이를 \space 반복하면, \\
&= P(A_{1})P(A_{2}|A_{1})P(A_{3}|A_{1} \cap A_{2})...P(A_{n}|A_{1} \cap A_{2} \cap ... \cap A_{n-1})
 \end{aligned}
$$
<br/>
<br/>
위의 식처럼 표현할 수 있습니다. 이를, 확률의 승법 정리 (곱하기 정리)라고 합니다.
<br/>
<br/>
위 식에, 각각의 사상이 독립인 경우에는  
$$ P(A_{1} \cap A_{2} \cap A_{3} \cap ... \cap A_{n}) = P(A_{1})P(A_{2})P(A_{3})...P(A_{n})$$
이 되게 됩니다.
<br/><br/>
<br/><br/>
$$P(A_{3}|A_{1} \cap A_{2})$$
를 예로 다른 경우를 생각해봅시다.  
<br/>
만약, 
$$ A_{3}$$
은
$$A_{1}$$
과 
$$ A_{2}$$
에 대해 각각 독립인데,
$$A_{1}$$
과 
$$ A_{2}$$
는 서로 간에 독립이 아니라면?  

<br/> 
$$ \begin{aligned} 
P(A_{3}|A_{1} \cap A_{2}) &= \frac{P(A_{1} \cap A_{2} \cap A_{3})}{P(A_{1} \cap A_{2})} = \frac{P(A_{1} \cap A_{2})P(A_{3})}{P(A_{1} \cap A_{2})} = P(A_{3})
\end{aligned}
$$  

각 사상이 독립인 경우와 달라지는게 없습니다.  
<br/>
<br/>
만약,
$$ A_{3}$$
은
$$ A_{2}$$
에 대해 독립인데,
$$A_{1}$$
에 대해서는 독립이 아니고,
$$A_{1}$$
와 
$$ A_{2}$$
는 서로 간에 독립이 맞다면?  

<br/>
$$ \begin{aligned} 
P(A_{3}|A_{1} \cap A_{2}) &= \frac{P(A_{1} \cap A_{2} \cap A_{3})}{P(A_{1} \cap A_{2})} = \frac{P(A_{1} \cap A_{3})P(A_{2})}{P(A_{1})P(A_{2})} = P(A_{3}|A_{1})
\end{aligned}
$$  
  
이 됩니다.  
<br/>
이것으로 조건으로 주어진 사상과, 우리가 알고자 하는 사상이 독립이 아닌 경우에는, 조건인 사상은 조건 그대로 남아 있는 것을 알 수 있습니다. 
<br/><br/>
<br/><br/>

## 베이즈 정리
서론이 길었으니 이제 베이즈 정리에 대해 이야기 해볼까 합니다.  
<br/>
아래의 조건부확률 식 두개를 살펴보면 좌항이 동일한 것을 알 수 있습니다.
<br/><br/>
$$ P(A \cap B) = P(A)P(B|A) $$
<br/>
$$  P(A \cap B) = P(B)P(A|B) $$
<br/><br/>
이를 통해, 아래의 식이 자연스럽게 나오게 되는데, 이것이 바로 베이즈정리라 불리는 식입니다.  
<br/>
$$ P(A)P(B|A) = P(B)P(A|B) $$  
<br/>
<br/>
그렇다면, 베이즈 정리가 왜 그렇게 유용한 것일까요?   
<br/>
그것은 바로, 베이즈 정리가 
$$ P(A|B) $$
와 
$$ P(B|A) $$
간의 관계를 나타내고 있기 때문입니다.  
<br/>
<br/>
좀 더 생각해보기 위해서 아래의 문제를 한 번 풀어보세요~!


##### 그림과 같이 앞에 양복을 차려입고 훤칠한?! 젊은 남자가 책상 앞에 앉아 있습니다. 사진 속 인물에 적절한 선택지를 골라보세요~!  
<br/>

<img src="/assets/img/statistics/01/1_3_1.png" alt="businessman" width="700"/>
<br/>
1. 남자
2. 비즈니스맨
3. 아침에 머리를 손질하고 온 비즈니스맨

<br/>
몇 번을 고르셨나요?  1번? 혹은 3번? 2번?  
<br/>
<br/>
많은 사람들이 1번 또는 3번을 고르게 됩니다.  
<br/>
먼저, 1번을 고른 사람의 생각을 확률적인 관점에서 접근해봅시다.  
<br/>
남자인 경우의 사상을 A, 비즈니스 전문 일(?)을 하는 사상을 B, 아침에 머리 손질을 할 사상을 C라고 임의로 정해봅시다.  
<br/>
그럼,   
1번의 경우는
$$ A $$
,  
2번의 경우는
$$ A \cap B$$
,  
3번의 경우는
$$ A \cap B \cap C$$
가 됩니다.  

교집합을 할 수록 집합의 원소의 수가 아무래도 줄어들테니, 아마도 가장 많은 원소를 가졌을 1번 A의 확률(가중치)이 가장 클 것입니다.  
그래서 1번을 골랐다면, 적절한 설명이 될 것입니다.  

<br/>
그렇다면, 3번을 고른 사람들의 생각을 확률적으로 생각해봅시다.  
왜 가장 적은 원소를 가졌을 사상, 3번을 골랐을까요?  
<br/><br/>
이를 이해하기 위해서,
<br/>
조건부확률을 통해 다시 1번을 선택한 사람의 경우를 생각해봅시다.  
<br/>
앞 선 문제의 사진을 D라는 사상이라고 해봅시다.  
<br/>
그렇다면 1번은 
$$P(A|D)$$
 즉, 사진(조건)이 주어졌을 때, 가장 높은 확률을 지닌 선택지를
 선택했습니다. 
 <br/><br/>
 반면, 3번을 선택한 사람들은, 결론부터 말해서
$$ P(D|A \cap B \cap C) $$
가 가장 클 것으로 보이기 때문에, 3번을 선택하였습니다.  
<br/>
다시 말해, 선택지에 있는 조건이 만족될 때, 사진이 나오는 확률이 최대가 될 만한 것을 골랐다는 것입니다.  
<br/>
이를 수식으로 살펴보면,  
<br/>
$$ P(D|선택지) = \frac{P(D \cap 선택지)}{P(선택지)}$$
<br/>
<br/>
분자의 항은 판단하기가 어렵기 때문에 그냥 두고서라도,
<br/><br/>
분모의 확률이 작을수록 커지게 되는 
$$ P(D|선택지) $$
를 최대로 만들기 위해,  
가장 작은 가중치를 가졌을 3번을 선택하게 된 것입니다.
<br/>
<br/>
$$
P(A|D)
$$
와
$$
P(D|A \cap B \cap C)
$$

<br/>
뭔가, 베이즈 정리가 조금씩 겹쳐보이기 시작하시나요?  

<br/>
여기서 베이즈정리의 유용성을 좀 더 이야기 하기 위해, 통계이야기를 잠깐 하고자 하는데요.  
<br/>
우리는 통계를 통해 각 원소가 측정할 수 있는 특정한 상태를 가지고 있는 집합, 즉 모집단(Population)을 조사하고 모집단 전체를 대표하는 상태를 정의합니다. 
<br/><br/>
모집단 내의 모든 집단원을 파악하기는 힘들기 때문에, 표본을 추출하여, 모집단을 대표하는 상태값(모수)을 추측하는 방법을 사용합니다.

여기서 표본을 D, 모수를 
$$ \Theta $$ 
라 하면, 
<br/>
(표본은 문제의 사진이고, 모수는 선택지가 될 것 입니다.)  

먼저 기본적으로 베이즈 정리에 의해 아래와 같은 관계를 가지게 됩니다.  

$$P(\Theta | D)P(D) = P(D|\Theta)P(\Theta)$$

<br/>
이와 더불어 표본 D가 주어졌을 때  
$$P(D)$$
는 이미 상수로 정해졌다고 말할 수 있습니다.
<br/><br/>
$$P(D=d_{i})$$
D가 어떤 사상을 가지든, 이미 주어진 표본 (데이터) 안에서 가중치가 주어진 것이기 때문입니다.  

<br/>
그래서 보통, 
$$P(D)$$
를 상수로 두고,  
<br/>
$$P(\Theta | D) \approx P(D | \Theta)P(\Theta)$$  
 위 식을 통해, 
$$P(\Theta | D)$$
 , 또는 
$$P(D | \Theta)$$
를 최대화시키려는 방법으로 모수 
$$\Theta$$
를 추측하게 됩니다.  
<br/>
조금 더 유식한 말로는,  
$$P( \Theta | D)$$
를 
$$ Posterior $$
(분포)  
$$P(D | \Theta)$$
를 
$$ Likelihood $$
라고 부릅니다.  
$$ P(\Theta) $$ 
는 
$$ Prior $$
라고 합니다.  
<br/>
$$ Posterior $$
는 Data가 주어졌을 때, 특정 모수를 가질 확률을 의미하고,  
$$ Likelihood $$
는 반대로 특정 모수라고 가정할 때, 주어진 Data가 나올 확률입니다.  
$$ Prior$$
는 말그대로 모수에 대한 확률로써 사전에 주어진 또는 추측한 지식을 의미합니다.  
<br/>
<br/>
일반적으로
$$ Likelihood: \space P(D | \Theta)$$
는 구하기가 쉬운편입니다. 
<br/>
모수를 가정하고 주어진 표본(데이터)와의 오차를 정의할 수 있기 때문입니다. 
<br/><br/>
이와는 상반되게,
<br/>
$$ Posterior \space P( \Theta | D)$$
는 모수 자체가 알려진 것이 아니기 때문에 (unknown) 구하기 쉽지 않습니다. 
<br/><br/>
하지만, Bayes's Theorem이 출동한다면?  베! 이! 즈!
<br/><br/>
$$P(\Theta | D) \approx P(D | \Theta)P(\Theta)$$  
<br/>
바로 
$$ Likelihood $$
를 활용하여 구할 수 있게 됩니다.
<br/>
<br/>
물론, Prior를 알고 있거나, 적절한 분포를 가정해야 겠지요. 좀 더 우리가 조정할 수 있는 파라미터가 추가된다고 생각하시면 더 좋을 것 같습니다.
<br/>
<br/>
정리하면,
베이즈 정리는 조건부확률의 정수가 들어있다.
<br/>
나중에는 베이즈 네트워크까지 살펴볼 수 있기를... 예~!



