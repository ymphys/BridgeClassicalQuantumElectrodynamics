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

由[Max Abraham](https://en.wikipedia.org/wiki/Max_Abraham), [Hendrik Lorentz](https://en.wikipedia.org/wiki/Hendrik_Lorentz)以及[P. A. M. Dirac](https://en.wikipedia.org/wiki/Paul_Dirac)命名，是Dirac在1938年将运动方程中的质量与Abraham-Lorentz力重整化后得到的[^2]，在[-,+,+,+]度规下，
$$
F^{\text{rad}}_\mu=\frac{\mu_0q^2}{6\pi mc}\left[\frac{d^2p_\mu}{d\tau^2}-\frac{p_\mu}{m^2c^2}\left(\frac{dp_\nu}{d\tau}\frac{dp^\nu}{d\tau}\right)\right],
$$
结合相对论协变的Lamor公式
$$
P=\frac{\mu_0q^2a^2\gamma^6}{6\pi c},
$$
可以验证
$$
\frac{1}{\Delta t}\int_0^{t}Pdt'=\frac{1}{\Delta t}\int_0^{t}\mathbf{F}^{\text{rad}}\cdot\mathbf{v}dt'
$$
其中
$$
p^\mu=mv^\mu=m\gamma(c,\mathbf{v}),\ \frac{dp^\mu}{d\tau}=m\frac{dv^\mu}{dt}\frac{dt}{d\tau}=m\gamma(\frac{\gamma^3}{c}\mathbf{v}\cdot\mathbf{a},)
$$


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
