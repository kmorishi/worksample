![最小二乗法](https://gyazo.com/f2be3507fd3218aa864562bae162fc4d)

> なぜ2乗しているのか

結論から言えば、それが関数の式を求める近道だからです。
試しに、2乗しない形で、

$y_i - (ax_i + b)$
<a href="https://www.codecogs.com/eqnedit.php?latex=$y_i&space;-&space;(ax_i&space;&plus;&space;b)$" target="_blank"><img src="https://latex.codecogs.com/png.latex?$y_i&space;-&space;(ax_i&space;&plus;&space;b)$" title="$y_i - (ax_i + b)$" /></a>

の総和を最小にするa,bを求めます。
すると、


$n| y_i - (ax_i + b) |$


となります。  
しかし、この形では、式を最小にするa,bを求めることは困難です。  
そこで、差の絶対値の総和の2乗を計算してみます。すると(途中式は省きます)、
```math
n{ b - ( \bar{y} - a \bar{x} ) }^2 + ( \sum x_i^2 - n \bar{x}^2 ) { a - \frac{ \sum x_i y_i - n \bar{x}{y} }{ \sum x_i^2 - n \bar{x}^2 } }^2
+ \sum y_i^2 - n \bar{y}^2 - \frac{ (\sum x_i y_i - n \bar{x}{y})^2 }{ \sum x_i^2 - n \bar{x}^2 }
```
となります(計算の途中で\sum x_i = n \bar{x}, \sum y_i = n \bar{y}としました)。
この式から、
```math
b = \bar{y} - a \bar{x}
```
```math
a = \frac{ \sum x_i y_i - n \bar{x}{y} }{ \sum x_i^2 - n \bar{x}^2 }
```
と定めると、総和の2乗は最小になることが分かります。
ここで、統計学の知識から、aの分母は分散の形になっており、分子は共分散の形になっています。
このように、2乗するとa,bを求めることができました。

また、

> なぜ最後に2で割っているのか

についてですが、こちらは式を微分する際に役立ちます。  
総和が()^2の形で表される場合、微分すると()の右肩の2が前に掛けられ、1/2で打ち消されます。
2で割るという行為は、微分計算を楽にするための便利な道具のようなものです。