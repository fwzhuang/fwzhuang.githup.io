---
title: Projective Dynamics
tags: Simulation
---

projective dynamics方法，作为有限元法与PBD方法的桥接，可认为是更普通形式的PBD方法。

<!--more-->

### 隐式欧拉积分

隐式欧拉积分的表达式

$$ \begin{cases} q_{n+1}=q_{n} +hv_{n+1}  \cdots (1)  \\
v_{n+1} =v_{n}+hM^{-1}(f_{int}(q_{n+1})+f_{ext})  \cdots  (2)
\end{cases} $$

其中M为质量矩阵，h为time step, 将（2）代入（1）式，可得

$$　M(q_{n+1}- q_n-hv_n)  = h^2(f_{int}(q_{n+1})+ f_{ext})  \cdots  (3) $$

令
$$ s_n =  q_n + hv_n + h^2 M^{-1}fext$$  

则有

$$ \frac{1}{h^2}M(q_{n+1}- s_n)= f_{int}(q_{n+1}) $$

上式可转化为下面式子的优化问题，

$$ \begin{aligned}
& \int\frac{1}{h^2}M(q_{n+1}- s_n)dq_{n+1} - \int f_{int}(q_{n+1})dq_{n+1} \\
&=\frac{1}{h^2}\int M^{\frac{1}{2}}(q_{n+1}- s_n)d(M^{\frac{1}{2}}(q_{n+1}- s_n)) + \sum_i W_i(q_{n+1})\\
&=\frac{1}{2h^2}(M^{\frac{1}{2}}(q_{n+1}- s_n):M^{\frac{1}{2}}(q_{n+1}- s_n)) + \sum_i W_i(q_{n+1})\\
&=\frac{1}{2h^2}\|M^{\frac{1}{2}}(q_{n+1}- s_n)\|_F^2 + \sum_i W_i(q_{n+1})
\end{aligned} $$

即最小化
$$ min_{q_{n+1}} \frac{1}{2h^2}\|M^{\frac{1}{2}}(q_{n+1}- s_n)\|_F^2 + \sum_i W_i(q_{n+1}) \cdots  (4) $$

其中
$$ \frac{1}{2h^2}\|M^{\frac{1}{2}}(q_{n+1}- s_n)\|_F^2  \cdots  (5) $$

代表的是惯性势能加上外力（重力）的作用。而后一项代表的是内部的弹性势能， W代表材质系数矩阵。



---

If you like TeXt, don't forget to give me a star. :star2:

[![Star This Project](https://img.shields.io/github/stars/kitian616/jekyll-TeXt-theme.svg?label=Stars&style=social)](https://github.com/fwzhuang/fwzhuang.github.io)