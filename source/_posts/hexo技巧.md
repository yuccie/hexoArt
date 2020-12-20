---
title: hexo技巧
categories:
  - Hexo
tags:
  - tip
date: 2020-12-20 10:32:12
---


### 模板

在 `scaffolds` 文件夹里的文件，是新建文件时的模板，文件根据类型不同，分为不同的模板：
- draft，草稿
- page，页面
- post，文章
- 自定义类型

#### draft相关

当一些文章还没有写完，可以先创建 draft 模板，这样就不会发布，也就不会被别人看到。当文章编写完成后，再发布即可：`hexo publish draft 文章名`，其实还可以使用简写：`hexo p draft 文章名`，意思就是将草稿箱里的文章发布，即挪到 `_posts` 文件夹下。

但开发阶段如何预览呢(但这样文章会被看到)：
- 在执行时加上 --draft 参数
- 把 render_drafts 参数设为 true 来预览草稿

#### 自定义模板

当然可以自定义模板，只需要在 `scaffolds` 里新建文件即可，文件名即是模板名。

新建基于该模板的文件时，只需：`hexo new new_tpl new_file_name` 即可。

### 端口

hexo 启动服务时默认是4000端口，如果冲突了就无法启动，此时可以：`hexo s -p 新端口` 即可。

### 部署到github

当然也可以部署到gitlab等，需要在配置文件 `_config.yml`（yml是一种文件格式，其实也可以使用json，但json在这里稍微麻烦些）里配置

```
# Deployment
## Docs: https://hexo.io/docs/one-command-deployment
deploy:
- type: git
  repo: git@github.com:yuccie/hexoArt.git
  message: hexo文章更新发布
# 还可以部署多个 
# - type: heroku
#   repo: xxx
```

但部署到服务器后，访问域名，提示资源404，原因是`https://yuccie.github.io/hexoArt/`应该为根地址，但资源获取的根地址却是`https://yuccie.github.io`。。。
