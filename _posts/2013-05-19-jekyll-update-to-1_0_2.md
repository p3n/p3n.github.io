---
layout: post
title: "jekyllを1.0.2に上げてみる他"
category : lessons
tags : [jekyll]
---
{% include JB/setup %}

### jekyll 0.12.1 -> 1.0.2
このバージョンでdirectory_watcherが1.5.1だとpostの変更を取れない問題も一緒に修正されている。

[Jekyll 1.0 がリリースされてた][1]によると`_config.yml`でexcludeを変えないといけないという情報だけれど、`jekyll serve -w`とか`jekyll doctor`などとやっても特に何も言われなかった。

ただ、

    Deprecation: Auto-regeneration can no longer be set from your configuration file(s). Use the --watch/-w command-line option instead.

などと言われるので、`_config.yml`の`auto: true`を外しておく。

###バージョンアップとは関係ないところ
いちいち自分で作るの面倒などと書いていたが、

    $ rake post title="jekyll-update-to-1.0.2"

などとやれば[ちゃんとできるじゃん][2]かだめすぎる。  
`{{"{% include JB/setup "}}%}`が入ってくれて、デフォルトだと日時をよしなに解決してくれる。

なお、これはOctopressでの

    $ rake new_post["jekyll-update-to-1.0.2"]

に相当。サーバ上げるのは`jekyll serve`で、変更監視入れるには

    $ jekyll serve -w

になった。前は`jekyll --server --auto`だったのがサブコマンド式に変わったみたいだ。Octopressでは

    $ rake preview

なのでまだこっちのが簡単だけれども。

####jekyllのエスケープについて
`{{"{% include JB/setup "}}%}`などをエスケープしたい場合、 &#123;&#123;&#34; と &#34;&#125;&#125; で囲めばいいようだ。  
ただ、`%}`などのあとにやってもうまく行かない。

> &#123;&#123;&#34;{{"{% include JB/setup &#34;&#125;&#125;"}}%}

こういう感じ。

####URLの参照形式

`[Google][1]`というように文中に書いておいて、どっか別の場所（段落やポストの最後）を参照できる。  
`[1]: <http://www.google.com> "Google"`
というようにしておけば、

[Google][3]

となってくれる。文中にそのまま仕込む`[Google](http://www.google.com)`よりも見やすくできる。

今回から採用してるけど、参照をそのまま出したいときはどうするんだろう？（はてななんかの脚注みたいな感じ）

####脚注
ぐぐったら`[^id]`みたいにして使えるとあるけど、うまいこと機能しない。[ここ][4]によれば、`_config.yml`に追記すれば行ける。

    markdown: redcarpet
    redcarpet:
        extensions: [footnotes]

ただし、forkしてるところじゃないとfootnotesは対応していないようだ。pull requestとかで取り込まれてないのかな？

###参照
* [Jekyllでliquidテンプレートタグをエスケープする
](http://fingaholic.github.io/posts/2012-08-08-escape-liquid-template-tags.html) 
* [Markdown文法の全訳 Links – リンク](http://blog.2310.net/archives/6#links)
* [Markdownの使用方法](http://www.kawaz.org/projects/kawaz/wikis/Markdownの使用方法/)



[1]: <http://www.kaoriya.net/blog/2013/05/07/> "KaoriYa"
[2]: <http://jekyllbootstrap.com/usage/jekyll-quick-start.html#2_create_a_post> "Jekyll Quick Start"
[3]: <http://www.google.com> "Google"
[4]: <http://blog.jerodsanto.net/2013/05/jekyll-with-footnotes/>