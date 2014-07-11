---
layout: post
title: 解决安装 gem 时出现的 cannot load such file mkmf 问题
---
本地安装 jekyll 时，出现如下错误：

```bash
ERROR: Error installing jekyll:
ERROR: Failed to build gem native extension.
    /usr/bin/ruby1.9.1 extconf.rb
	/usr/lib/ruby/1.9.1/rubygems/custom_require.rb:36:in `require': cannot load such file -- mkmf (LoadError)
	from /usr/lib/ruby/1.9.1/rubygems/custom_require.rb:36:in `require'
	from extconf.rb:1:in `<main>'
	Gem files will remain installed in /var/lib/gems/1.9.1/gems/fast-stemmer-1.0.2 for inspection.
	Results logged to /var/lib/gems/1.9.1/gems/fast-stemmer-1.0.2/ext/gem_make.out
```

在 [Stack Overflow](http://stackoverflow.com/questions/12731904/rails-installation-failed-on-ubuntu-with-cannot-load-such-file-mkmf) 找到答案：mkmf 是 ruby-dev 的一部分，系统未安装。Debian 通过：

```bash
$ sudo apt-get install ruby1.9.1-dev
```
完美解决。
