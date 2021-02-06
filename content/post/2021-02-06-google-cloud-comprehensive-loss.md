---
title: "Google クラウド巨大赤字の話"
date: 2021-02-06T11:56:34+09:00
author: "lyohe"
tags: [ GCP ]
---

Google の Cloud セグメントが約5,880億円の巨額損失を出したというニュースを見かけた。

[TechCrunch] Google Cloudは2020年に約5880億円の損失
https://jp.techcrunch.com/2021/02/03/2021-02-02-google-cloud-lost-5-6b-in-2020/

Form 10-K は[こちら](https://www.sec.gov/Archives/edgar/data/1652044/000165204421000010/goog-20201231.htm)。

これについて様々な意見を見かけたが、自分の印象と異なる意見が多かったので自分の意見を書いておきたい。

以下、 $ 1B = $ 1 Billion（10億ドル）とする。

## GCP は大丈夫か？

このニュースを見て GCP 大丈夫かな？続くのかな？というのが気になる人がいると思う。むしろ何千億円の赤字なんて大丈夫かと思うのが普通だろう。

しかしながら、Cloud で何千億円の赤字を出したところで Google がどうにかなるわけではない。Alphabet, Inc は純資産が $222B あって2020年12月期の包括利益は$ 40B 以上あるし、 Cloud セグメントは高い成長率のクラウド業界で全体の平均より大幅に高い成長率（YoY +47%）を出している。

Cloud の売上は下記の通り増加し、2年間で2倍以上に成長している。

- 2018 -> 2019: $5.8B -> $8.9B（YoY+53%）
- 2019 -> 2020: $8.9B -> $13.0B（YoY+47%）

![google_revenue_details](/post/2021-02-06/google_revenue_details.png)

なお、今週行われた Conference call では CEO によって Revenue backlog が Q3 -> Q4 で $19B -> $30B [^1]に増加し、増加要因のほぼ全てが Cloud セグメントであると述べられている。 backlog は未認識の収益で、つまり先の期でそれくらい収益を得られる契約があるということになる。これは GCP がプラットフォームとして多くの企業から信頼されていることを表しているし、今後の成長も期待できる。

[^1]: 正確に言うと $29.8B で、1年以内に終了する契約、キャンセル可能な契約、履行済みの未請求を含まない金額。これらは今後2年間で約半分を収益認識し、残りはそれ以降になる。詳しくは Form 10-K p66 Deferred Revenues and Remaining Performance Obligations 参照。

上記のように数字だけ見ると撤退する理由が無いし、むしろ撤退するなんて言い出したら株主は経営陣をクビにすべきだろう。既存のビジネスより成長可能性が高い投資機会があって資金も人材もあるなら、それに投資するのは経営者として当然の選択だと思う。

しかし Google のことなので、やはり突然撤退するかもしれない笑

## Google Workspace の影響

ちなみに冒頭の記事にもある通りこの Cloud 事業には Google Workspace（旧 G Suite）と Google Cloud Platform の売上が両方含まれている。YoY+47% という成長率にもこれが含まれている。Workspace がそんな急成長しているとは思えない [^2] ので、 GCP の成長率はこれより高いことになる。

[^2]: paying businesses が毎年 +1 million 増えていて、現状 6 ~ 7 million なので（既存顧客からの収益増があったとしても）成長率は高くて 30% くらいではないか

Workspace の paying business の数は[2020年3月に6 millionを超えた](https://www.cnbc.com/2020/04/07/google-g-suite-passes-6-million-customers.html)らしい。それぞれの business に何人のユーザーがいるかは開示されていない（されてたらすみません）。

Microsoft の Office 365 が 250 ~ 300 million くらいで、ガートナーの調査によると Google のシェアは MS の 1/8 程度[らしい](https://www.cnbc.com/2020/10/06/google-g-suite-becomes-workspace-gets-new-pricing-tiers.html)ので雑に計算すると 30 million くらいか？これが単価 $100/year とすると Workspace だけで $3B/year の 売上がある計算になる。本当にこんな売上あるのか？書いてて自信がなくなってきた。

上記の内容は推測が多すぎるが、 Workspace が混じってるので純粋な GCP の売上だけが計上されているわけではないということが言いたかった。

## Microsoft Azure

ちなみに Microsoft は ’Server Products and cloud services’ セグメントとして Azure, SQL Server, Windows Server, Visual Studio, System Center, そして GitHub の売上をまとめて開示している。

Microsoft は Azure 単体での収益を開示していないが、成長率は開示している。2021年6月期Q2 の [Form 10-Q](https://microsoft.gcs-web.com/node/28966/html) では Azure 単体の前年同期比成長率が YoY+50% で、 Azure の属する Server Products セグメントは YoY+26% だった。

## Amazon Web Services

Amazon は 'AWS' セグメントとして AWS の損益を開示している。

[Form 10-K の Segment Information](https://d18rn0p25nwr6d.cloudfront.net/CIK-0001018724/5a60b19f-08ef-4231-ad6a-f4810eb38769.html#) を見ると良さそうだ。2020年12月期の売上は $45.3B で利益は $13.5B、成長率は YoY+29% だった。

## Amazon, Google のクラウド事業の収益規模

業界最大手の AWS と Google Cloud の売上と利益（損失）を比較してみる。2020年の成長率は Google が上回っているものの、規模では圧倒的な差がついているように見える。

![google_vs_amazon](/post/2021-02-06/google_vs_amazon.png)

実は Amazon が AWS セグメントの開示を始めたのは2015年12月期から（直近3年開示するので実質的には2013年から）だが、このとき既にこのセグメントでは利益を出している。

![aws_figures](/post/2021-02-06/aws_figures.png)

![aws_revenue_and_profit](/post/2021-02-06/aws_revenue_and_profit.png)

2013 -> 2020年の7年間でなんと収益が15倍（！）になっている。なお、Google のクラウド事業を単純に収益だけで見ると2016年の AWS くらいの規模になる。

ちなみに AWS も GCP と同じくらいの規模のときは同程度の成長率を記録しているが、規模の拡大に従って成長率が落ち着いてきた。どの事業者にも言えることだけど、クラウドの新たなユースケースを掘り出したり既存顧客の成長に貢献するというところが重要になってくると思う。実際、 Google の Conference call ではその辺が強調されているように（自分には）聞こえた。

## 個人的な意見

単にサーバーをデータセンターに置いてそれを貸す、というビジネスであれば価格や品質などの競争力は規模に比例すると考えられる。しかし、一口にクラウドといっても AWS や Azure や GCP はより抽象化の進んだマネージドサービスとして製品を提供しているわけで、ビジネスの付加価値を規模の経済だけでは測れない。

コンピュータ資源を抽象化したマネージドサービスたち[^3]を組み合わせてサービスを提供するというのが当たり前になっていくと、それはただサーバーを借りるより高い付加価値がある。クラウドの市場規模というのは本当に巨大だと思う。

[^3]: もしくはサーバーレス（サーバーはある）のコンテナ実行環境とか関数とか？

結局は顧客のユースケースによって何を選ぶか（または複数のクラウドを使い分けるか）という話になってくる。例えば Cloud Spanner や BigQuery と同じものが AWS にあるかって言われると、似ているのはある（Aurora とか Redshift とか）けど同じものはない。ネットワーク効果の強い winner takes all 的なビジネスだと話が全く違ってくると思うけど、実際には AWS も Azure も GCP も成長を続けている。市場はもっと大きくなる可能性が高い。

そういう意味では収益の成長率が市場平均を大幅に上回ってるし今後の成長可能性もあるよ、というのは普通に良いニュースなんじゃないかと思いました。