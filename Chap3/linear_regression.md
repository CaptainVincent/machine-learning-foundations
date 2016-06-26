# Linear Regression

Linear Regression 討論的問題在於 output 是屬於 $$\mathbb{R}$$ 實數空間

Linear Regression 的 Hypothesis (這僅是其中一種 H 的設計方式)

$$h(x)=\sum_{i={0}}^d w_ix_i= w^Tx$$

問題可以想像成是在求出一條/高維平面, 當 **x** 代入時可以與 $$y_n$$ 愈接近。 (紅色標出的距離稱作 residuals 餘數)
![](illustrationLR.jpg)
這邊 Error Measure 是使用這個問題傳統常用的 **Squared**
$$
\begin{matrix}
err(\hat{y}_n,y_n) = (\hat{y}_n-y_n)^2
\end{matrix}
$$
我們可以得到 in-sample
$$
E_{in}(w)=\frac{1}{N}\sum_{n=1}^N(\hat{y}_n - y_n)^2=\frac{1}{N}\sum_{n=1}^N(w^Tx_n-y_n)^2
$$
How to minize $$E_{in}$$?
$$
\begin{aligned}
E_{in}(\color{blue}{w}) &= \frac{1}{N}\sum_{n=1}^{N}(\color{blue}{w^T}\color{red}{x_n}-\color{purple}{y_n})^2=\frac{1}{N}\sum_{n=1}^{N}(\color{red}{x_n^T}\color{blue}{w}-\color{purple}{y_n})^2 (矩陣乘法的交換)\\\

&=\frac{1}{N}\begin{Vmatrix}
\color{red}{x_1^T}\color{blue}{w}-\color{purple}{y_1}\\\
\color{red}{x_2^T}\color{blue}{w}-\color{purple}{y_2}\\\
...\\\
\color{red}{x_N^T}\color{blue}{w}-\color{purple}{y_N}
\end{Vmatrix}^2 (將 Sumation 換成向量長度的相乘)\\\

&=\frac{1}{N}\begin{Vmatrix}
\color{red}{\begin{bmatrix}
--x_1^T--\\\
--x_2^T--\\\
...\\\
--x_N^T--
\end{bmatrix}}
\color{blue}{w} -
\color{purple}{\begin{bmatrix}
y_1\\\
y_2\\\
...\\\
y_3
\end{bmatrix}}
\end{Vmatrix}^2 \\\

&=\frac{1}{N}||
\underbrace{\color{red}{X}}_{N\times d+1}\;\;\;
\underbrace{\color{blue}{w}}_{d+1\times 1} \; - \;
\underbrace{\color{purple}{y}}_{N\times 1}
||^2
\end{aligned}
$$

目標找到一個 w 使得 $$E_{in}(w)$$ 可以是 minimum, 此函數可以推導 (課程中未證) 是連續(continuous)、可微(differentiable)、開口向上的凸函數(convex), 而這個函數的最低點
$$
E_{in}(\color{blue}{w}) \equiv
\begin{bmatrix}
\frac{\partial E_{in}}{\partial \color{blue}{w}_0}(\color{blue}{w})\\\
\frac{\partial E_{in}}{\partial \color{blue}{w}_1}(\color{blue}{w})\\\
...\\\
\frac{\partial E_{in}}{\partial \color{blue}{w}_d}(\color{blue}{w})
\end{bmatrix}=\begin{bmatrix}
\color{orange}{0}\\\
\color{orange}{0}\\\
...\\\
\color{orange}{0}
\end{bmatrix}
$$