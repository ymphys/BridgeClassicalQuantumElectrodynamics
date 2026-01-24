<!-- TYPE: A / Learning Notes -->
# 【学习笔记】Abraham-Lorentz-Dirac方程与Landau Lifshitz方程

> 本文属于《电动力学：经典与量子之间》合集中的**学习笔记**部分，主要记录我在重新学习经典电动力学辐射问题时的理解过程、困惑与阶段性认识。

---

## 1. 经典电动力学中的辐射反作用力

经典电动力学中，Maxwell方程组描述了电流源如何产生电磁场，Lorentz力与Newton运动定理描述了粒子在电磁场中如何运动，联立这些方程似乎可以给出电磁现象的所有自洽描述。然而，当涉及到电子在自身的运动为源产生的电磁场中的运动时，会出现如下几个问题[^1]：

- 电子的自场在自身位置处发散
- 自作用力正比于电子加速度的一阶导数，运动方程具有三阶时间导数
- 若假设电子为非点粒子，需引入非电磁内应力维持其结构

本节介绍Abraham-Lorentz-Dirac方程和Landau-Lifshitz方程，作为经典电动力学框架下对辐射反作用的自洽描述。

---

## 2. Abraham-Lorentz-Dirac方程

由[Max Abraham](https://en.wikipedia.org/wiki/Max_Abraham), [Hendrik Lorentz](https://en.wikipedia.org/wiki/Hendrik_Lorentz)以及[P. A. M. Dirac](https://en.wikipedia.org/wiki/Paul_Dirac)命名，是Dirac在1938年将运动方程中的质量与Abraham-Lorentz力重整化后得到的[^2]。Dirac利用Maxwell方程$\partial_\mu F^{\mu\nu}=j^\nu$的解包含推迟解和超前解的特点，将其重新分解为对称和反对称部分：
$$
F^{\mu\nu}_S=\frac{1}{2}(F^{\mu\nu}_{\text{ret}}+F^{\mu\nu}_{\text{adv}}),\ F^{\mu\nu}_R=\frac{1}{2}(F^{\mu\nu}_{\text{ret}}-F^{\mu\nu}_{\text{adv}})
$$
其中推迟解和超前解可分别由对应的Green函数得到：
$$
G_{\text{ret}}(x)=\frac{c}{2\pi}\theta(x^0)\delta(x^2),\ G_{\text{adv}}(x)=\frac{c}{2\pi}\theta(-x^0)\delta(x^2),\\
G_{S}(x)=\frac{c}{4\pi}\delta(x^2),\ G_{R}(x)=\frac{c}{4\pi}\text{sgn}(x^0)\delta(x^2),\
$$
假设粒子世界线为$y=y(\tau)$，则对称和反对称势分别为
$$
A^\mu_S=\frac{\mu_0qc}{4\pi}\int d\tau v^\mu(\tau)\delta(\Delta^2),\ A^\mu_R=\frac{\mu_0qc}{4\pi}\int d\tau v^\mu(\tau)\text{sgn}(\Delta^0)\delta(\Delta^2),
$$
其中$\Delta^\mu=x^\mu-y^\mu(\tau),\Delta^2=\Delta^\mu\Delta_\mu,\Delta^0$为其0-分量。当我们将观测点（场点$x$）取在粒子世界线上$x=y(\tau_0)$时，展开可得
$$
y(\tau)=y(\tau_0)+(\tau-\tau_0)\frac{dy(\tau)}{d\tau}\bigg|_{\tau=\tau_0}+\frac{1}{2!}(\tau-\tau_0)^2\frac{d^2y(\tau)}{d\tau^2}\bigg|_{\tau=\tau_0}+\ldots=y(\tau_0)+(\tau-\tau_0)v^\mu_0+\frac{1}{2!}(\tau-\tau_0)^2a^\mu_0+\frac{1}{3!}(\tau-\tau_0)^3\dot{a}^\mu_0+\ldots
$$
因此Minkowski距离可展开为
$$
\lim_{x\to y(\tau_0)}\Delta^2=(y(\tau_0)-y(\tau))^2=(\tau-\tau_0)^2c^2-\frac{1}{12}(\tau-\tau_0)^4a^\mu_0a_{\mu0}+\mathcal{O}((\tau-\tau_0)^5)
$$
其中用到$v^\mu_0v_{\mu0}=c^2,v^\mu_0a_{\mu0}=0$以及$v^\mu_0\dot{a}_{\mu0}=-a^\mu_0a_{\mu0}$. 进一步将上述Minkowski距离代入$\delta$函数
$$
\delta((y(\tau_0)-y(\tau))^2)=\delta((\tau-\tau_0)^2c^2[1-\frac{1}{12c^2}(\tau-\tau_0)^2a^\mu_0a_{\mu0}+\mathcal{O}((\tau-\tau_0)^3)])
$$
由$\delta$函数性质可得，在$x\to y(\tau_0)$时，令$u\equiv\tau-\tau_0$，保留领头阶可得
$$
\delta((y(\tau_0)-y(\tau))^2)=\frac{1}{2c^2|u|}(\delta(u^+)+\delta(u^-))
$$
求得对称势为
$$
A^{\mu}_S=\frac{\mu_0q}{8\pi c}\int d\tau \frac{v^\mu(\tau)}{|\tau-\tau_0|}(\delta(u^+)+\delta(u^-))
$$
只要场点在粒子世界线上，对称部分即发散。

反对称部分为
$$
A^\mu_R=-\frac{\mu_0q}{8\pi c}\int d\tau\frac{v^\mu(\tau)}{|u|}[\delta(u^+)-\delta(u^-)]=-\frac{\mu_0q}{4\pi c}\int du v^\mu(u+\tau_0)\frac{d\delta(u)}{du}=\frac{\mu_0q}{4\pi c^2}a^\mu(\tau_0),
$$
可以看到即使在粒子世界线上发散项亦严格相消，仅留下有限项。由在任意场点$x$处反对称势可求得反对称部分的场为
$$
F^{\mu\nu}_R=\partial^\mu A^\nu_R(x)-\partial^\nu A^\mu_R(x)=\frac{\mu_0qc}{2\pi}\int d\tau \ \text{sgn}(\Delta^0)\delta'(\Delta^2)[v^\nu(\tau)\Delta^\mu-v^\mu(\tau)\Delta^\nu]
$$
据此求得粒子受到的来自该场的力
$$
F^\mu_{\text{rad}}=qF^{\mu\nu}v_{0\nu}=\frac{\mu_0cq^2}{2\pi}\int d\tau \ \text{sgn}(\Delta^0)\delta'(\Delta^2)[v\cdot v_0\Delta^\mu-\Delta\cdot v_0v^\mu]=\frac{\mu_0cq^2}{2\pi}\int du \ \text{sgn}(-u)\delta'(\Delta^2)\left[\frac{1}{2}c^2u^2a_0^\mu+\frac{1}{3}u^3(a_0^2v_0^\mu+c^2\dot{a}_0^\mu)\right]
$$
积分中由于$\text{sng}(-u)$是奇函数，$\delta'(\Delta^2)$为偶函数，$[\ldots]$中第一项正比于$u^2$为偶函数，积分为0；第二项保留，且利用对称性可得
$$
F^\mu_{\text{rad}}=-\frac{\mu_0cq^2}{3\pi}(a_0^2v_0^\mu+c^2\dot{a}_0^\mu)\int_0^\infty du \delta'(\Delta^2)u^3=\frac{\mu_0q^2}{6\pi c}(\dot{a}_0^\mu+\frac{a_0^2}{c^2}v_0^\mu)
$$
即具有Lorentz协变的Abraham-Lorentz力，注意括号中第二项有的教科书中符号为负，来自于度规选择的区别，本文选择$(+,-,-,-)$度规。

对应的运动方程
$$
\frac{dp^\mu}{d\tau}=F^{\text{rad}}_{\mu}+\frac{q}{c}F^{\mu\nu}v_\nu
$$
即为Abraham-Lorentz-Dirac方程(ALD方程)。可以看到，与非相对论情形相比，ALD力具有协变性，但是对应运动方程仍然是时间的三阶导数，因此预加速(preacceleration)与奔离解(runaway solution)仍然存在。





---

## 3. Landau-Lifshitz方程

（不是复述教材，而是**对照你的理解与教材**）

- 教材是如何陈述的
- 哪一句话你觉得“理所当然但不真正明白”
- 哪些步骤在教材中被省略

可引用：
- Jackson / Landau / Griffiths 等（无需完整推导）

---

## 6. 小结（阶段性，而非结论）

- 这一轮学习你确认了什么
- 哪些误解被纠正了
- 下一步你打算继续看的方向

---

## 附录

- 脚注

  [^1]: [【学习笔记】经典电动力学中的辐射](https://zhuanlan.zhihu.com/p/1988653319149877095)
  [^2]: Paul Adrien Maurice Dirac. Classical theory of radiating electrons. [**Proc. A** 1 August 1938; 167 (929): 148–169.](https://royalsocietypublishing.org/rspa/article/167/929/148/5807/Classical-theory-of-radiating-electrons)
  
- 参考教材

- 相关讲义或论文

- 给未来自己的提醒
