---
layout: post
title:  "Setup Jekyll and Github-Pages"
date:   2023-04-24 19:13:54 +0800
categories: jekyll settings
---
本网站的配置主要依据 [Github Pages 官方教程](https://docs.github.com/en/pages)，本博客仅记录 [Prerequisites](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll#prerequisites) 中在 Win10 上安装并使用 [Ruby](https://www.ruby-lang.org/en/) 和 [Bundler](https://bundler.io/) 及配置 [Jekyll](https://jekyllrb.com/) 中碰到的问题及相应的解决方案。

## 安装 [Ruby](https://www.ruby-lang.org/en/)

官方推荐的教程是 [Jekyll 官方教程](https://jekyllrb.com/docs/installation/windows/#installing-ruby-and-jekyll)，但是实际我是根据[第三方教程](https://idratherbewriting.com/documentation-theme-jekyll/mydoc_install_jekyll_on_windows.html#install-ruby-and-ruby-development-kit)安装成功的。

最后发现两者在安装Ruby这块没啥区别，只要注意安装时一定要勾选安装`MSYS2 and MINGW development tool chain`。

安装完成后，只需打开一个新的终端即可输入以下命令来检验Ruby是否可以正常使用：
```shell
ruby -v
# Output: ruby 3.2.2 (2023-03-30 revision e51014f9c0) [x64-mingw-ucrt]
```

与此同时，Ruby的包管理工具 `gem` 也应该已经安装完成：
```shell
gem -v
# Output: 3.4.10
```

由于众所周知的原因，使用国内的镜像源会更快。网上大多推荐[国内镜像源](https://gems.ruby-china.com/)，但是使用时[有问题](./2023-04-24-Setup-Jekyll-and-Github-Pages.markdown#问题)，换了[清华源](https://mirrors.tuna.tsinghua.edu.cn/rubygems/)之后就解决了，因此最终我选择使用[清华源](https://mirrors.tuna.tsinghua.edu.cn/rubygems/)，以下为修改 `gem` 默认源的命令：
```shell
gem sources -r https://rubygems.org/ -a https://mirrors.tuna.tsinghua.edu.cn/rubygems/
# Output:
# https://mirrors.tuna.tsinghua.edu.cn/rubygems/ added to sources
# https://rubygems.org/ removed from sources
```

使用以下命令可以查看 `gem` 当前的源，证明换源成功：
```shell
gem sources
# Output:
# *** CURRENT SOURCES ***
#
# https://mirrors.tuna.tsinghua.edu.cn/rubygems/
```

## 安装 [Bundler](https://bundler.io/)

[Github Pages 官方教程](https://docs.github.com/en/pages) 推荐使用 [Bundler](https://bundler.io/) 来部署 [Jekyll](https://jekyllrb.com/), 他的作用和用法有点类似 Python 的环境管理工具 `pip` 和 C/C++ 系列的 `make` ，其好处在于可以为每个项目单独配置所需的包和插件，而不是全都装在系统的默认路径下。

在 Windows 的开启菜单的搜索栏中搜索 `cmd`，选择“以管理员身份运行”后，使用以下 `gem` 命令安装即可：
```shell
gem install bundler
```

同理，我们也需要修改其配置，使其从镜像源安装：
```shell
bundle config mirror.https://rubygems.org https://gems.ruby-china.com
```

Bundler 需要配合 Gemfile 使用，在 Gemfile 中第一行可以指定下载源，为了在github上部署时和本地使用时使用不同的源，可以使用该命令来设置镜像源，此时配置会写在`.bundle/config`文件中。在本地和远端使用不同的分支即可使用相应的配置。

## 使用 [Bundler](https://bundler.io/) 部署 [Jekyll](https://jekyllrb.com/)

参考文章：[Using Jekyll with Bundler](https://jekyllrb.com/tutorials/using-jekyll-with-bundler/) 和 [Github Pages 官方教程](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll#creating-your-site)

### 问题

从[国内镜像源](https://gems.ruby-china.com/)拉取包元数据，网站上显示最新版的 `github-pages` 的版本号为 `228` ，但是实际拉取的时候却显示只有 `188` 及之前的版本，更换[清华源](https://mirrors.tuna.tsinghua.edu.cn/rubygems/)后，问题解决。

![国内镜像源网站上显示最新版228存在](https://s2.loli.net/2023/04/24/yqYgliIAXW3boHV.png)

![本地拉取时显示没有](https://s2.loli.net/2023/04/24/s2eHJYazbUuvWFQ.png)
