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

### 辐射场与辐射功率

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

由此可以计算Poynting矢量，
$$
\mathbf{S}=\frac{q^2}{16 \pi^2 \epsilon_0 c^3} \frac{|\hat{\mathbf{R}} \times[(\hat{\mathbf{R}}-\mathbf{v} / c) \times \mathbf{a}]|^2}{\kappa^6 R^2} \hat{\mathbf{R}}
$$
公式中的每一项都是在推迟时间$t'$计算得到的, $t'+R(t')/c=t$, 因此每单位时间$dt'$辐射能量的角分布为
$$
\frac{d \mathcal{P}}{d \Omega}=\kappa R^2 \mathbf{S} \cdot \hat{\mathbf{R}}=\frac{q^2}{16 \pi^2 \epsilon_0 c^3} \frac{|\hat{\mathbf{R}} \times[(\hat{\mathbf{R}}-\mathbf{v} / c) \times \mathbf{a}]|^2}{\kappa^5}
$$
总辐射功率为
$$
\mathcal{P}=\frac{q^2}{6 \pi \epsilon_0 c^3} \gamma^4\left(a^2+\frac{\gamma^2}{c^2}(\mathbf{v} \cdot \mathbf{a})^2\right)
$$
这实际上这是相对论版本的**Lamor公式**，也称为*Lienard推广的Lamor公式*。下面针对几种典型情况给出辐射功率：

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
这被称为**Lamor公式**。

更进一步地，考虑电子在频率为$\omega$, 振幅为$E_0$的外电场作用下运动，如场强较弱，电子运动速度远远小于光速，可近似得到$a=q_eE_0/m_e$, 代入Lamor公式可得电子辐射总功率
$$
\overline{\mathcal{P}}_{\text {radiated }}=\frac{\mu_0 q_e^4 E_0^2}{12 \pi m_e^2 c}
$$

如果将其和入射电磁波功率密度$\bar{S}_{\text {incident}}$比较，则可得到Thomson散射截面
$$
\sigma=\frac{\overline{\mathcal{P}}_{\text {radiated }}}{\bar{S}_{\text {incident }}}=\frac{\mu_0^2 q_e^4}{6 \pi m^2 c^2}=\frac{8 \pi}{3} r_e^2
$$
其中$\bar{S}_{\text {incident}}=cE_0^2/(2\mu_0)$, $r_e=q_e^4/(4\pi\epsilon_0mc^2)$是电子的经典半径。

### 辐射反作用

上面的讨论给出了电子如何产生电磁辐射，以及辐射功率的角分布、总功率，根据能量守恒，电子一定在损失能量。基于能量损失，我们可以计算辐射对电子的反作用。不幸的是，这种计算有其局限性：辐射能量并不等于电子在某一时刻损失的总能量，还应包含速度变化带来的自场（库仑场）能量变化，因此我们只能在时间平均的意义上通过辐射损失能量计算辐射反作用力，且要求系统在$t=t_1,t_2$时处于完全相同的状态。周期性运动显然是满足这种要求的，对此可以得到
$$
\mathbf{F}_{\mathrm{rad}}=\frac{\mu_0 q^2}{6 \pi c} \dot{\mathbf{a}} .
$$
上式是对非相对论情况的辐射功率计算得到的，称为**Abraham-Lorentz公式**[^2]。虽然它满足了能量守恒的要求，但其对加速度变化率的依赖导致运动方程从二阶微分方程变为三阶，这带来一些令人难以接受的结果，比如加速度的发散解，或破坏因果性的解（外力施加之前就开始加速），而且这两种情况只能消去一种。上述情况在相对论情形下仍然存在，$K_{\mathrm{rad}}^\mu=\frac{\mu_0 q^2}{6 \pi c}\left(\frac{d \alpha^\mu}{d \tau}-\frac{1}{c^2} \alpha^\nu\alpha_\nu \eta^\mu\right)$.[^3]

既然能量守恒无法给出令人满意的辐射反作用力，我们只能计算粒子的场对自身的作用力，不幸的是这依然无法简单直接地进行，因为经典电动力学中，电子产生的场在趋近其自身时发散。如果我们假设电子不是点粒子，而是具有一定的空间分布（形状因子, form factor），则**自作用力(self-force)**的确是可以计算的，具体的结果自然与假设的空间分布有关，但当我们对计算结果取点粒子极限，仍然可以得到一些有意义的结果。一般而言，自作用力的结果具有如下结构：
$$
F_{\text{self}}=\frac{q^2}{4\pi\epsilon_0}\left[-A\frac{a(t)}{c^2\ell}+\frac{2\dot{a}(t)}{3c^3}+\mathcal{O}(\ell)\right]
$$
其中$\ell$是电子形状因子的特征尺度，第一项会贡献到电子的质量，系数$A$与所取的形状因子有关，对Griffith所取的dumbbell 形状因子，第一项恰好对应电子的静电势能[^4]，对Lorentz所取的球形形状因子则会多出一个3/4[^5]. 然而该项在点粒子极限下发散，对应电子的质量发散。

有趣的是，第二项与所取形状因子无关，且在点粒子极限下仍然存在，对应的正是Abraham-Lorentz力。





[^1]: $A^\mu,F^{\mu\nu}$的详细求解可参见[1]: Chap. 6, Sec. 4, Sub. 4. P165-168;[2]: Chap. 14, Sec. 1. P661-665.
[^2]: $\mathbf{F}_{\mathrm{rad}}$的求解参见[2]: Chap. 11, Sec. 2, Sub. 2. P466-467.
[^3]: 见[2]: Prob. 12.70, P545.
[^4]: 见[2]: Chap. 11, Sec. 2, Sub. 3. P469-472.
[^5]: 见[3]: Chap. 16, Sec. 3. P750-755.



---

## 3. 量子电动力学中的辐射

量子电动力学中，光子是规范粒子，传递电磁相互作用，因此所有的光子归根结底都来自带电荷的费米子顶点。



---

## 4. 小结

- 这一轮学习你确认了什么
- 哪些误解被纠正了
- 下一步你打算继续看的方向

---

## 附录


- 参考教材: 

  [1] David Tong, [Electromagnetism](https://www.damtp.cam.ac.uk/user/tong/em.html).

  [2] D. J. Griffith, Introduction to Electrodynamics.
  
  [3] J. D. Jackson, Classical Electrodynamics, 3rd edition.