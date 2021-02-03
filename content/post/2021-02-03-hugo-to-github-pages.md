---
title: "Hugo + GitHub Pages でブログを作った話"
date: 2021-02-03T09:27:07+09:00
author: "lyohe"
tags: [ hugo, blog ]
---

このブログは Hugo + GitHub Pages で作った。

## Hugo

Hugo は Go 製の静的サイトジェネレータで、 Markdown 等で書いた文章から Web サイトを生成してくれる。
生成した Web サイトの中身はただの静的なファイルなので、 [Netlify](https://www.netlify.com/) や [GitHub Pages](https://pages.github.com/) その他さまざまなサービスで Hosting できる。

Hugo には様々なテーマが用意されていて、見た目を簡単にカスタマイズできる。このブログでは [Tania](https://themes.gohugo.io/hugo-tania/) というテーマを利用している。テーマの適用は非常にかんたんで、 Hugo のプロジェクト内の themes ディレクトリにテーマをダウンロード（多くは GitHub で提供されてるので普通に clone してくればよい）し、設定ファイルで使用するテーマを指定するだけでよい。

Hugo の仕組みや設定ファイルの書き方についてはさくらインターネットさんが公開している記事が分かりやすかったので、これを読んでから[公式ドキュメント](https://gohugo.io/documentation/)を読めば大抵のことは分かると思う。

- [【さくらのナレッジ】静的サイトジェネレータ「Hugo」と技術文書公開向けテーマ「Docsy」でOSSサイトを作る](https://knowledge.sakura.ad.jp/22908/)

ちなみに上記のサイトでは設定ファイルとして config.toml を使っているが、 TOML だけでなく YAML も設定ファイルとして使うことができる。

## GitHub Pages に deploy するまで

GitHub Pages を始めるのは非常に簡単で、ここに書いてある通りにやるだけでよい。

https://pages.github.com/

リポジトリを作ったら `hugo new post/ファイル名` で新しくファイルを作り、 Markdown 等でコンテンツを書く。テーマによって書き方が異なるケースがあるので、テーマごとの Demo サイトと自分のサイトを見比べたり `hugo server` でローカルで動かしてチェックするのがよい。

コンテンツを格納する場所は設定ファイルで変更できる。また、記事のひな形を作りたいときは `archetypes/default.md` を編集すると `hugo new` で生成するファイルの中身を変えることができる。

デプロイするときは `hugo` コマンドで public/ 内に Web サイトを生成できるので、それを GitHub Pages 用に作った `username.github.io` という名前の repository に push すればよい（username のところには GitHub のユーザー名を入れる）。

GitHub アカウントに二要素認証を設定している方は push するときにユーザー名とパスワードで認証できない場合があるので、 [personal access token](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token) を作って password の代わりにそれを入力する。

Hugo の公式ドキュメントにはデプロイ用のスクリプトの例もある。

https://gohugo.io/hosting-and-deployment/hosting-on-github/
