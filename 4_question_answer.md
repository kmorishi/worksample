前提となる受講者レベル  
・大学数学の基礎(教養科目レベル)を理解している  
・統計学の基礎(教養科目レベル)を理解している

[![https://gyazo.com/f2be3507fd3218aa864562bae162fc4d](https://i.gyazo.com/f2be3507fd3218aa864562bae162fc4d.png)](https://gyazo.com/f2be3507fd3218aa864562bae162fc4d)

> なぜ2乗しているのか

最小二乗法は、各データ
<img src = "https://latex.codecogs.com/png.latex?(x_i,y_i)">
の関係を最も良く近似する関数の式を求める方法です。  
例えば、各データの関係を近似する関数が一次関数で表される場合、
傾き<img src = "https://latex.codecogs.com/png.latex?a">と切片<img src = "https://latex.codecogs.com/png.latex?$b">
を求める必要があります。  
その求め方として、各データ<img src = "https://latex.codecogs.com/png.latex?(x_i,y_i)">と直線との差(この差を残差といいます)  
<img src = "https://latex.codecogs.com/png.latex?$y_i&space;-&space;(ax_i&space;&plus;&space;b)$">  
の総和を最小にする<img src = "https://latex.codecogs.com/png.latex?a,"><img src = "https://latex.codecogs.com/png.latex?b">
を定めることが知られています。
そして、残差の総和を計算すると、  

<img src = "https://latex.codecogs.com/png.latex?n&space;\left&space;|&space;y_i&space;-&space;(ax_i&space;&plus;&space;b)&space;\right&space;|">

となります。  
しかし、この形では、<img src = "https://latex.codecogs.com/png.latex?a,"><img src = "https://latex.codecogs.com/png.latex?b">はいくらでも大きくしてよく、
残差を最小にする<img src = "https://latex.codecogs.com/png.latex?a,"><img src = "https://latex.codecogs.com/png.latex?b">
の値が定まりません。
そこで、残差の総和の2乗を計算してみます。すると(途中式は省きます)、

<img src = "https://latex.codecogs.com/png.latex?n\{&space;b&space;-&space;(&space;\bar{y}&space;-&space;a&space;\bar{x}&space;)&space;\}^2&space;&plus;&space;\left&space;(&space;\sum&space;x_i^2&space;-&space;n&space;\bar{x}^2&space;\right&space;)&space;\left\{&space;a&space;-&space;\frac{&space;\sum&space;x_i&space;y_i&space;-&space;n&space;\bar{x}\bar{y}&space;}{&space;\sum&space;x_i^2&space;-&space;n&space;\bar{x}^2&space;}&space;\right\}^2&space;&plus;&space;\sum&space;y_i^2&space;-&space;n&space;\bar{y}^2&space;-&space;\frac{&space;(\sum&space;x_i&space;y_i&space;-&space;n&space;\bar{x}\bar{y})^2&space;}{&space;\sum&space;x_i^2&space;-&space;n&space;\bar{x}^2&space;}">


となります。ただし、  

<img src = "https://latex.codecogs.com/png.latex?\sum&space;x_i&space;=&space;n&space;\bar{x}$,&space;$\sum&space;y_i&space;=&space;n&space;\bar{y}">

としています。
この式から、

<img src = "https://latex.codecogs.com/png.latex?a&space;=&space;\frac{&space;\sum&space;x_i&space;y_i&space;-&space;n&space;\bar{x}\bar{y}&space;}{&space;\sum&space;x_i^2&space;-&space;n&space;\bar{x}^2&space;}">  

<img src = "https://latex.codecogs.com/png.latex?b&space;=&space;\bar{y}&space;-&space;a&space;\bar{x}">

と定めることで、残差の総和を最小にできます。  
ここで、統計学の知識から、<img src = "https://latex.codecogs.com/png.latex?a">の分母は分散の形になっており、分子は共分散の形になっています。  
分散と共分散はデータの数値が分かれば求めることができるので、
<img src = "https://latex.codecogs.com/png.latex?a,"><img src = "https://latex.codecogs.com/png.latex?b">を定め、
直線の式を求めることができました。  
このように、2乗することで、計算のためのメリットが生まれます。
他にも、残差の正負を考える必要もなくなるので、場合分けをして計算が煩雑になることも防げます。

> なぜ最後に2で割っているのか

前述の方法と別の方法で<img src = "https://latex.codecogs.com/png.latex?a,"><img src = "https://latex.codecogs.com/png.latex?b">を求めてみましょう。  
残差の総和の2乗を<img src = "https://latex.codecogs.com/png.latex?d">とおくと、  
<img src = "https://latex.codecogs.com/gif.latex?d&space;=&space;\sum\{y_i&space;-&space;(ax_i&space;&plus;&space;b)\}^2">
です。  
ここで、<img src = "https://latex.codecogs.com/png.latex?d">は<img src = "https://latex.codecogs.com/png.latex?a,"><img src = "https://latex.codecogs.com/png.latex?b">
による変数であるため、<img src = "https://latex.codecogs.com/png.latex?a,"><img src = "https://latex.codecogs.com/png.latex?b">は
偏微分で求めることもできます。  
具体的には、<img src = "https://latex.codecogs.com/png.latex?\frac{\partial d}{\partial a},"><img src = "https://latex.codecogs.com/png.latex?\frac{\partial d}{\partial b}">
を求め、<img src = "https://latex.codecogs.com/png.latex?=0">とおくことで、前述の<img src = "https://latex.codecogs.com/png.latex?a,"><img src = "https://latex.codecogs.com/png.latex?b">
と同じ値を導くことができます。  
しかし、実際に偏微分を行うと分かるのですが、偏微分を行うと、指数である右肩の2は式全体に掛けられ、<img src = "https://latex.codecogs.com/png.latex?=0">とおいた際に打ち消されます。それまで式全体を2で括っておくのは面倒です。  
そこで、始めから  
<img src = "https://latex.codecogs.com/gif.latex?d&space;=&space;\frac{1}{2}\sum\{y_i&space;-&space;(ax_i&space;&plus;&space;b)\}^2">  
とすることで、偏微分した際に全体2を掛ける動作を省くことができます。
なお、2で割ったとしても、最終的に求められる<img src = "https://latex.codecogs.com/png.latex?a,"><img src = "https://latex.codecogs.com/png.latex?b">
の値は同じです。  
このように、2で割るという行為は、偏微分の計算を楽にするためのちょっとしたテクニックです。
2乗したものの変化量を求めるときには非常によく使われるので、ぜひ覚えておいて役立ててください。
