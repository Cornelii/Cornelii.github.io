---
layout: post
title: "Maxwell's Equations from Special Relativity"
author-id: "Cornelii. G. Son"
tags: [Maxwell Equation, Special Relativity]
comments: true
mathjax: true
---

----
<br/>
<br/>

#### From Lorentz Invariance to Maxwell's Equations
----

$$  $$  

$$ \begin{aligned} 
I (Action) = - \int m d\tau - e \int g_{\mu \nu}A^{\nu}dx^{\mu}
\end{aligned} $$  

where, proper time $$ d\tau = \sqrt{-g_{\mu \nu}dx^{\nu}dx^{\mu}} $$

<br/>

$$ \begin{aligned} 
\delta I = - \int m \delta(d\tau) - e[ \int g_{\mu \nu}\delta(A^{\nu})dx^{\mu} + \int g_{\mu \nu}A^{\nu}\delta(dx^{\mu})]
\end{aligned} $$  

<br/>

$$ \begin{aligned} 
\delta(d\tau) &= \frac{-g_{\mu \nu} (\delta (dx^{\mu})dx^{\nu} + \delta (dx^{\nu})dx^{\mu})}{2\sqrt{-g_{\mu \nu}dx^{\nu}dx^{\mu}}} \\ &= \frac{-2g_{\mu \nu} \delta (dx^{\mu})dx^{\nu}}{2\sqrt{-g_{\mu \nu}dx^{\nu}dx^{\mu}}} = \frac{-g_{\mu \nu} \delta (dx^{\mu})dx^{\nu}}{d\tau}
\end{aligned} $$  

$$ \begin{aligned} 
\delta(dx^{\mu}) &= d(\delta x^{\mu})
\end{aligned} $$  

$$ \begin{aligned} 
\delta(A^{\mu}) &= \frac{\partial{A^{\mu}}}{\partial{x_{\alpha}}}\delta x^{\alpha}
\end{aligned} $$  


$$ \begin{aligned} 
\delta I &= \int m g_{\mu \nu} \frac{dx^{\nu}}{d\tau} \delta (dx^{\mu})  - e[ \int g_{\mu \nu} \frac{\partial{A^{\nu}}}{\partial{x_{\alpha}}}\delta x^{\alpha} dx^{\mu} + \int g_{\mu \nu}A^{\nu}d(\delta x^{\mu})] \\ &= \int m g_{\mu \nu} \frac{dx^{\nu}}{d\tau} \frac{d (\delta  x^{\mu})}{dt} dt  - e[ \int g_{\mu \nu} \frac{\partial{A^{\nu}}}{\partial{x_{\alpha}}}\delta x^{\alpha} \frac{dx^{\mu}}{dt} dt + \int g_{\mu \nu}A^{\nu} \frac{d(\delta x^{\mu})}{dt} dt] 
\end{aligned} $$  

<br/>

$$ \text{at  } t_1, t_2 $$  

$$ \delta x^{\mu} (t_1) = \delta x^{\mu} (t_2) = 0 $$

<br/>

$$ \begin{aligned} 
\delta I &= \int^{t_2}_{t_1} m g_{\mu \nu} \frac{dx^{\nu}}{d\tau} \frac{d (\delta  x^{\mu})}{dt} dt  - e[ \int^{t_2}_{t_1} g_{\mu \nu} \frac{\partial{A^{\nu}}}{\partial{x_{\alpha}}}\delta x^{\alpha} \frac{dx^{\mu}}{dt} dt + \int^{t_2}_{t_1} g_{\mu \nu}A^{\nu} \frac{d(\delta x^{\mu})}{dt} dt] \\
&= m g_{\mu \nu} \frac{dx^{\nu}}{d\tau} \delta  x^{\mu} \biggr\rvert^{t_2}_{t_1} - \int^{t_2}_{t_1} m g_{\mu \nu}  \delta  x^{\mu} \frac{d}{dt} (\frac{dx^{\nu}}{d\tau}) dt  - e \int^{t_2}_{t_1} g_{\mu \nu} \frac{\partial{A^{\nu}}}{\partial{x_{\alpha}}}\delta x^{\alpha} \frac{dx^{\mu}}{dt} dt \\ & \text{ } -e g_{\mu \nu}A^{\nu} \delta x^{\mu} \biggr\rvert^{t_2}_{t_1} +e \int^{t_2}_{t_1} g_{\mu \nu} \delta x^{\mu} \frac{d(A^{\nu})}{dt} dt \\
\\
&= - \int^{t_2}_{t_1} m g_{\mu \nu}  \delta  x^{\mu} \frac{d}{dt} (\frac{dx^{\nu}}{d\tau}) dt  - e \int^{t_2}_{t_1} g_{\mu \nu} \frac{\partial{A^{\nu}}}{\partial{x_{\alpha}}}\delta x^{\alpha} \frac{dx^{\mu}}{dt} dt +e \int^{t_2}_{t_1} g_{\mu \nu} \delta x^{\mu} \frac{dA^{\nu}}{dt} dt
\\
\\
& \text{ dummy index change}
\\
\\
&=- \int^{t_2}_{t_1} m g_{\mu \nu}  \delta  x^{\mu} \frac{d}{dt} (\frac{dx^{\nu}}{d\tau}) dt  - e \int^{t_2}_{t_1} g_{\alpha \nu} \frac{\partial{A^{\nu}}}{\partial{x_{\mu}}}\delta x^{\mu} \frac{dx^{\alpha}}{dt} dt +e \int^{t_2}_{t_1} g_{\mu \nu} \delta x^{\mu} \frac{dA^{\nu}}{dt} dt
\\
&=- \int^{t_2}_{t_1} [ m g_{\mu \nu} \frac{d}{dt} (\frac{dx^{\nu}}{d\tau})  - e  g_{\alpha \nu} \frac{\partial{A^{\nu}}}{\partial{x_{\mu}}} \frac{dx^{\alpha}}{dt} +e  g_{\mu \nu}  \frac{dA^{\nu}}{dt} ] \delta  x^{\mu} dt
\end{aligned} $$  

<br/>
$$ \delta I = 0, \text{} $$  

<br/>
$$ \begin{aligned} 
\therefore 
m g_{\mu \nu} \frac{d}{dt} (\frac{dx^{\nu}}{d\tau})  - e  g_{\alpha \nu} \frac{\partial{A^{\nu}}}{\partial{x_{\mu}}} \frac{dx^{\alpha}}{dt} +e  g_{\mu \nu}  \frac{dA^{\nu}}{dt} = 0
\end{aligned} $$  

<br/>

$$ \begin{aligned} 
m g_{\mu \nu} \frac{d}{dt} (\frac{dx^{\nu}}{d\tau}) = e  g_{\alpha \nu} \frac{\partial{A^{\nu}}}{\partial{x_{\mu}}} \frac{dx^{\alpha}}{dt} -e  g_{\mu \nu}  \frac{dA^{\nu}}{dx_{\alpha}} \frac{dx^{\alpha}}{dt}
\end{aligned} $$  

<br/>

$$ \text{Applying Metric tensor and } \frac{dt}{d\tau} \text{ on both side} $$  

<br/>

$$ \begin{aligned} 
m \frac{d^2x_{\mu}}{d\tau^2} &= e ( \frac{\partial{A_{\alpha}}}{\partial{x_{\mu}}} \frac{dx^{\alpha}}{d\tau} - \frac{dA_{\mu}}{dx_{\alpha}} ) = e ( \frac{\partial{A_{\alpha}}}{\partial{x_{\mu}}} - \frac{dA_{\mu}}{dx_{\alpha}} ) \frac{dx^{\alpha}}{d\tau} \\
&= e F_{\mu \alpha} \frac{dx^{\alpha}}{d\tau} = e F_{\mu \alpha} U^{\alpha}
\end{aligned} $$  

$$ \text{where } F_{\mu \alpha}  = \frac{\partial{A_{\alpha}}}{\partial{x_{\mu}}} - \frac{\partial{A_{\mu}}}{\partial{x_{\alpha}}} $$

<br/>
<br/>

#### Maxwell's Equations
----
$$ \begin{aligned}  F^{\mu \alpha} = -F^{\alpha \mu } \text{, } F^{\mu \mu} = 0  \end{aligned} $$  

with natural units and Heaviside–Lorentz units. 
$$ \begin{aligned} c = 1, \epsilon_0 = 1, \mu_0 = 1 \end{aligned} $$  

$$ \text{let } F^{\mu \alpha} = \begin{pmatrix} 0 & E^x & E^y & E^z \\\ -E^x & 0 & B^z & -B^y \\\ -E^y & -B^z & 0 & B^x \\\ -E^z & B^y & -B^x & 0 \end{pmatrix} $$

$$ \begin{aligned} \text{let } J^{\mu} \text{ four current } (\rho, \vec{J})\end{aligned} $$
<br/>
then,

$$ \begin{aligned} F^{\mu \alpha},_{\alpha} = J^{\mu} \end{aligned} $$

$$ \begin{aligned} \text{when } \mu = 0 \text{, } \text{ } \text{ } F^{0 \alpha},_{\alpha} = J^{0} \end{aligned} $$

$$ \begin{aligned} \nabla \cdot E = \rho \end{aligned} $$

$$ \begin{aligned} \text{when } \mu = i \text{, } \text{ } \text{ } F^{i \alpha},_{\alpha} = J^{i} \end{aligned} $$

$$ \begin{aligned} -\frac{\partial{E}}{\partial{t}} + \nabla \times B = \vec{J}  \end{aligned} $$

<br/>
And, $$ F^{\mu \nu} $$ automatically holds Bianchi identity with four independent equations.  

$$  F^{\mu \nu},_{\gamma} + F^{\nu \gamma},_{\mu } + F^{\gamma \mu},_{\nu  } = 0 $$

<br/>

$$ \mu \leftrightarrow \nu, \mu \leftrightarrow \gamma, \nu \leftrightarrow \gamma $$ does not make any change.

It implies that it has $$ _4C_3 \text{ or } _4C_1 $$ equations. select three elements among {x, y, z, t}.

<br/>

When choosing {x, y, z} from {x, y, z, t}  

$$  F^{x y},_{z} + F^{y z},_{x } + F^{z x},_{y} = 0 $$  

$$  B^{z},_{z} + B^{x},_{x } + B^{y},_{y} = 0 $$  

$$  \nabla \cdot B = 0 $$  

For other three equations {x, y, t}, {x, z, t}, {y, z, t} from {x, y, z, t}  

$$  \frac{\partial{B}}{\partial{t}} + \nabla \times E = 0 $$  

Now we've just got Maxwell's equations here!

$$ \begin{aligned} \nabla \cdot E = \rho \end{aligned} $$  

$$ \begin{aligned} -\frac{\partial{E}}{\partial{t}} + \nabla \times B = \vec{J}  \end{aligned} $$  

$$  \nabla \cdot B = 0 $$  

$$  \frac{\partial{B}}{\partial{t}} + \nabla \times E = 0 $$  
