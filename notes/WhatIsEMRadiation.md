<!-- TYPE: A / Learning Notes -->
# 【学习笔记】什么是电磁辐射？经典电动力学视角

> 本文属于《电动力学：经典与量子之间》合集中的**学习笔记**部分，主要记录我在重新学习经典电动力学辐射问题时的理解过程、困惑与阶段性认识。

---

## 1. 电磁辐射的定义

根据百科，电磁辐射是携带动量的电磁场波动，也可以看作光子（们）。频率的取值范围为$(0,\infty)$，真空中传播的速度为光速$c\approx3.0\times10^8$m/s. 

常见电磁辐射及其频率、波长、对应单光子能量及典型来源如下：

|  频段  |    频率范围     |   波长范围    |    单光子能量    | 典型来源     |
| :----: | :-------------: | :-----------: | :--------------: | ------------ |
| 无线电 |     kHz–GHz     |  300km-30cm   | 4.14peV-4.14ueV  | 闪电、天线   |
|  微波  |     GHz–THz     |  30cm-0.3mm   | 4.14ueV-4.14meV  | CMB、雷达    |
|  红外  |   THz-400THz    | 0.3mm-0.75um  |  4.14meV-1.66eV  | 热辐射       |
| 可见光 |   400–750 THz   |  700-400 nm   |  1.66eV-3.11eV   | 恒星、灯     |
|  紫外  | 750 THz-30 PHz  | 400 nm-10 nm  |   3.11eV-124eV   | 等离子体     |
| X 射线 | 30 PHz - 30 EHz | 10 nm - 10 pm | 124 eV - 124 keV | 同步辐射     |
| γ 射线 |    > 30 EHz     |    < 10 pm    |    > 124 keV     | 宇宙极端事件 |



---

## 2. 经典电动力学中的辐射

经典电动力学中，辐射是作为具有非惯性运动的源的Maxwell方程组的解的一部分自然出现的。考虑一个点粒子，其世界线为$Y^\mu(\tau)$, 洛伦兹规范下，Maxwell方程组可写为
$$
\square A^\mu=\mu_0 J^\mu, \text{with}\ \partial_\mu A^\mu=0,\ J^\mu=qc\int d\tau \dot{Y}^\mu(\tau)\delta^{4}(X-Y).
$$
其中$\delta^{4}(X-Y)=\delta(ct-Y^0)\delta^{3}(\vec{x}-\vec{y}(\tau))$, 上式的解为
$$
A^\mu(X)=\frac{\mu_0 q c}{4 \pi} \frac{\dot{Y}^\mu\left(\tau_{\star}\right)}{\left|R^\nu\left(\tau_{\star}\right) \dot{Y}_\nu\left(\tau_{\star}\right)\right|}
$$
其中$R^\mu\equiv X^\mu-Y^\mu(\tau)$, $\tau_{\star}$是$\delta^4$函数积分后确定的固有时解，满足$R^\mu(\tau_\star)R_\mu(\tau_\star)=0$. 场强张量为
$$
F_{\mu \nu}(X)=\frac{\mu_0 q c}{4 \pi} \frac{1}{R^\rho \dot{Y}_\rho}\left[\left(-c^2+R^\lambda \ddot{Y}_\lambda\right) \frac{R_\mu \dot{Y}_\nu-R_\nu \dot{Y}_\mu}{\left(R^\sigma \dot{Y}_\sigma\right)^2}+\frac{\ddot{Y}_\mu R_\nu-\ddot{Y}_\nu R_\mu}{R^\sigma \dot{Y}_\sigma}\right]
$$
其中正比于$1/R$的项即为辐射项，详细求解可见附录。

回到三维形式即为

可参见[1]: Chap. 6, Sec. 4, Sub. 4. P165-168;[2]: Chap. 14, Sec. 1. P661-665.

---

## 3. 与教材表述的对照

（不是复述教材，而是**对照你的理解与教材**）

- 教材是如何陈述的
- 哪一句话你觉得“理所当然但不真正明白”
- 哪些步骤在教材中被省略

可引用：
- Jackson / Landau / Griffiths 等（无需完整推导）

---

## 4. 一个或两个关键公式的角色说明（可选）

（**不是完整推导**）

- 这个公式“解决了什么问题”
- 如果没有它，物理图像哪里不闭合
- 它依赖了哪些假设

---

## 5. 当前仍然存在的疑问

（非常重要，不要回避）

- 哪些地方你还没想通
- 哪些地方你怀疑自己的理解
- 哪些问题你觉得“将来可能需要量子理论才能解释”

---

## 6. 小结（阶段性，而非结论）

- 这一轮学习你确认了什么
- 哪些误解被纠正了
- 下一步你打算继续看的方向

---

## 附录

- $A^\mu,F^{\mu\nu}$的求解

采用推迟 Green 函数求解四势

  达朗贝尔算符的推迟 Green 函数满足
$$
\square G_{\text{ret}}(X-X') = \delta^{(4)}(X-X')
$$
  其显式形式为
$$
G_{\text{ret}}(X-X') = \frac{1}{2\pi},\theta(X^0-X'^0),\delta!\big((X-X')^2\big)
$$
  因此势的解为
$$
A^\mu(X) = \mu_0 \int d^4X' , G_{\text{ret}}(X-X') J^\mu(X')
$$
  代入四流表达式：
$$
A^\mu(X)= \mu_0 q c \int d\tau , \dot Y^\mu(\tau), G_{\text{ret}}!\big(X - Y(\tau)\big)
$$

利用光锥 δ 函数完成固有时积分, 代入 Green 函数：
$$
A^\mu(X)= \frac{\mu_0 q c}{2\pi}\int d\tau , \dot Y^\mu(\tau),\theta!\big(X^0-Y^0(\tau)\big)\delta!\big(R^2(\tau)\big)
$$
其中
$$
R^\mu(\tau) \equiv X^\mu - Y^\mu(\tau)
$$

δ 函数的变量变换

$$
\delta(f(\tau))=\sum_{\tau_*}\frac{\delta(\tau-\tau_*)}{|f'(\tau_*)|}
$$
并注意
$$
\frac{d}{d\tau} R^2(\tau)= -2 R^\mu \dot Y_\mu
$$
得到
$$
\delta(R^2)= \frac{\delta(\tau-\tau_*)}{2|R\cdot \dot Y|}
$$
其中 (\tau_*) 由**推迟光锥条件**
$$
R^2(\tau_*)=0,\quad X^0>Y^0(\tau_*)
$$
唯一确定。
得到 Liénard–Wiechert 四势. 执行 (\tau) 积分后： 
$$
\boxed{ A^\mu(X)\frac{\mu_0 q c}{4\pi}\frac{\dot Y^\mu(\tau_*)}{R^\nu(\tau_*),\dot Y_\nu(\tau_*)}}
$$
这是**协变形式的 Liénard–Wiechert 势**，与你给出的结果完全一致。

场强张量的计算：(F_{\mu\nu}=\partial_\mu A_\nu-\partial_\nu A_\mu), (A^\mu(X)) **不仅显含 (X)**，还**隐含于 (\tau_\*(X))**。

推迟时间的导数

由光锥条件 [ R^2(\tau_*)=0 ] 对 (X^\alpha) 求导： 
$$
2R_\mu \left( \delta^\mu_\alpha\dot Y^\mu\frac{\partial\tau_*}{\partial X^\alpha}\right)=0
$$

解得
$$
\boxed{ \frac{\partial\tau_*}{\partial X^\alpha}\frac{R_\alpha}{R\cdot \dot Y}}
$$

对四势求导

  # 四势写成
$$
A^\mu\frac{\mu_0 q c}{4\pi}\frac{\dot Y^\mu}{\kappa},
\quad\kappa \equiv R\cdot\dot Y
$$

对 (X^\alpha) 求导： 
$$
\partial_\alpha A^\mu
\frac{\mu_0 q c}{4\pi} \left[ \frac{\ddot Y^\mu}{\kappa} \frac{\partial\tau_*}{\partial X^\alpha}\frac{\dot Y^\mu}{\kappa^2}\partial_\alpha \kappa\right]
$$

而 
$$
\partial_\alpha \kappa\dot Y_\alpha+\left(R\cdot\ddot Y\right)\frac{R_\alpha}{\kappa}
$$

计算 (F_{\mu\nu})

  # 整理并反对称化，得到 [ \boxed{ F_{\mu \nu}(X)

  \frac{\mu_0 q c}{4 \pi}
  \frac{1}{R\cdot \dot Y}
  \left[
  \left(-c^2+R\cdot\ddot Y\right)
  \frac{R_\mu \dot{Y}*\nu-R*\nu \dot{Y}*\mu}{(R\cdot\dot Y)^2}
  +
  \frac{\ddot{Y}*\mu R_\nu-\ddot{Y}*\nu R*\mu}{R\cdot\dot Y}
  \right]
  }
  ]

  ------

  ## 8. 辐射项的识别（物理解释）

  在远区 (R\to\infty)：

  - (R\cdot\dot Y \sim R)
  - 第一项 (\sim 1/R^2)：**近场（Coulomb + 速度场）**
  - 第二项 (\sim 1/R)：**真正的辐射场**

  因此：
  [
  \boxed{
  F^{\text{rad}}*{\mu\nu}
  \propto
  \frac{\ddot Y*\mu R_\nu-\ddot Y_\nu R_\mu}{R}
  }
  ]

  这表明：

  > **辐射并非附加假设，而是非惯性世界线的 Maxwell 方程解中必然出现的远区贡献**

  ------

  ## 9. 总结

  - Maxwell 方程 + 推迟 Green 函数 ⇒ Liénard–Wiechert 势
  - 推迟时间 (\tau_*(X)) 的隐式依赖是辐射产生的根源
  - (1/R) 项严格对应加速度，体现辐射的协变本质
  - 全过程完全保持 Lorentz 协变性

  ------

  ## 参考文献（权威来源）

  1. J. D. Jackson, *Classical Electrodynamics*, 3rd ed., Wiley (1998), Ch. 14
  2. L. D. Landau & E. M. Lifshitz, *The Classical Theory of Fields*, Butterworth-Heinemann (1975), §63
  3. F. Rohrlich, *Classical Charged Particles*, World Scientific (2007)
  4. S. Weinberg, *The Quantum Theory of Fields, Vol. I*, Cambridge University Press (1995), Appendix A

  ------

  如果你愿意，我可以进一步：

  - 推导非协变三维形式并与 Jackson 表达式对照
  - 计算 Poynting 向量并导出 Larmor/Liénard 辐射功率
  - 讨论自力、Abraham–Lorentz–Dirac 方程的起源

  请告诉我你希望深入的方向。

- 参考教材: 

  [1] David Tong, [Electromagnetism](https://www.damtp.cam.ac.uk/user/tong/em.html).

  [2] J. D. Jackson, Classical Electrodynamics, 3rd edition.

  

- 相关讲义或论文

- 给未来自己的提醒
