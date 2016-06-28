# Logistic Regression

binary classification: $$\text{ideal }f(x) = sign(P(+1|x) - \frac{1}{2}) \in \{-1, +1\}$$

'soft' binary classification: $$f(x) = P(+1|x) \in [0, 1]$$

與一般的 binary classification 的問題不同, 今天想知道的是這 binary 結果發生的機率各是多少? 但依據我們手上有的資料其實跟以往在解 binary classification 並無不同, 所以我們並不知曉這未知的機率, 我們僅有的是對某次 sample 到的 **x** 去計算出來的 y 各是多少, 所以從想像上這 N 次 Sample 的結果 y 其實是隱含著雜訊的資料 (預期是落在 0~1 的 $$\mathbb{R}$$, 但實際觀察到的僅是確切的結果 是否為 +1)。

## Step 1
先用與 Linear Regression 相同的方法, 用特徵值去計算取出一個分數
$$
\color{purple}{s}=\sum_{i=\color{red}{0}}^d\color{orange}{w_i}{x_i}=w^Tx
$$
## Step 2
然後要如何將這個分數轉換成 $$\in [0, 1]$$, 我們就想像分數愈高機率就愈大吧! 所以這邊製造了一個函數 logistic function $$\theta(s)$$ 將 $$[-\infty,+\infty]$$ 轉換到 [0, 1]
$$
\color{blue}{\theta}(\color{purple}{s})=\frac{e^\color{purple}{s}}{1+e^\color{purple}{s}}=\frac{1}{1+e^\color{purple}{-s}}
$$
![](sigmoid_function.png)

這個函數有底下幾個關鍵值
* s = 0, $$\theta(0) = \frac{1}{2}$$