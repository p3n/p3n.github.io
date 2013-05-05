---
layout: post
title: privateとか
date: 2013-05-05 15:56:00
category : lessons
tags : [intro, 初心者, jekyll, todo]
---

ひとまずドラフトで保存とかはやっぱり普通にローカルに書き溜めておくものなのかな。
GitHubだしprivateはなさそうな。
あとひとつひとつタイトルつけるのが案外面倒くさい。パス名になるから仕方ないが。
アーカイブは上じゃなくて横につけたいな。すぐに飛びたい。

### コメントについて
デフォルトではdisqusになっている。
そのまま使うだけだと、いらぬDiscoveryというのがくっついてうざいため、Admin > Settings > Discoveryで、
Choose your Discovery levelのJust commentsを選んでおく。

### dateについて
なんだか知らないけど、dateを指定してるのに指定が効いてない。
この記事がローカルでは6 mayになってる。
あと、
    `jekyll --server --auto`
で起動してるのにオートで変更が適用されてなくて毎回上げ直してる。
今はいいけど大量になってきたら重そうだ。記事の変更をぱっぱと読み込んでくれないのかな。

### Markdorn記法
やっても適用されないと思ったら、ローカルに入ってなかった。  

    $ gem install redcarpet
    Fetching: redcarpet-2.2.2.gem (100%)
    Building native extensions.  This could take a while...
    Successfully installed redcarpet-2.2.2
    Parsing documentation for redcarpet-2.2.2
    unable to convert "\xCF" from ASCII-8BIT to UTF-8 for lib/redcarpet.bundle, skipping
    Installing ri documentation for redcarpet-2.2.2
    1 gem installed

しかしスペース4つ開けてるのに複数行のコード記法が適用されてない。  
→前後に改行が必要なだけだった。やれやれだ。  
[Markdown: Syntax](http://daringfireball.net/projects/markdown/syntax#precode)