<!-- TYPE: A / Learning Notes -->

# 【学习笔记】什么是电磁辐射？

> 本文属于《电动力学：经典与量子之间》合集中的**学习笔记**部分，主要记录我在重新学习辐射问题时的困惑、理解与阶段性认识。

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

经典电动力学中，辐射是作为具有非惯性运动的源的Maxwell方程组的解的一部分自然出现的。考虑一个点粒子，其世界线为$Y^\mu(\tau)$, 洛伦兹规范$\partial_\mu A^\mu=0$下，Maxwell方程组可写为
$$
\partial_\mu F^{\mu\nu}=\square A^\mu=\mu_0 J^\mu,\ J^\mu=qc\int d\tau \dot{Y}^\mu(\tau)\delta^{4}(X-Y).
$$
其中$\delta^{4}(X-Y)=\delta(ct-Y^0)\delta^{3}(\vec{x}-\vec{y}(\tau))$, 上式的解为[^1]
$$
A^\mu(X)=\frac{\mu_0 q c}{4 \pi} \frac{\dot{Y}^\mu\left(\tau_{\star}\right)}{\left|R^\nu\left(\tau_{\star}\right) \dot{Y}_\nu\left(\tau_{\star}\right)\right|}
$$
其中$R^\mu\equiv X^\mu-Y^\mu(\tau)$, $\tau_{\star}$是$\delta^4$函数积分后确定的固有时解，满足$R^\mu(\tau_\star)R_\mu(\tau_\star)=0,R^0(\tau)>0$. 场强张量为
$$
F_{\mu \nu}(X)=\frac{\mu_0 q c}{4 \pi} \frac{1}{R^\rho \dot{Y}_\rho}\left[\left(-c^2+R^\lambda \ddot{Y}_\lambda\right) \frac{R_\mu \dot{Y}_\nu-R_\nu \dot{Y}_\mu}{\left(R^\sigma \dot{Y}_\sigma\right)^2}+\frac{\ddot{Y}_\mu R_\nu-\ddot{Y}_\nu R_\mu}{R^\sigma \dot{Y}_\sigma}\right]
$$
其中正比于$1/R$的项即为辐射项，回到三维形式即为

$$
\mathbf{E}(\mathbf{x}, t)=\frac{q}{4 \pi \epsilon_0}\left[\frac{\hat{\mathbf{R}}-\mathbf{v} / c}{\gamma^2 \kappa^3 R^2}+\frac{\hat{\mathbf{R}} \times[(\hat{\mathbf{R}}-\mathbf{v} / c) \times \mathbf{a}]}{\kappa^3 R c^2}\right]_{\mathrm{ret}},\ \kappa=1-\frac{\hat{\mathbf{R}} \cdot \mathbf{v}}{c}
$$

$$
\mathbf{B}=\frac{1}{c}[\hat{\mathbf{R}}]_{\mathrm{ret}} \times \mathbf{E}=-\frac{q \mu_0}{4 \pi}\left[\frac{\hat{\mathbf{R}} \times \mathbf{v}}{\gamma^2 \kappa^3 R^2}+\frac{(\hat{\mathbf{R}} \cdot \mathbf{a})(\hat{\mathbf{R}} \times \mathbf{v} / c)+\kappa \hat{\mathbf{R}} \times \mathbf{a}}{c \kappa^3 R}\right]_{\mathrm{ret}}
$$

由此可以计算Poynting矢量，进而得出辐射功率的角分布以及总辐射功率。这里给出几种典型的辐射功率：

**bremsstrahlung**

即轫致辐射，也称为“刹车”辐射，出现在电子加速度与速度方向平行/反平行时。
$$
\frac{d \mathcal{P}}{d \Omega}=\frac{q^2 a^2}{16 \pi^2 \epsilon_0 c^3} \frac{\sin ^2 \theta}{(1-(v / c) \cos \theta)^5},\ \mathcal{P}=\frac{q^2 \gamma^6 a^2}{6 \pi \epsilon_0 c^3}
$$

**cyclotron and synchrotron radiation**

非相对论情况下称为cyclotron radiation, 即回旋辐射；相对论情况下为synchrotron radiation, 即同步辐射。
$$
\frac{d \mathcal{P}}{d \Omega}=\frac{q^2 a^2}{16 \pi^2 \epsilon_0 c^3} \frac{1}{(1-(v / c) \cos \theta)^3}\left(1-\frac{\sin ^2 \theta \cos ^2 \phi}{\gamma^2(1-(v / c) \cos \theta)^2}\right)\ \mathcal{P}=\frac{q^2 \gamma^4 a^2}{6 \pi \epsilon_0 c^3}
$$
**electric dipole radiation**

即电偶极辐射，考虑一个电荷量为Q的带电粒子以频率$\omega$振荡，振幅为$d$，电偶极矩$p=Qd$, 时间平均后的辐射功率为
$$
\overline{\mathcal{P}}=\frac{\mu_0 p^2 \omega^4}{12 \pi c}=\frac{Q^2 a^2}{12 \pi \epsilon_0 c^3}
$$
这被称为Lamor公式。

更进一步地，考虑电子在频率为$\omega$, 振幅为$E_0$的外电场作用下运动，如场强较弱，电子运动速度远远小于光速，可近似得到$a=q_eE_0/m_e$, 代入Lamor公式可得电子辐射总功率
$$
\overline{\mathcal{P}}_{\text {radiated }}=\frac{\mu_0 q_e^4 E_0^2}{12 \pi m_e^2 c}
$$

如果将其和入射电磁波功率密度$\bar{S}_{\text {incident}}$比较，则可得到Thomson散射截面
$$
\sigma=\frac{\overline{\mathcal{P}}_{\text {radiated }}}{\bar{S}_{\text {incident }}}=\frac{\mu_0^2 q_e^4}{6 \pi m^2 c^2}=\frac{8 \pi}{3} r_e^2
$$
其中$\bar{S}_{\text {incident}}=cE_0^2/(2\mu_0)$, $r_e=q_e^4/(4\pi\epsilon_0mc^2)$是电子的经典半径。

[^1]: $A^\mu,F^{\mu\nu}$​的详细求解可参见[1]: Chap. 6, Sec. 4, Sub. 4. P165-168;[2]: Chap. 14, Sec. 1. P661-665.

---

## 3. 量子电动力学中的辐射

量子电动力学中，光子是规范粒子，传递电磁相互作用，因此所有的光子归根结底都来自带电荷的费米子顶点。



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


- 参考教材: 

  [1] David Tong, [Electromagnetism](https://www.damtp.cam.ac.uk/user/tong/em.html).

  [2] J. D. Jackson, Classical Electrodynamics, 3rd edition.