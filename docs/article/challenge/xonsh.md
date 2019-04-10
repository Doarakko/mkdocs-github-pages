# 話題沸騰中の「Xonsh」というものを触ってみました
## はじめに
この記事は「[Xonsh Advent Calendar 2018]()」の11日目の記事です。

「Xonsh」というものが話題沸騰中とのことなので、時代の波に乗り遅れないように触ってみました。

## 「Xonsh」 とは
Xonsh（エックスオンシュ） とは Python 製のシェルです。



Xonsh の日本人開発者の方が記事をいっぱい書いてくれています。

[https://vaaaaaanquish.hatenablog.com/archive/category/xonsh:embed:cite]



Xonsh のことを調べていると、大抵この方の記事に行き着きます。  
勘弁して欲しいです。

## 実行環境
- macOS 10.13.6
- anaconda3-5.2.0
    - Python 3.6.5
- pip 18.1

## 試してみる
### インストール
```
$ pip install xonsh
```

`pip` で入るのが驚きです。  
シェルと聞くと、インストールとか環境周りとか面倒くさそうなイメージがあるのですが、`pip`を見ると安心しますね 。

### 起動
起動する際には、以下コマンドを打つ必要があります。
不思議な感じです。
```
$ xonsh
```

### びっくり
何も読まずにとりあえずうってみました。
```
$ import pandas as pd
$ df = pd.read_csv('../input/sales_train.csv')
$ df.head()
         date  date_block_num  shop_id  item_id  item_price  item_cnt_day
0  02.01.2013               0       59    22154      999.00           1.0
1  03.01.2013               0       25     2552      899.00           1.0
2  05.01.2013               0       25     2552      899.00          -1.0
3  06.01.2013               0       25     2554     1709.05           1.0
4  15.01.2013               0       25     2555     1099.00           1.0
```
本当に Python でびっくりです。



## 良かったところ
### インストールが簡単
Python を使っている人であれば、秒で入れられます。

<u><b>「Xonsh のインストールでつまずく人、マジで0人説」</b></u>
### 環境への影響
Python のパッケージなので（間違ってたらごめんなさい）、他のところをいじる必要がないのは大きいです。

なにかしでかしたら、`pip uninstall xonsh`で致命傷は受けないという保険があります。

### Python で書ける安心感
普通のシェルだと、自分でなにか作りたいと思ってもハードルが高いです。

Xonsh は Python でなんでも書けます。

Pyhton は最強です。  
つまり、<u><b>「Xonsh」は最強ということです。</b></u>

## 悪かったところ
### 起動が面倒
起動する際には、毎回 `Xonsh` コマンドを打たなければいいけません。  

回避策あったら教えてください。


### pyenv, gcloud が使えない
普段 `gcloud`コマンドを使うために、`pyenv` で Python2 と Python3 を切り替えているのですが、ここら辺は使えないようです。

「Xonsh」自体が Python3 上で動いているので、Python 2 には切り替えられないという感じでしょうか。

他のシェルと違い Pyhton 上で動くとなると、ここらへんのバージョンの問題はでできますね

Xonsh の問題というよりは、`gcloud` が Pyhton 3 に対応すればいいだけの話です。  

## さいごに
ちょっとしたコマンドを作っていたのですが、間に合わなかったので別記事に書こうと思います。

みなさんも時代の波に乗り遅れないように `pip install xonsh` しましょう。

## 参考資料
[Pythonistaに贈るXonshのススメ](https://vaaaaaanquish.hatenablog.com/entry/2017/11/30/175236)