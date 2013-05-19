---
layout: post
title: 導入 - privateとか
date: 2013-05-05 15:56:00
category : lessons
tags : [intro, 初心者, jekyll, todo, Markdown]
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
　→可能だった。単にdirectory_watcherが1.5.1で[うまく動作してくれない](http://stackoverflow.com/questions/15591000/jekylls-auto-doesnt-work)だけ。

### Markdown記法
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

### GitHubまわり
これも普通にリポジトリなのでIssuesも使えるはず。  
TODOを中身に書くと鬱陶しいし、別管理はどっか行ってしまう。楽そうだ。コミットログとIssuesのつなぎも簡単。  
Wikiは使わない気がするけどわからない。  
GitHubの練習によさそう。写経をpushしちゃうと著作権法に引っかかるからGitだけの練習にしかならん。  

### Octopress
自分で逃げられる部分が少ないので、ちゃんと手順を踏まないといけない。  
アカウントが違うと鍵を二つ用意しないといけなかったり（あるのをGitHub側で設定すればいいのかもしれないけど）  
ローカルのユーザ名を見てくれない疑惑がある。globalが使われてしまうのかな。  
アカウント使い分ける人もあんまりいないだろうけど、ネットと実社会は離れててほしい……。  
こっちは素に近いから、こっちがローカル設定すればいいのかなあ。

ただ、自動化されてるだけあってすごく便利。  
`$ rake new_post["test post"]`でページが作れて、`rake preview`でサーバが上がる。deployもrakeで行ける。  
変な実験したり遊んだりしないならこっちのが良さそうだ。