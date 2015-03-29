---
title: 画像を指定のサイズで crop する、他
date: 2015-03-27 20:09 JST
tags: web, bootstrap, css
---

bootstrap で画像を並べたサムネイルギャラリーを作ろうとして、画像のサイズが完全にバラバラでｱｲｴｴしたので調べた。

READMORE

```css
.ratio{
  position:relative;
  width: 100%;
  height: 0;
  padding-bottom: 50%; /* % of width, defines aspect ratio */

  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
}
```

背景に画像を指定して、`background-size: cover;` でいい感じにするハックっぽい。調べてみると各所で `background-size: cover;` 便利という声を見つけたので覚えておく。

あとこれ背景画像で指定しているので普通の Lazy load は使えない。いい感じの無いかなーと探したらやっぱりあった。フェードインアニメーションとかはやってくれないみたいだけどあれのせいで遅く感じる部分もあるので個人的には不要。

```html
<div class="bg lazyload" data-bg="http://cdn.qiita.com/assets/siteid-reverse-cd0519106e5814e34d402b3e821820cf.png"></div>

<script src="./lazysizes/plugins/unveilhooks/ls.unveilhooks.js"></script>
<script src="./lazysizes/lazysizes.js"></script>
```

どうでもいいけどこれコードのシンタックス汚いですね。気が向いたら変えよう。

参考
----

<a href="http://stackoverflow.com/questions/12694919/cropping-the-image-to-aspect-ratio-in-bootstrap-responsive-grid">css - Cropping the image to aspect ratio in bootstrap responsive grid - Stack Overflow</a>

<a href="http://qiita.com/suisho/items/3ad3c0eded587e432aa5">究極で軽量なlazyloader。lazysizes - Qiita</a>
