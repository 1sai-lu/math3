# 傅立葉級數求解

## 題目
令 $f(x) = x^2$，其中 $x \in [-\pi, \pi]$。
求函數 $f(x)$ 之傅立葉級數。

---

## 傅立葉級數公式
在區間 $[-\pi, \pi]$ 上，一個週期函數 $f(x)$ 的傅立葉級數展開式為：
$$f(x) = \frac{a_0}{2} + \sum_{n=1}^{\infty} (a_n \cos(nx) + b_n \sin(nx))$$

其中傅立葉係數的計算公式如下：
* $a_0 = \frac{1}{\pi} \int_{-\pi}^{\pi} f(x) dx$
* $a_n = \frac{1}{\pi} \int_{-\pi}^{\pi} f(x) \cos(nx) dx$
* $b_n = \frac{1}{\pi} \int_{-\pi}^{\pi} f(x) \sin(nx) dx$

---

## 詳細求解步驟

### Step 1: 分析函數奇偶性 (Parity Analysis)
觀察給定的函數：
$$f(-x) = (-x)^2 = x^2 = f(x)$$

因為 $f(-x) = f(x)$，所以 $f(x) = x^2$ 是一個**偶函數 (Even Function)**。

根據奇偶函數的性質：
1. 偶函數與奇函數 $\sin(nx)$ 的乘積為奇函數，因此在對稱區間 $[-\pi, \pi]$ 上的積分為 0。
   所以：**$b_n = 0$**。
2. 偶函數在對稱區間 $[-\pi, \pi]$ 上的積分可以簡化為 $[0, \pi]$ 區間積分的 2 倍。

---

### Step 2: 計算係數 $a_0$
利用偶函數性質簡化公式：
$$a_0 = \frac{2}{\pi} \int_{0}^{\pi} x^2 dx$$

進行積分：
$$a_0 = \frac{2}{\pi} [ \frac{x^3}{3} ]_{0}^{\pi} = \frac{2}{\pi} ( \frac{\pi^3}{3} - 0 ) = \frac{2\pi^2}{3}$$

因此，直流項（常數項）為：
$$\frac{a_0}{2} = \frac{\pi^2}{3}$$

---

### Step 3: 計算係數 $a_n$
利用偶函數性質簡化公式：
$$a_n = \frac{2}{\pi} \int_{0}^{\pi} x^2 \cos(nx) dx$$

此處我們需要使用**分部積分法 (Integration by parts)**，公式為 $\int u dv = uv - \int v du$。
我們使用表格法（DI Method）快速計算：

| 正負號 | 微分 (D) | 積分 (I) |
| :---: | :---: | :---: |
| + | $x^2$ | $\cos(nx)$ |
| - | $2x$ | $\frac{1}{n} \sin(nx)$ |
| + | $2$ | $-\frac{1}{n^2} \cos(nx)$ |
| - | $0$ | $-\frac{1}{n^3} \sin(nx)$ |

根據表格，積分結果為：
$$\int x^2 \cos(nx) dx = x^2 \cdot \frac{\sin(nx)}{n} - 2x \cdot ( -\frac{\cos(nx)}{n^2} ) + 2 \cdot ( -\frac{\sin(nx)}{n^3} )$$
$$\int x^2 \cos(nx) dx = \frac{x^2 \sin(nx)}{n} + \frac{2x \cos(nx)}{n^2} - \frac{2 \sin(nx)}{n^3}$$

將其代回 $a_n$ 的計算式中，並帶入上下限 $0$ 到 $\pi$：
$$a_n = \frac{2}{\pi} [ \frac{x^2 \sin(nx)}{n} + \frac{2x \cos(nx)}{n^2} - \frac{2 \sin(nx)}{n^3} ]_{0}^{\pi}$$

已知對於任意整數 $n$，$\sin(n\pi) = 0$ 且 $\sin(0) = 0$：
* 當 $x = \pi$ 時，第一項與第三項皆為 0。
* 當 $x = 0$ 時，所有項皆為 0。

因此，式子可以簡化為僅剩 $x = \pi$ 時的第二項：
$$a_n = \frac{2}{\pi} ( \frac{2\pi \cos(n\pi)}{n^2} ) = \frac{4 \cos(n\pi)}{n^2}$$

由於 $\cos(n\pi) = (-1)^n$，我們得到：
$$a_n = \frac{4(-1)^n}{n^2}$$

---

### Step 4: 組合傅立葉級數
將求得的係數 $\frac{a_0}{2} = \frac{\pi^2}{3}$、$a_n = \frac{4(-1)^n}{n^2}$ 以及 $b_n = 0$ 代回原展開式：

$$f(x) = \frac{\pi^2}{3} + \sum_{n=1}^{\infty} \frac{4(-1)^n}{n^2} \cos(nx)$$

也可以將前幾項展開寫成：
$$x^2 = \frac{\pi^2}{3} - 4 \cos(x) + \cos(2x) - \frac{4}{9} \cos(3x) + \dots$$

---

## 最終答案
$$f(x) = \frac{\pi^2}{3} + \sum_{n=1}^{\infty} \frac{4(-1)^n}{n^2} \cos(nx)$$
