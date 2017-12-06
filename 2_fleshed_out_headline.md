前提となる受講者レベル  
・大学数学の基礎を学習している
・pythonでアルゴリズム、データ構造を学んだ程度

# このテキストのゴール
このテキストで学習した後の受講者の状態です。
1. 誤差逆伝搬法の概要を理解する
2. 誤差逆伝搬法の理解に必要な数学的理論を知り、簡単な計算問題を解くことができる
3. 誤差逆伝搬法の利用例を知る

# 誤差逆伝搬法とは
誤差逆伝搬法がどのような計算であるかを説明します。

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

## 連鎖率
誤差逆伝搬法で使われる理論である、連鎖率の説明をします。  
<img src = "https://latex.codecogs.com/gif.latex?z">が<img src = "https://latex.codecogs.com/gif.latex?u">の関数で、<img src = "https://latex.codecogs.com/gif.latex?u">が<img src = "https://latex.codecogs.com/gif.latex?(x,y)">の関数であるとき、<img src = "https://latex.codecogs.com/gif.latex?z">を<img src = "https://latex.codecogs.com/gif.latex?x">で、<img src = "https://latex.codecogs.com/gif.latex?z">を<img src = "https://latex.codecogs.com/gif.latex?y">でそれぞれ偏微分すると、  
<img src = "https://latex.codecogs.com/gif.latex?\frac{\partial&space;z}{\partial&space;x}$&space;=&space;$\frac{\partial&space;z}{\partial&space;u}&space;\frac{\partial&space;u}{\partial&space;x}">  
<img src = "https://latex.codecogs.com/gif.latex?\frac{\partial&space;z}{\partial&space;y}$&space;=&space;$\frac{\partial&space;z}{\partial&space;u}&space;\frac{\partial&space;u}{\partial&space;y}">  
となります。

### 連鎖率理解のための演習問題
連鎖率の演習問題に取り組みます。  
例題  
次の関数の
<img src = "https://latex.codecogs.com/gif.latex?\frac{dy}{dx}">
を求めよ。

<img src = "https://latex.codecogs.com/gif.latex?x = r(\theta - \sin \theta)">  


<img src = "https://latex.codecogs.com/gif.latex?y = r(1 - \cos \theta)">  


ただし、<img src = "https://latex.codecogs.com/gif.latex?r > 0">


## 最急降下法
誤差逆伝搬法で使われる、最急降下法の理論を説明します。  
最急降下法は、山下り法(山登り法)とも呼ばれます。  
もしも山の中で迷ってしまったとき、どうするでしょうか。
ドローンを使って勾配が最も急な方向へ下り、doro-nnwo



### 最急降下法理解のための演習問題
最急降下法の演習問題に取り組みます。

# 誤差逆伝搬法利用例
誤差逆伝搬法の利用例を紹介します。  
誤差逆伝搬法は、ニューラルネットワークの学習で使われることが多いです。

## ニューラルネットワーク
ニューラルネットワークの説明と、誤差逆伝搬法がどのように使われているかの紹介をします。
ニューラルネットワークは、人間の脳を表現した数学モデルです。  
ニューラルネットワークが学習をするためには、人間が学習のデータを与える必要があります。例えば、リンゴの画像とミカンの画像を見比べ、どちらがリンゴかを判断する場合を考えましょう。

修正に使われるのが誤差逆伝搬法です。

誤差が少なくなるように、データの傾きを減らしていきます。
ここで、最急降下法が使われます。
