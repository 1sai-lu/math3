# 拉普拉斯變換求解微分方程

## 題目
$$\frac{d^2x}{dt^2} - 3\frac{dx}{dt} + 2x = \delta(t)$$

**初始條件：**
* $x(0) = 0$
* $x'(0) = 0$

---

## 詳細求解步驟

### Step 1: 對微分方程兩邊進行拉普拉斯變換 (Laplace Transform)
設 $\mathcal{L}\{x(t)\} = X(s)$。

根據拉普拉斯變換的微分性質：
* $\mathcal{L}\{\frac{dx}{dt}\} = sX(s) - x(0)$
* $\mathcal{L}\{\frac{d^2x}{dt^2}\} = s^2X(s) - sx(0) - x'(0)$

以及單位脈衝函數（狄拉克 $\delta$ 函數）的拉普拉斯變換：
* $\mathcal{L}\{\delta(t)\} = 1$

將初始條件 $x(0) = 0$ 與 $x'(0) = 0$ 代入上述公式中，可得：
* $\mathcal{L}\{\frac{dx}{dt}\} = sX(s)$
* $\mathcal{L}\{\frac{d^2x}{dt^2}\} = s^2X(s)$

將這些結果代回原微分方程：
$$s^2X(s) - 3sX(s) + 2X(s) = 1$$

---

### Step 2: 求解 $X(s)$
提出公因式 $X(s)$：
$$(s^2 - 3s + 2)X(s) = 1$$

將多項式進行因式分解：
$$(s - 1)(s - 2)X(s) = 1$$

因此，我們可以得到 $X(s)$ 的表達式：
$$X(s) = \frac{1}{(s - 1)(s - 2)}$$

---

### Step 3: 部分分式拆解 (Partial Fraction Decomposition)
將 $X(s)$ 拆解為部分分式：
$$\frac{1}{(s - 1)(s - 2)} = \frac{A}{s - 1} + \frac{B}{s - 2}$$

利用通分或留數法（Heaviside 蓋住法）求係數 $A$ 與 $B$：
* **求 $A$：** 兩邊同乘 $(s - 1)$ 並令 $s = 1$
  $$A = \frac{1}{1 - 2} = -1$$

* **求 $B$：** 兩邊同乘 $(s - 2)$ 並令 $s = 2$
  $$B = \frac{1}{2 - 1} = 1$$

因此，$X(s)$ 可以寫成：
$$X(s) = \frac{1}{s - 2} - \frac{1}{s - 1}$$

---

### Step 4: 進行反拉普拉斯變換 (Inverse Laplace Transform)
對 $X(s)$ 取反變換以求得原函數 $x(t)$：
$$x(t) = \mathcal{L}^{-1}\{X(s)\} = \mathcal{L}^{-1}\{\frac{1}{s - 2}\} - \mathcal{L}^{-1}\{\frac{1}{s - 1}\}$$

根據常用拉普拉斯變換公式 $\mathcal{L}^{-1}\{\frac{1}{s - a}\} = e^{at}$，可得終解：
$$x(t) = e^{2t} - e^{t} \quad (t \ge 0)$$

---

## 最終答案
$$x(t) = e^{2t} - e^{t}$$
