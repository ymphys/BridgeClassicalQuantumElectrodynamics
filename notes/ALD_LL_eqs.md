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
其中$\Delta^\mu=x^\mu-y^\mu(\tau),\Delta^2=\Delta^\mu\Delta_\mu,\Delta^0$为其0-分量。积分$d\tau$的范围是$(-\infty,\infty)$，表示对过去和未来所有时刻的贡献进行累加，当我们需要考虑粒子在特定时刻$\tau_0$受到的力时，将观测点（场点$x$）取在粒子世界线上$x=y(\tau_0)$时，令$u\equiv\tau-\tau_0$，Minkowski距离可展开为
$$
\Delta^2=(y(\tau_0)-y(\tau))^2=u^2c^2-\frac{1}{12}u^4a^\mu_0a_{\mu0}+\mathcal{O}(u^5)
$$
其中用到$v^\mu_0v_{\mu0}=c^2,v^\mu_0a_{\mu0}=0$以及$v^\mu_0\dot{a}_{\mu0}=-a^\mu_0a_{\mu0}$. 进一步将上述Minkowski距离代入$\delta$函数，并保留领头阶可得
$$
\delta((y(\tau_0)-y(\tau))^2)=\delta(u^2c^2[1-\frac{1}{12c^2}u^2a^\mu_0a_{\mu0}+\mathcal{O}(u^3)])=\frac{1}{2c^2|u|}(\delta(u^+)+\delta(u^-))
$$
反对称部分的势为
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

对称部分的势为
$$
A^{\mu}_S=\frac{\mu_0q}{8\pi c}\int d\tau \frac{v^\mu(\tau)}{|\tau-\tau_0|}(\delta(u^+)+\delta(u^-))
$$
只要场点在粒子世界线上，对称部分即发散。由在任意场点$x$处对称势可求得对称部分的场为

$$
F^{\mu\nu}_S=\frac{\mu_0qc}{2\pi}\int d\tau \delta'(\Delta^2)[v^\nu(\tau)\Delta^\mu-v^\mu(\tau)\Delta^\nu]
$$
粒子在$\tau_0$时刻受到的来自对称部分场的力为
$$
F^\mu_{S}=qF^{\mu\nu}_Sv_{0\nu}=\frac{\mu_0cq^2}{2\pi}\int du \delta'(\Delta^2)\left[\frac{1}{2}c^2u^2a_0^\mu+\frac{1}{3}u^3(a_0^2v_0^\mu+c^2\dot{a}_0^\mu)\right]
$$
再次借助奇偶性分析可知$[\ldots]$中的第二项为0，而第一项会给出发散的结果，引入正则化$\Delta^2\to\Delta^2-\epsilon^2$，积分可得
$$
F^\mu_{S}=\frac{\mu_0c^3q^2}{4\pi}a_0^\mu\int du \delta'(\Delta^2-\epsilon^2)u^2=\frac{\mu_0c^3q^2}{4\pi}a_0^\mu(-\frac{1}{2c^3\epsilon})=-\frac{\mu_0q^2}{8\pi\epsilon}a_0^\mu
$$
将对称和反对称部分的力均代入运动方程可得
$$
\frac{dp^\mu}{d\tau}=F_{\text{rad}}^{\mu}+F_{S}^{\mu}+\frac{q}{c}F^{\mu\nu}v_\nu
$$

$$
m_{\text{bare}}a_0^\mu=\frac{\mu_0q^2}{6\pi c}(\dot{a}_0^\mu+\frac{a_0^2}{c^2}v_0^\mu)-\frac{\mu_0q^2}{8\pi\epsilon}a_0^\mu+\frac{q}{c}F^{\mu\nu}v_\nu
$$

即为Abraham-Lorentz-Dirac方程(ALD方程)。如定义
$$
\delta m=\frac{\mu_0q^2}{8\pi\epsilon},\ m_{\text{phys}}=m_{\text{bare}}+\delta m
$$
则发散部分被吸收进裸质量中，物理上可观测的质量仍然是有限的，这种思想即为**重整化**。

可以看到，与非相对论情形相比，ALD力具有协变性，但是对应运动方程仍然是时间的三阶导数，因此预加速(preacceleration)与奔离解(runaway solution)仍然存在。


---

## 3. Landau-Lifshitz方程

如上节我们看到的，ALD 方程是一个关于时间的三阶微分方程（包含 $\dot{a}^\mu$），这在数学上导致了不符合物理的预加速与奔离解。Landau 和 Lifshitz 指出，在经典力学范围内，辐射反作用力相对于外部 Lorentz 力通常是很小的。因此，我们可以将辐射项视为微扰，通过将零阶运动方程代入一阶项来降阶。具体做法如下：

首先，定义一个特征时间常数 $\tau_e$：
$$
\tau_e = \frac{\mu_0 q^2}{6\pi m c}
$$
则 ALD 方程写为：
$$
a^\mu = \frac{q}{mc} F^{\mu\nu} v_\nu + \tau_e \left( \dot{a}^\mu + \frac{a^2}{c^2} v^\mu \right)
$$
当辐射项极小时（$\tau_e \to 0$），粒子的加速度由 Lorentz 力决定。这可以作为零阶近似，对零阶方程式两边关于固有时 $\tau$ 求导：
$$
\dot{a}^\mu = \frac{d}{d\tau} \left( \frac{q}{mc} F^{\mu\nu} v_\nu \right) = \frac{q}{mc} \left[ \left( \frac{d F^{\mu\nu}}{d\tau} \right) v_\nu + F^{\mu\nu} \left( \frac{dv_\nu}{d\tau} \right) \right]\approx \frac{q}{mc} \left[ (v^\alpha \partial_\alpha F^{\mu\nu}) v_\nu + F^{\mu\nu} \left( \frac{q}{mc} F_{\nu\lambda} v^\lambda \right) \right]
$$
其中第一项利用了全微分关系 $\frac{d F^{\mu\nu}}{d\tau} = \frac{\partial F^{\mu\nu}}{\partial x^\alpha} \frac{dx^\alpha}{d\tau} = v^\alpha \partial_\alpha F^{\mu\nu}$，第二项代入了零阶加速度作为近似。整理得：
$$
\dot{a}^\mu \approx \frac{q}{mc} (v^\alpha \partial_\alpha F^{\mu\nu}) v_\nu + \frac{q^2}{m^2 c^2} F^{\mu\nu} F_{\nu\lambda} v^\lambda
$$
对$a^2$项亦代入零级加速度近似，
$$
a^2 \approx \left( \frac{q}{mc} F^{\alpha\beta} v_\beta \right) \left( \frac{q}{mc} F_{\alpha\lambda} v^\lambda \right) = \frac{q^2}{m^2 c^2} (F^{\alpha\beta} v_\beta) (F_{\alpha\lambda} v^\lambda)
$$
得到 Landau-Lifshitz 方程
$$
a^\mu = \frac{q}{mc} F^{\mu\nu} v_\nu + \frac{q}{mc} \tau_e (v^\alpha \partial_\alpha F^{\mu\nu}) v_\nu + \left(\frac{q}{mc}\right)^2\tau_e\left[ F^{\mu\nu} F_{\nu\lambda} v^\lambda + \frac{v^\mu}{c^2}(F^{\alpha\beta} v_\beta) (F_{\alpha\lambda} v^\lambda) \right]
$$
可见其由三部分组成，第一项由Lorentz力贡献，第二项是梯度项，描述了由于外场在粒子运动范围内的非均匀性导致的修正，第三项是平方项，描述了即使在均匀场中，粒子由于偏转而产生的辐射能量流失及其对轨迹的修正。

可以看到，通过迭代代入，我们成功地将ALD方程转换为了一个可以实际计算的“唯象有效方程”。应该注意，这种近似仅在辐射力远小于 Lorentz 力时有效。

---

## 4. 同步辐射衰减

作为一个LL方程的实际应用，考虑同步辐射中电子的能量损失。为简单起见，假设电子处于匀强磁场$\mathbf{B}=B\hat{z}$中，电磁场张量为$F^{21}=-F^{12}=B$, 其余分量为0，梯度项也为0，LL方程为
$$
a^0 = \tau_e\left(\frac{q}{mc^2}\right)^2v^0(F^{\alpha\beta} v_\beta) (F_{\alpha\lambda} v^\lambda)
$$
定义$v_\perp^2=v_x^2+v_y^2$, 可得$(F^{\alpha\beta} v_\beta) (F_{\alpha\lambda} v^\lambda)=-B^2v_\perp^2$. 进而由$a^0=dv^0/d\tau$以及$v^\mu=\gamma(c,\vec{v})$, $dt=\gamma d\tau$可得
$$
\frac{d\gamma mc^2}{dt}=-\tau_e\frac{q^2B^2}{mc^2}v_\perp^2
$$
代入$\tau_e$的定义可得相对论协变的Lamor辐射功率



- 这一轮学习你确认了什么
- 哪些误解被纠正了
- 下一步你打算继续看的方向

---

## 附录

- 脚注

  [^1]: [【学习笔记】经典电动力学中的辐射](https://zhuanlan.zhihu.com/p/1988653319149877095)
  [^2]: Paul Adrien Maurice Dirac. Classical theory of radiating electrons. [**Proc. A** 1 August 1938; 167 (929): 148–169.](https://royalsocietypublishing.org/rspa/article/167/929/148/5807/Classical-theory-of-radiating-electrons)
  
- 参考教材
