---
layout: post
title: "Navier-Stokes Equations"
author-id: "Cornelii. G. Son"
comments: true
tags: [Fluid Dynamics]
chapter: "1-1"
---

----
<br/>
<br/>

#### Navier-Stokes Equations?
----
유체의 지배방정식이며, 비선형 미분방정식입니다. 

실해를 얻어내기에는 굉장히 한정적이며, FVM 등의 방법을 활용하여 근사해를 구합니다만 실제 유체를 굉장히 정밀하게 해석하는 것으로 알려져 있습니다. 

또한, 밀레니엄 문제 중 하나에 포함되어 있는 것으로 유명합니다.

<br/>
<br/>

#### Reynolds Transport Theorem (레이놀즈 전달 정리)
----
Reynolds Transport Theorem을 다루지 않고, "유체" 에 대한 식을 전개할 수 없습니다. 
말그대로 유체는 흐르는 것이기 때문입니다. 
이 흐름의 수학적 표현이 바로 Reynolds Transport Theorem입니다.

$$ B_{sys} $$ 를 어떠한 **유체**의 성질이라고 한다면, 

$$ \begin{aligned} \frac{dB_{sys}}{dt} = \frac{\partial}{\partial{t}}\int_{CV} \beta \rho dV + \int_{CS} \beta \rho (v \cdot n )dA

\end{aligned} $$

where, $$ CV: Control Volume, CS: Control Surface, \\
B_{sys} = \int_{CV} \beta \rho dV \\
\rho: density
 $$
<br/>

오른쪽 변의 2번째 항의 $$ v $$는 Control Surface 표면에서의 속도벡터입니다. $$ n $$은 표면 면적에 수직한 법선벡터입니다.  

<span style="color:red">**여기서 유의해야 할 것이 이렇게 표현하면 나가는 방향이 +, 들어오는 방향이 - 라는 것입니다.**</span>  
  
왜 나가는데 +를 해줘야 하고, 들어오는 것을 -로 해주어야 할까요?  

이것을 이해하는게 상당히 중요한데, 관심이 있는 것은 $$ B_{sys} $$이지
CV안의 물성 $$ B_{CV} $$ 가 아닙니다!  

특정 시점(point)에 (CV를 구성한 시점) $$ B_{sys} = B_{CV} $$ 이지만, 문제는 유체라서 흐르는 것이죠. 

<span style="color:blue">
**CV 안에 있었던, 하지만 $$ B_{sys} $$ 에 속해 있던 그 물성이 방금 나갔으니 그것을 더해주어야 하는 것이고,**</span>  

<span style="color:blue">
**CV 밖에 있었던, 하지만 $$ B_{sys} $$ 에 속하지 않았던 들어온 친구를 빼주어야 하는 것입니다.**</span>  


마지막으로 식을 조금 변형해서 $$ dA $$ 면적을 법선벡터를 포함된 값으로 보면 $$ dA = \lvert {dA} \rvert \vec{n} $$ 아래 처럼도 쓸 수 있을 것입니다. 

$$ \begin{aligned} \frac{dB_{sys}}{dt} = \frac{\partial}{\partial{t}}\int_{CV} \beta \rho dV + \int_{CS} \beta \rho v \cdot dA

\end{aligned} $$


<br/>
<br/>

#### Continuity Equation (연속방정식) 
----
연속방정식은 유체역학의 구성방정식. 쉽게 말해 만족해야만 하는 제한 조건과 같은 식입니다. 질량 보존의 법칙이기 때문에 거의 모든 상황에서 만족하는 것이 당연할 것입니다.  

$$ \begin{aligned} \frac{d m_{sys}}{dt} &= \frac{\partial}{\partial{t}} \int_{CV} \rho dV + \int_{CS} \rho v \cdot dA = 0
\end{aligned} $$  

<br/>

###### - Cartesian Fixed Control Volume
----

velocity field
$$
  v = u\vec{i} + \nu\vec{j} + w\vec{k}  
$$ 

$$ \begin{aligned} \frac{\partial{\rho}}{\partial{t}}dxdydz + dxdydz(\frac{\partial{\rho u}}{\partial{x}} + \frac{\partial{\rho \nu}}{\partial{y}} + \frac{\partial{\rho w}}{\partial{z}}) = 0
\end{aligned} $$


$$ \begin{aligned} \frac{\partial{\rho}}{\partial{t}} + (\frac{\partial{\rho u}}{\partial{x}} + \frac{\partial{\rho v}}{\partial{y}} + \frac{\partial{\rho w}}{\partial{z}}) = 0
\end{aligned} $$  

<br/>
Incompressible Flow (비압축 유체) 에서는 ( $$ \rho: constant, \frac{\partial{\rho}}{\partial{x^i}} = 0, \frac{\partial{\rho}}{\partial{t}} = 0 $$ )

$$ \begin{aligned} \frac{\partial{u}}{\partial{x}} + \frac{\partial{\nu}}{\partial{y}} + \frac{\partial{w}}{\partial{z}} = 0
\end{aligned} $$  

<br/>

Steady-State (정상 상태) 에서는 ( $$ \frac{\partial}{\partial{t}} = 0 $$ )

$$ \begin{aligned} \frac{\partial{\rho u}}{\partial{x}} + \frac{\partial{\rho \nu}}{\partial{y}} + \frac{\partial{\rho w}}{\partial{z}} = 0
\end{aligned} $$  

<br/>

###### - Reynolds Transport Theorem with Gauss's Divergence Theorem  
----
(fixed Control Volume)

$$ \begin{aligned} \frac{d m_{sys}}{dt} &= \frac{\partial}{\partial{t}} \int_{CV} \rho dV + \int_{CS} \rho v \cdot dA = 0
\end{aligned} $$  

좌측의 두번째 항에 대해 Gauss's Divergence Theorem 에 의해서,

$$ \begin{aligned} \int_{CS} \rho v \cdot dA = \int_{CV} \nabla \cdot (\rho v) dV
\end{aligned} $$  

(fixed Control Volume)

$$ \begin{aligned} \frac{d m_{sys}}{dt} &=  \int_{CV} \frac{\partial{\rho}}{\partial{t}} dV + \int_{CV} \nabla \cdot (\rho v) dV = 0
\end{aligned} $$  

$$ \begin{aligned} \int_{CV} [\frac{\partial{\rho}}{\partial{t}} + \nabla \cdot (\rho v) ] dV = 0
\end{aligned} $$  

위 식이 항상 만족하기 위해서는, 적분 내부항이 0이여야 하기 때문에,  

$$ \begin{aligned} \frac{\partial{\rho}}{\partial{t}} + \nabla \cdot (\rho v) = 0
\end{aligned} $$  

<br/>
Incompressible Flow (비압축 유체) 에서는 ( $$ \rho: constant, \frac{\partial{\rho}}{\partial{x^i}} = 0, \frac{\partial{\rho}}{\partial{t}} = 0 $$ )

$$ \begin{aligned} \nabla \cdot v = 0
\end{aligned} $$  


<br/>

Steady-State (정상 상태) 에서는 ( $$ \frac{\partial}{\partial{t}} = 0 $$ )

$$ \begin{aligned} \nabla \cdot (\rho v) = 0
\end{aligned} $$  

<br/>
<br/>

#### Linear Momentum Conservation (선형 모멘텀 보존식) 
----

뉴턴 제2법칙을 알고있다면 친숙하시겠지만, 시간에 따른 선형모멘텀의 변화 즉 선형모멘텀의 시간 미분이 **힘** 으로 표현됩니다.
  

$$ \begin{aligned} \frac{d (mv)_{sys}}{dt} &= \Sigma F =  \frac{\partial}{\partial{t}} \int_{CV} \rho v dV + \int_{CS} \rho v (v \cdot dA)
\end{aligned} $$  

<br/>

$$ \begin{aligned} \Sigma F = F_{pressure} + F_{viscous} + F_{gravity} 
\end{aligned} $$  

<br/>

###### - Cartesian Fixed Control Volume
----

$$ x $$축만을 놓고 보면,

$$ \begin{aligned} \Sigma dF_x &=  -\frac{\partial{P}}{\partial{x}}dV + \frac{\partial{\sigma_{xx}}}{\partial{x}}dV + \frac{\partial{\tau_{yx}}}{\partial{y}}dV + \frac{\partial{\tau_{zx}}}{\partial{z}}dV + \rho g_x dV
\end{aligned} $$  

where, $$ dV = dxdydz $$  

$$ \tau $$ 를 2차텐서로 아래와 같이 정의하여 3축의 식을 한 식으로 표현하면,  

$$ \tau = \begin{pmatrix} \sigma_{xx} & \tau_{xy} & \tau_{xz} \\\ \tau_{yx} & \sigma_{yy} & \tau_{yz} \\\ \tau_{zx} & \tau_{zy} & \sigma_{zz} \end{pmatrix} $$

<br/>  

$$ \begin{aligned} \Sigma dF &= (-\nabla P + \nabla \cdot \tau + \rho g)dV
\end{aligned} $$  


<br/>

$$ \begin{aligned} \frac{\partial{\rho v}}{\partial{t}} dV + [\rho v (v \cdot dA)]_{+out -in} &= \frac{\partial{\rho v}}{\partial{t}}dV + \frac{\partial{u \rho v}}{\partial{x}}dV + \frac{\partial{\nu \rho v}}{\partial{y}}dV + \frac{\partial{w \rho v}}{\partial{z}}dV
\end{aligned} $$  

<br/>



$$ \begin{aligned} \therefore (-\nabla P + \nabla \cdot \tau + \rho g)dV = \frac{\partial{\rho v}}{\partial{t}}dV + \frac{\partial{u \rho v}}{\partial{x}}dV + \frac{\partial{\nu \rho v}}{\partial{y}}dV + \frac{\partial{w \rho v}}{\partial{z}}dV
\end{aligned} $$  

<br/>

$$ \begin{aligned} -\nabla P + \nabla \cdot \tau + \rho g &= \frac{\partial{\rho v}}{\partial{t}} + \frac{\partial{u \rho v}}{\partial{x}} + \frac{\partial{\nu \rho v}}{\partial{y}} + \frac{\partial{w \rho v}}{\partial{z}} \\
&= \rho \frac{\partial{v}}{\partial{t}} + v \frac{\partial{\rho}}{\partial{t}} + u \rho  \frac{\partial{v}}{\partial{x}} + \nu \rho \frac{\partial{v}}{\partial{y}} + w \rho \frac{\partial{v}}{\partial{z}} + v \frac{\partial{u \rho}}{\partial{x}} + v \frac{\partial{\nu \rho}}{\partial{y}} + v \frac{\partial{w \rho}}{\partial{z}} \\
&= \rho \frac{\partial{v}}{\partial{t}} + u \rho  \frac{\partial{v}}{\partial{x}} + \nu \rho \frac{\partial{v}}{\partial{y}} + w \rho \frac{\partial{v}}{\partial{z}} + v ( \frac{\partial{\rho}}{\partial{t}} + \frac{\partial{u \rho}}{\partial{x}} + \frac{\partial{\nu \rho}}{\partial{y}} + \frac{\partial{w \rho}}{\partial{z}}) 
\end{aligned} $$  

because last four terms are of continuity equation, which becomes zero  

$$
\begin{aligned}
-\nabla P + \nabla \cdot \tau + \rho g &= \rho \frac{\partial{v}}{\partial{t}} + u \rho  \frac{\partial{v}}{\partial{x}} + \nu \rho \frac{\partial{v}}{\partial{y}} + w \rho \frac{\partial{v}}{\partial{z}} \\
&= \rho (\frac{\partial{v}}{\partial{t}} + u \frac{\partial{v}}{\partial{x}} + \nu \frac{\partial{v}}{\partial{y}} + w \frac{\partial{v}}{\partial{z}}) \\
&= \rho \frac{dv}{dt}
\end{aligned}
$$

<br/>

If viscousity terms are represented by Newtonian Fluid  

$$ \tau_{ij} = \mu (\frac{\partial{v_i}}{\partial{x_j}} + \frac{\partial{v_j}}{\partial{x_i}}) $$  

$$ \nabla \cdot \tau = \mu (\nabla^2 v + \nabla (\nabla \cdot v)) $$  

$$
\begin{aligned}
\rho \frac{dv}{dt} &= -\nabla P + \mu (\nabla^2 v + \nabla (\nabla \cdot v)) + \rho g 
\end{aligned}
$$  

For the incompressible flow  
$$ \nabla \cdot v = 0 $$  

<br/>

$$
\begin{aligned}
\rho \frac{dv}{dt} &= -\nabla P + \mu \nabla^2 v + \rho g 
\end{aligned}
$$  

We've just got Navier-Stokes Equation for incompressible flow!

<br/>

###### - Reynolds Transport Theorem with Gauss's Divergence Theorem  
----
(fixed Control Volume)  

$$ \begin{aligned} F_{pressure} + F_{viscous} + F_{gravity}  =  \frac{\partial}{\partial{t}} \int_{CV} \rho v dV + \int_{CS} \rho v (v \cdot dA)
\end{aligned} $$  

<br/>

Caution: $$ dA = \lvert dA \rvert \vec{n} $$ 

let's take $$ F_{pressure} $$ into $$ F_{viscous} $$ with $$ \hat \tau $$  

$$ \hat \tau = \begin{pmatrix} \sigma_{xx} - p & \tau_{xy} & \tau_{xz} \\\ \tau_{yx} & \sigma_{yy} - p & \tau_{yz} \\\ \tau_{zx} & \tau_{zy} & \sigma_{zz} - p \end{pmatrix} = \tau - pI$$


$$ \begin{aligned} F_{viscous + pressure} = \int_{CS} \hat \tau \cdot dA
\end{aligned} $$  

$$ \begin{aligned} F_{gravity} = \int_{CV} \rho g  dV
\end{aligned} $$  

<br/>

$$ \begin{aligned} \int_{CS} \hat \tau \cdot dA + \int_{CV} \rho g  dV = \frac{\partial}{\partial{t}} \int_{CV} \rho v dV + \int_{CS} \rho v (v \cdot dA)
\end{aligned} $$  

$$ \begin{aligned} \int_{CV} \nabla \cdot \hat \tau dV + \int_{CV} \rho g  dV = \int_{CV} \frac{\partial{\rho v}}{\partial{t}} dV + \int_{CV} \nabla \cdot (\rho v) v + \rho v \cdot \nabla v dV
\end{aligned} $$  

For it holds regardless of CV  

$$ \begin{aligned} \nabla \cdot \hat \tau + \rho g = \frac{\partial{\rho v}}{\partial{t}} + \nabla \cdot (\rho v) v + \rho v \cdot \nabla v
\end{aligned} $$  

$$
\begin{aligned}
-\nabla p + \nabla \cdot \tau + \rho g &= \rho \frac{\partial{v}}{\partial{t}} + v \frac{\partial{\rho}}{\partial{t}} + \nabla \cdot (\rho v) v + \rho v \cdot \nabla v \\
&= \rho \frac{\partial{v}}{\partial{t}} + \rho v \cdot \nabla v + (\frac{\partial{\rho}}{\partial{t}} + \nabla \cdot (\rho v))v \\
&= \rho \frac{\partial{v}}{\partial{t}} + \rho v \cdot \nabla v \\
&= \rho \frac{dv}{dt}
\end{aligned}
$$

As mentioned before, applying Newtonian Fluid Assumption for viscous term.  

$$
\begin{aligned}
\rho \frac{dv}{dt} &= -\nabla p + \mu (\nabla^2 v + \nabla (\nabla \cdot v)) + \rho g 
\end{aligned}
$$  

For the incompressible flow  
$$ \nabla \cdot v = 0 $$  

<br/>

$$
\begin{aligned}
\rho \frac{dv}{dt} &= -\nabla p + \mu \nabla^2 v + \rho g 
\end{aligned}
$$  

