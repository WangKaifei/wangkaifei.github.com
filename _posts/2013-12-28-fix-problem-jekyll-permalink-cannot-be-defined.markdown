---
layout: post
title: 解决通过 _config.yml 自定义固定链接后不生效的问题
---
本地开启 jekyll server ，并开启 `--watch` 参数，修改 post 的分类、title，生成的 permalink 均发生变化。但通过修改 `_config.yml` 来自定义 permalink 时，自定义链接不生效。

通过万能的 Google，最后在一份旧文档[Jekyll固定链接](http://zhouyichu.com/%E7%BF%BB%E8%AF%91/2012/12/05/Jekyll-Wiki-Permalinks.html)中找到了原因：

> 即使 `--auto` 选项被打开了，当你在Jekyll运行时修改其固定链接的风格，你需要重新启动Jekyll才能使新的风格生效。