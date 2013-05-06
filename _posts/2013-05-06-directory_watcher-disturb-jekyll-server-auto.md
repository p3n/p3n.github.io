---
layout: post
title: jekyll --server --autoが利かない
date: 2013-05-06 16:15:00
category : lessons
tags : [jekyll, trouble]
---

Octopressで`rake preview`がちゃんと動かなくなる現象が、こちらにもあったようだ。  
話の経路としては逆なんだけどともかく、directory_watcherは1.5.1になるとうまく作動しない。

	$ gem list
	
	*** LOCAL GEMS ***
	
	bigdecimal (1.2.0)
	bundler (1.3.5)
	classifier (1.3.3)
	directory_watcher (1.5.1)
	fast-stemmer (1.0.2)
		:
	 （中略）
		:
	yajl-ruby (1.1.0)

バージョンを落とすには、一度アンインストールしてからインストールしなおす必要がある。

	$ gem uninstall directory_watcher && gem install directory_watcher -v 1.4.1
	
	You have requested to uninstall the gem:
		directory_watcher-1.5.1
	
	jekyll-0.12.1 depends on directory_watcher (~> 1.1)
	If you remove this gem, these dependencies will not be met.
	Continue with Uninstall? [yN]  y
	Successfully uninstalled directory_watcher-1.5.1
	Fetching: directory_watcher-1.4.1.gem (100%)
	Successfully installed directory_watcher-1.4.1
	Parsing documentation for directory_watcher-1.4.1
	Installing ri documentation for directory_watcher-1.4.1
	Done installing documentation for directory_watcher after 0 seconds
	1 gem installed

これで無事、記事の変更を即時確認できるようになった。  
本来こうだったのか……。

* [Jekyll's “--auto” doesn't work?](http://stackoverflow.com/questions/15591000/jekylls-auto-doesnt-work)