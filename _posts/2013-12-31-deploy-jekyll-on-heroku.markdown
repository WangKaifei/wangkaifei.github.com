---
layout: post
title: 在 heroku 上部署 jekyll
---
在 heroku 上部署了 jekyll，中间出现过几次折腾，记录下过程。

```
1) cd to your jekyll directory
2) add config.ru (see example bellow)
3) build pages, type: jekyll
4) add Gemfile (see example bellow)
5) git init && git add .
6) git commit -m "first heroku app"
7) git push heroku master
```
config.ru:

```
require "rack/jekyll"
run Rack::Jekyll.new
```

Gemfile:

```
source "http://rubygems.org"
gem "rack-jekyll"

```
在第一次推送时，提示 `Gemfile.lock required. Please check it...`，部署失败，后来从 Stackoverflow 找到答案，进行如下操作：

```
8) sudo bundle install --deployment
9) git commit -a Gemfile.lock -m " add Gemfile.lock"
10) git push heroku master
```
That's all.

参考网站：

1. [rack-jekyll](https://github.com/adaoraul/rack-jekyll)
2. [Push Rack-Jekyll app to Heroku](http://stackoverflow.com/a/3126100)
3. [The --deployment flag requires a Gemfile.lock](http://stackoverflow.com/a/17189031)
