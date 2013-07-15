---
layout: post
title: "カテゴリを複数指定する"
description: ""
category: lessons
tags: [jekyll]
---
{% include JB/setup %}

[jekyllを1.0.2に上げてみる他](http://p3n.github.io/lessons/2013/05/19/jekyll-update-to-1_0_2/)で書いたように

	$ rake post title="have both categories"

すると自動で記事が作られる。デフォルトテンプレートが、

	---
	layout: post  
	title: "have both categories"  
	description: ""  
	category:   
	tags: []  
	---

こういう感じで入るのだけど、categoryにスペースやカンマ区切りで複数入れようとしても入らない。  
categoriesにした上でスペース区切りにするか、tagsと同じようにブラケットで囲ってカンマ区切りにするのがお手軽。カテゴリ自体にカンマやスペースを入れたい場合は配列にするらしい。


#####参照 
* [Jekyll のカテゴリーとタグの指定方法 3 パターン](http://tech.nitoyon.com/ja/blog/2013/04/17/jekyll-pluralize/)