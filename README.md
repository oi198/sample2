### ソニーの株価変動を予測してみた！

[google colabで開く](https://colab.research.google.com/drive/1PkRAXsBzbp4z9OTw9KnpAli7WlG19N_O?usp=sharing)

今回はRNNでおなじみのLSTMを使って明日のソニーの終値を予測するモデルを作ってみました
実装環境はgoogle colabを使いました

#### 株価データを取得する

`import pandas_datareader as web`<br>
`com = 6758 #ソニー銘柄コード`<br>
`web.DataReader([str(com) + '.JP'], 'stooq')`<br>

上記のコードで銘柄コードに対する企業の過去5年間の終値、高値、安値、始値、出来高を取得できます

<img src="https://uploda1.ysklog.net/49edcf2db85d8fff471c2851a80ff6cb.png" width="300px">

ソニーの終値グラフを描画

<img src="https://uploda3.ysklog.net/37da57f1445fd0111fa92fd610c8953d.png" width="300px">

株価データの内、直近228日分の終値をテスト用データ、それ以前の912日分の終値を訓練用データにしました

#### LSTMモデルを作成・学習させる

以下のようなモデルを作成

<img src="https://uploda3.ysklog.net/5de30f0fdd11acf5e317680dc9497aff.png" width="300px">

最適化アルゴリズムにはAdam、<br>

モデル評価のための損失関数は平均二乗誤差(MSE)を設定しました

#### 予測結果と実際の値を比較

<img src="https://uploda3.ysklog.net/46277b378094c5078e09816c12159464.png" width="300px">

#### 結論

