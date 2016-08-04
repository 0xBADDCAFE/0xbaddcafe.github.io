---
title: 非同期処理から ListView を決まった順に追加する（のに付随した試行錯誤）
date: 2015-04-12 15:54 JST
tags: Android
---
android で Volley で引っぱってきたデータを順に ListView の Adapter に追加したいということがあって、但し Volley の処理は基本的に非同期でリスナーで行うのでそのまま追加すると順に入ってくれないということがあった。
READMORE
まず Volley で叩く API の為の key があって、追加したい要素数は分かっている。なので正解というか最終的な方法としては、Volley のリスナーの中で取得したデータをこの key と一緒に Map に詰めていって、key の数と Map の要素数の判定を全てのリスナーの中で行って一致した際（= 全ての非同期タスクの最後）に一括で adapter.add() するという形になった。

まあややこしく見えるので文で書くものではない。

で、やり口として不味かった方法もあった。

ひとつは、key をベースに先に adapter.add しておいて、それを書き替えるという方法。adapter にセットした List を変更する。これが一番筋が良く見えた、というか実際可能だと思うんだけど、set した List の変更を adapter に通知する為に notifyDataSetChanged() を呼ばないといけない。adapter の変更は通常 add や clear すると自動で更新されるものなので、notifyDataSetChanged() を呼ぶというのが気持ち悪く感じてやめた。

あとは [Adapter がセットする View を直接書き替える方法](http://stackoverflow.com/questions/4075975/redraw-a-single-row-in-a-listview) を試したけど、これも adapter が変更されていないので、fragment が切り替わったりして再描画がかかると adapter の持ってるデータに表示が置き変わった。開いている間に一時的かつ動的に書き替えたい場合はいいかもしれない。

あとひとつ、取得したデータは別の用途でも用いるので JsonObjectArray に格納していたんだけど、これのサイズと key の数を比較して最初の方法をやろうとした。これがハマって、空のJsonObjectArray に index を指定して格納していっていて、例えば非同期で 4 つ目の key にあたる処理が最初に完了して、put(4, obj) とかした場合、1-3 が無くても要素数は 4 を返す。これを何も考えずやって nullpo しまくった。

とりあえず忘れそうなので自分だけ分かればいい程度に殴り書きした。
