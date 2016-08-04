---
title: ref.vim (+refe2) で ruby のマニュアルを参照する
date: 2015-03-29 21:51 JST
tags: vim,ruby
---

ちまちま ruby を書きだしていい加減環境をととのえないと馬鹿らしいと感じたので vim-endwise とか入れたりしてたんだけど、ref.vim を入れる際にしょうもない詰まり方をしたので覚え書きする。

READMORE

refe2 の導入
------------

まあとりあえず doc とか雑に読んでみた感じ、ref.vim 単体でも動く感じはあったので入れてみた。リファレンスが表示されるものの外部コマンドを実行したような感じになってしまい、doc に載ってるリファレンスビューアが開いている感じがなかったのでググる。

ref.vim に同梱されているソースは refe のものらしく、今設定無しで動いているのは ri だったのでこういう自体になってるっぽかったので、refe を入れることにする。で、調べていくと今は refe2 を入れたほうがいいらしい。

```bash
gem install refe2
rbenv rehash # if use rbenv
```

ここで `refe Array` とかしてもデータベースエラーとか吐くので何事かと思ったんだけど、bitclust コマンドでデータベースを作成しておく必要があるらしい。

```bash
bitclust setup
refe Array
```

うまくいっていれば日本語でリファレンスが表示される。

ref.vim の導入
--------------

と言っても上で書いた通り、先に導入してしまったので特に書くことは無い。みんな大好き neobundle を使いましょうという感じ。

リファレンスの参照も特別な設定は (試した ubuntu 環境だと) 不要で、doc にある通りキーワード上で `K` を押すだけでリファレンスビューアが開きハイライトされて見易いリファレンスが表示される。

便利ですね
----------

なんか ref.vim の導入記事は結構あって、その中に refe の導入も一緒に書いてあることがほとんどだったんだけどその refe の導入の情報が微妙に古いのか一発で動く手順がまとまってるいい記事が\無かったのでメモする (refe2 でなく refe を導入していたり、データベースの作成について触れていないとか)。

参考
----

<a href="http://qiita.com/jnchito/items/5141b3b01bced9f7f48f">脱初心者を目指すVimmerにオススメしたいVimプラグインや.vimrcの設定 - Qiita</a>

<a href="http://qiita.com/kuranari_tm/items/aa4434bde1e3b83b71b6">Vimからrefeを使うまでの覚書 - Qiita</a>

<a href="http://qiita.com/hara/items/6dcd3c2fed326ed33510">Ruby - refe で最新のるりまを参照する - Qiita</a>



