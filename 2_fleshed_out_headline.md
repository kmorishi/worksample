前提となる受講者レベル  
・大学数学の基礎(教養科目レベル)を理解している  
・pythonでアルゴリズム、データ構造を学び、コードを打つことができる

# このテキストのゴール
このテキストで学習した後の受講者の状態です。
1. 誤差逆伝搬法の概要を理解する
2. 誤差逆伝搬法の理解に必要な数学的理論を知り、簡単な計算問題を解くことができる
3. 誤差逆伝搬法の利用例を知る

# 誤差逆伝搬法とは
誤差逆伝搬法がどのような計算であるかを説明します。
誤差逆伝搬法は、人間の脳をコンピュータに適用したモデルであるニューラルネットワークの計算に使われる手法です。  
現在、ニューラルネットワークは既にオープンソースとして出回り、誰でも使用可能になっています。しかし、AIの学習に携わる者として、その背景に使われている理論を理解しておく必要はあるでしょう。

# 誤差逆伝搬法を支える理論
誤差逆伝搬法に使われている数学的理論について説明します。

## 偏微分
1変数関数
<img src = "https://latex.codecogs.com/gif.latex?y&space;=&space;f(x)">
を微分するとき、  
<img src = "https://latex.codecogs.com/gif.latex?\frac{dy}{dx}">  
と書きました。偏微分は、2変数以上の関数を微分するときに使われます。
2変数関数
<img src = "https://latex.codecogs.com/gif.latex?z&space;=&space;f(x,&space;y)">  
を微分するとき、  
・<img src = "https://latex.codecogs.com/gif.latex?y">を定数と考え、<img src = "https://latex.codecogs.com/gif.latex?x">で微分する  
・<img src = "https://latex.codecogs.com/gif.latex?x">を定数と考え、<img src = "https://latex.codecogs.com/gif.latex?y">で微分する  
の2つの方法があります。  
1つ目を  
<img src = "https://latex.codecogs.com/gif.latex?\frac{\partial&space;z}{\partial&space;x}">  
と記述し、2つ目を  
<img src = "https://latex.codecogs.com/gif.latex?\frac{\partial&space;z}{\partial&space;y}">  
と記述します。  

変数が増えると式が複雑に見えてしまいがちですが、
「微分する変数以外はすべて定数」と考えれば楽になります。

## 連鎖率
誤差逆伝搬法で使われる理論である、連鎖率の説明をします。  
<img src = "https://latex.codecogs.com/gif.latex?z">が<img src = "https://latex.codecogs.com/gif.latex?u">の関数で、<img src = "https://latex.codecogs.com/gif.latex?u">が<img src = "https://latex.codecogs.com/gif.latex?(x,y)">の関数であるとき、<img src = "https://latex.codecogs.com/gif.latex?z">を<img src = "https://latex.codecogs.com/gif.latex?x">で、<img src = "https://latex.codecogs.com/gif.latex?z">を<img src = "https://latex.codecogs.com/gif.latex?y">でそれぞれ偏微分すると、  
<img src = "https://latex.codecogs.com/gif.latex?\frac{\partial&space;z}{\partial&space;x}$&space;=&space;$\frac{\partial&space;z}{\partial&space;u}&space;\frac{\partial&space;u}{\partial&space;x}">  
<img src = "https://latex.codecogs.com/gif.latex?\frac{\partial&space;z}{\partial&space;y}$&space;=&space;$\frac{\partial&space;z}{\partial&space;u}&space;\frac{\partial&space;u}{\partial&space;y}">  
となります。  

偏微分も分数のように扱うことができるということです。

### 連鎖率理解のための演習問題
連鎖率の演習問題に取り組みます。  

例題  
次の関数の
<img src = "https://latex.codecogs.com/gif.latex?\frac{dy}{dx}">
を求めよ。  

<img src = "https://latex.codecogs.com/gif.latex?x&space;=&space;r(\theta&space;-&space;\sin&space;\theta)">  

<img src = "https://latex.codecogs.com/gif.latex?y&space;=&space;r(1&space;-&space;\cos&space;\theta)">  


ただし、<img src = "https://latex.codecogs.com/gif.latex?r > 0">  

※この曲線は、サイクロイドと呼ばれる有名な曲線です。  
[![https://gyazo.com/fd6d7bc524f2d1d0a7846cd31e4ce972](https://i.gyazo.com/fd6d7bc524f2d1d0a7846cd31e4ce972.png)](https://gyazo.com/fd6d7bc524f2d1d0a7846cd31e4ce972)

## 最急降下法
誤差逆伝搬法で使われる、最急降下法の理論を説明します。  

最急降下法は、山下り法(山登り法)とも呼ばれます。  
もしも山の中で迷ってしまったとき、どうするでしょうか。
空を飛ぶ道具を使って麓の方向が分かればよいのですが、ドローンなどはまだ所有していない人も多いです。  

1つの方法として、勾配が急な方向に向かって下りていけば、いつかは麓にたどり着けることが考えられます。  
このように、「勾配が最も急な方向に向かって下りる」操作を最急降下法といいます。  
最急降下法はグラフの極小値を求めるために使用されます。  

下の図は、
<img src = "https://latex.codecogs.com/gif.latex?y&space;=&space;(x-2)^2">
のグラフです。  
[![https://gyazo.com/dd856ac8cbe37c3e0d40183728cc34f9](https://i.gyazo.com/dd856ac8cbe37c3e0d40183728cc34f9.png)](https://gyazo.com/dd856ac8cbe37c3e0d40183728cc34f9)

最急降下法で極小値を求める場合の手順は、以下の通りです。
1. スタート地点<img src = "https://latex.codecogs.com/gif.latex?(x_k,y_k)">を定める  
2. 関数の微分を求め、定数<img src = "https://latex.codecogs.com/gif.latex?\alpha">(後述)の値を定める  
3. <img src = "https://latex.codecogs.com/gif.latex?x^{k&plus;1}&space;=&space;x^k&space;-&space;\alpha&space;\frac{dy}{dx^k}">に従って、<img src = "https://latex.codecogs.com/gif.latex?x^{k+1}">を定める  
4. <img src = "https://latex.codecogs.com/gif.latex?x^{k+1}">が最小値でない場合、3に戻る  

ここで、<img src = "https://latex.codecogs.com/gif.latex?\alpha">は斜面を下る歩幅を表しています。<img src = "https://latex.codecogs.com/gif.latex?\alpha">が大きいと、大きく斜面を下ります。  

最急降下法は関数の1階微分が求められれば計算が可能であり、計算にかかるコストが低いです。しかし、とりあえず低い方向を目指す手法のため、スタート地点の定め方によっては最小値の探索にかなりの回数がかかってしまうことがあります。

### 最急降下法理解のための演習問題
最急降下法の演習問題に取り組みます。  

例題  
次の関数の最小値を求めよ。ただし、<img src = "https://latex.codecogs.com/gif.latex?\alpha=1">とする。  
<img src = "https://latex.codecogs.com/gif.latex?y&space;=&space;\left&space;(\frac{2}{3}x&space;-&space;2&space;\right)^2">

# 誤差逆伝搬法利用例

## ニューラルネットワーク
ニューラルネットワークの説明と、誤差逆伝搬法がどのように
使われているかの紹介をします。  

ニューラルネットワークは、人間の脳をコンピュータに適用した数学モデルです。  
人間がデータを繰り返し与えることで、コンピュータはパターンを把握し、学習していきます。  
例えば、コンピュータにいくつかのリンゴの画像を見せ、2番目に見せた画像はどれか選ばせるゲームを考えましょう。
[![https://gyazo.com/4feda8689a21dcc4585d53a89bb0ad22](https://i.gyazo.com/4feda8689a21dcc4585d53a89bb0ad22.png)](https://gyazo.com/4feda8689a21dcc4585d53a89bb0ad22)

コンピュータはいきなりリンゴの画像を見分けられることはできません。コンピュータが認識した画像が現実の画像に近づくように、人間の手でデータを与え、コンピュータの認識を修正してあげる必要があります。
その修正に使われるのが誤差逆伝搬法なのです。

ここで、ニューラルネットワークの簡単なモデルを考えてみます。
[![https://gyazo.com/c9f3383abca0c9d0ae88aa1d6e0bcb90](https://i.gyazo.com/c9f3383abca0c9d0ae88aa1d6e0bcb90.png)](https://gyazo.com/c9f3383abca0c9d0ae88aa1d6e0bcb90)

実は、人間が与えたリンゴの画像はコンピュータ上ではそのまま認識されず、重みが掛けられ、バイアスが足された状態で出力されます。

つまり、  
<img src = "https://latex.codecogs.com/gif.latex?y&space;=&space;f(wx&space;&plus;&space;b)">  
と表されます。このことから、実際に求めたい画像データを<img src = "https://latex.codecogs.com/gif.latex?t,">コンピュータの出力画像を<img src = "https://latex.codecogs.com/gif.latex?y">とし、両者の差を限りなく小さくすることで、出力画像を実際の画像に近づけることができそうです。  

ここで、数学的テクニックを利用します。<img src = "https://latex.codecogs.com/gif.latex?t,"><img src = "https://latex.codecogs.com/gif.latex?y">の大小は不明であるため、正負の影響を失くすために、  
<img src = "https://latex.codecogs.com/gif.latex?(y&space;-&space;t)^{2}">  
の差を小さくすることを考えます。また、<img src = "https://latex.codecogs.com/gif.latex?y">は<img src = "https://latex.codecogs.com/gif.latex?w,"><img src = "https://latex.codecogs.com/gif.latex?b">に依って変化するため、微分をして変化量を調べる必要がありそうです。微分による計算を楽にするために、求める差を<img src = "https://latex.codecogs.com/gif.latex?E">とすると、<img src = "https://latex.codecogs.com/gif.latex?E">は、  
<img src = "https://latex.codecogs.com/gif.latex?E&space;=&space;\frac{1}{2}(y&space;-&space;t)^{2}">  
となります。

この<img src = "https://latex.codecogs.com/gif.latex?E">を小さくするために使われるのが最急降下法です。
具体的には、<img src = "https://latex.codecogs.com/gif.latex?w,"><img src = "https://latex.codecogs.com/gif.latex?b">を最小にすれば<img src = "https://latex.codecogs.com/gif.latex?E">は最小になるので、<img src = "https://latex.codecogs.com/gif.latex?w,"><img src = "https://latex.codecogs.com/gif.latex?b">に対して最急降下法の式を立てます。すると、<img src = "https://latex.codecogs.com/gif.latex?w">は  
<img src = "https://latex.codecogs.com/gif.latex?w^k&space;-&space;\epsilon&space;\frac{\partial E}{\partial w^k}">  
で最小化され、<img src = "https://latex.codecogs.com/gif.latex?b">も同様に、  
<img src = "https://latex.codecogs.com/gif.latex?b^k&space;-&space;\epsilon&space;\frac{\partial E}{\partial b^k}">  
で最小化されます(<img src = "https://latex.codecogs.com/gif.latex?\epsilon">は前述の<img src = "https://latex.codecogs.com/gif.latex?\alpha">に当たる定数で、学習率と呼ばれます)。
このような計算で、入力と出力の誤差を失くしています。
