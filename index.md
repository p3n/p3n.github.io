---
layout: page
title: 403 everywhere
tagline: 
---
{% include JB/setup %}

### このページの説明
ruby + jekyll + jekyll bootstrap で作られ、GitHubによってホスティングされています。  
みんなタダで（Unix系OSなら）簡単です。すばらしい。  
……使うだけじゃなくて貢献しないといけないんだけどね、ほんとは。  
  
### 最近の投稿

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
