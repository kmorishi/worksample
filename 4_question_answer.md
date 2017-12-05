前提となる受講者レベル  
・高校数学の知識を有し、大学数学の基礎を理解している

[![https://gyazo.com/f2be3507fd3218aa864562bae162fc4d](https://i.gyazo.com/f2be3507fd3218aa864562bae162fc4d.png)](https://gyazo.com/f2be3507fd3218aa864562bae162fc4d)

> なぜ2乗しているのか

最小二乗法は、各データ
$(x_i,y_i)$
の関係を最も良く近似する関数の式を求める方法です。  
なぜ2乗しているのかですが、結論から言えば、それが関数の式を求める近道だからです。
試しに、2乗しない形で、

<img src = "https://latex.codecogs.com/png.latex?$y_i&space;-&space;(ax_i&space;&plus;&space;b)$">

の総和を最小にする$a$,$b$を求めます。
すると、  

<img src = "https://latex.codecogs.com/png.latex?$n&space;|&space;y_i&space;-&space;(ax_i&space;&plus;&space;b)&space;|$">

となります。  
しかし、この形では、式を最小にする$a$,$b$を求めることは困難です。  
そこで、差の絶対値の総和の2乗を計算してみます。すると(途中式は省きます)、

<img src = "https://latex.codecogs.com/png.latex?$n\{&space;b&space;-&space;(&space;\bar{y}&space;-&space;a&space;\bar{x}&space;)&space;\}^2&space;&plus;&space;\left&space;(&space;\sum&space;x_i^2&space;-&space;n&space;\bar{x}^2&space;\right&space;)&space;\left\{&space;a&space;-&space;\frac{&space;\sum&space;x_i&space;y_i&space;-&space;n&space;\bar{x}\bar{y}&space;}{&space;\sum&space;x_i^2&space;-&space;n&space;\bar{x}^2&space;}&space;\right\}^2$&space;$&plus;&space;\sum&space;y_i^2&space;-&space;n&space;\bar{y}^2&space;-&space;\frac{&space;(\sum&space;x_i&space;y_i&space;-&space;n&space;\bar{x}\bar{y})^2&space;}{&space;\sum&space;x_i^2&space;-&space;n&space;\bar{x}^2&space;}$">

となります。ただし、  

$\sum x_i = n \bar{x}$, $\sum y_i = n \bar{y}$

としてます。
この式から、

$a = \frac{ \sum x_i y_i - n \bar{x}\bar{y} }{ \sum x_i^2 - n \bar{x}^2 }$

$b = \bar{y} - a \bar{x}$

と定めると、総和の2乗は最小になることが分かります。
ここで、統計学の知識から、$a$の分母は分散の形になっており、分子は共分散の形になっています。
このように、2乗すると$a$,$b$を求めることができました。

また、

> なぜ最後に2で割っているのか

についてですが、こちらは式を微分する際に役立ちます。  
総和が()^2の形で表される場合、微分すると()の右肩の2が前に掛けられ、$1/2$で打ち消されます。
2で割るという行為は、微分計算を楽にするための便利な道具のようなものです。
