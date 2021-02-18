---
title: "Fusuma でスライドを作るスライドを Fusuma で作る"
date: 2021-02-13T17:33:47+09:00
author: "lyohe"
tags: [ Fusuma ]
---

[Fusuma](https://hiroppy.github.io/fusuma/) は Markdown でスライドを作る OSS で、最近大きなアップデートが行われた。

- [Markdownでスライドを作るツールのFusumaのv2をリリースをしました](https://blog.hiroppy.me/entry/fusuma-v2)

上記の記事で Fusuma の存在を知り、自分でも試しに使ってみた。

思ったより楽に良さげなスライドができたのでスライドを作る際の選択肢の一つとしてお勧めしたい。しかしながら、自分が作ったスライドが公開できないやつなので、別に Fusuma を使ってスライドを作る方法を説明するスライドを作りそれをブログに書くことにした。

なお、本記事の Fusuma に関する情報のほぼ全ては [README](https://github.com/hiroppy/fusuma/blob/master/README.md) と[公式サイトの intro](https://hiroppy.github.io/fusuma/intro/) 、[site/docs/guides](https://github.com/hiroppy/fusuma/tree/master/site/docs/guides) を読めば書いてあることしか書いていない。そちらの方が正確かつ詳しいので、使ってみようかと思った方はそちらを読んだ方が有益そうだ。

この記事には主に自分の動機や印象に残ったことを書いた。

（Fusuma は Slide door だから Fusuma っていう名前なのかな...）

## 自分の動機

何故スライドを Markdown で作るのか？

多くの人はスライドを作るとき Microsoft PowerPoint / Keynote / Google Slides を使うと思う。これらの製品は GUI で多彩な操作ができ、直感的でとても便利だ。人によって好みは分かれるだろうが、私は Google Slides が大好きでよく使っていた。

### 既製のスライド作成ソフトへのちょっとした不満

Google スライドの機能に関しては大きな不満はないのだが、起動してスライドの体裁を整えて...みたいなのがちょっと面倒だなーと感じていた。

そこで Markdown でやれば手軽にスライド作れるのでは！？と思ったのが Fusuma に手を出した理由だ。また、テキストなので Git 等の VCS でバージョン管理しやすいというメリットもある。

## スライドを作るスライド

完成品はこちら ↓ で、ここの GitHub Pages にディレクトリ分けてデプロイした。 

https://lyohe.github.io/slide/fusuma-example

iframe で埋め込むこともできる（自分側の都合でサイズの調整がちょっと難しかった）。

<iframe src="https://lyohe.github.io/slide/fusuma-example" style="width:100%; height:45rem;"></iframe>

### 最低限のスライドを動かすまで

1. とりあえずスライド用のディレクトリを作って `npm init` しておく
1. `npm install fusuma -D` で Fusuma をインストールする
1. `npx fusuma init` で今いるディレクトリにスライドのひな形を作る
1. `npx fusuma start` で development server を起動する

これだけでスライドのひな形ができ、ブラウザから `localhost:8080` で確認できる。サーバーを起動しっぱなしにしてファイルを編集することで変更が自動的に反映される。

この初期状態のスライドは [demo](https://hiroppy.github.io/fusuma/themes/) で触ることができる。動かしてみると使用感が分かると思う。あとは自分のスライドか、できれば[公式サイトの intro](https://hiroppy.github.io/fusuma/intro/) を見てほしい。

あとは自分で作ってみましょう！

## スライドを作成する際の注意点

ここからは自分がスライド作る中で印象に残ったことを書いていく。

### PDF 出力前に build すべし

Fusuma には `npx fusuma pdf` で PDF を出力する機能があるが、これは build した HTML を基に生成するので先に build しないと PDF export に失敗する。

build や pdf export は[コマンドラインオプションでいろいろできる](https://github.com/hiroppy/fusuma/blob/master/packages/fusuma/src/cli/index.js)が特に理由なければデフォルトを使うのがいいと思う。

### シンタックスハイライト

スライド上でプログラムをシンタックスハイライトするために [Prism.js](https://www.npmjs.com/package/prismjs) を使っている。

そのため、 Prism で対応していない言語はハイライトできない。自分はそういう言語使ったことないが...ちなみに [Zenn も Prism.js を使っている](https://zenn.dev/zenn/articles/markdown-guide#%E3%82%B3%E3%83%BC%E3%83%89%E3%83%96%E3%83%AD%E3%83%83%E3%82%AF)ので、 Zenn でハイライトできる言語はだいたいハイライトできると考えてよさそう。

### デプロイ

Deploy には [gh-pages](https://www.npmjs.com/package/gh-pages) を使っている。

`npx fusuma deploy` を実行すると git の remote origin に `gh-pages` ブランチを作り、そこにスライドを build した結果（`dist/`）を push する。

自分は Fusuma が提供する deploy コマンドを使わず、 `dist/` 以下を直接に自分の GitHub Pages 用リポジトリにぶち込んだ。

### Presentation モード

Presentation モードに入るとスピーカーノート、現在のスライド、次のスライドが見えるのだが、 Fusuma が提供する機能はこれだけではない。

録音してくれたりページごとの時間を記録してくれたり、様々な便利機能がある。これ Google スライドにも欲しいんだよなぁ。

https://hiroppy.github.io/fusuma/docs/modes/presenter

### 数式や図形、フローチャートも書ける

[Mermaid.js](https://github.com/mermaid-js/mermaid) を使って図形やチャートを描ける。

https://hiroppy.github.io/fusuma/docs/guides/math-chart

試しにシーケンス図を描いてみた（下図の右半分は VS Code）。

![mermaid-sequence](/post/2021-02-13/mermaid-sequence.png)

他にもフローチャートやガントチャート、 ER 図などいろいろ書ける。記法は [Mermaid.js の README を見ると](https://github.com/mermaid-js/mermaid#examples)いろいろ書いてある。

### npm

これは恥ずかしい話なのだが、 Fusuma 入れた後にそのプロジェクトで npm 使って手動でいろいろ入れたら何もしてないのに壊れて困った（いろいろ npm uninstall して一からやり直したらなおった）。

実際 npm のこと何も分からず使ってる感があるのでちゃんと勉強しようと思う。

## 結論

もし Fusuma を知らない人がいたら、とりあえず [README](https://github.com/hiroppy/fusuma/blob/master/README.md) と[公式サイトの intro](https://hiroppy.github.io/fusuma/intro/) を見てほしい。私は今後さくっとスライド作りたいときはこれを使うことにした。

そして[作者の方](https://github.com/hiroppy)に課金できるボタンが GitHub にあったので $5/month のコースを押した。

あと今回の記事と関係ないが [Promise の本](https://azu.github.io/promises-book/)のおかげで Promise のことが分かるようになってきたので、著者の [azu](https://github.com/azu) さんにも $5/month 課金した。ちなみに私の Slack には azu さんの GitHub アクティビティが流れるチャンネルがある。

自分自身はプログラミング初心者なので何やってるのか全く分からんのだが、やっていこうと思います。
