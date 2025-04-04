---
title: 将hugo模板布置到github上做自己的blog记录
description: About the use of github
slug: github pages
date: 2025-04-04 00:00:00+0000
image: cover.jpg
categories:
    - github_uses
weight: 1       # You can add weight to some posts to override the default sorting (date descending)
---

# 部署自己的github pages

## 1.关于github和git的使用

### 1.1 ssh

这个地方问题比较大，因为之前用户名设置成中文，所以连接ssh的时候一直报错找不到文件夹

```bash
ssh -T git@github.com git@github.com: Permission denied (publickey).
```

然后要先更改用户名，其实有教程[更改用户名](https://blog.csdn.net/highlighters/article/details/125133965)

，不过因为自己比较懒，（确实课比较多）然后就远程工程师了，但是具体教程和这个差不多，但是远程是装了一个mini系统，代替这个教程里的另一个账户，以防账户出问题

配置ssh具体教程如下

[ssh](https://blog.csdn.net/weixin_42310154/article/details/118340458)

现在文件夹下应该两种密钥都有了，下次直接cat开始就可以了。

### 1.2处理git clone的网络连接问题

首先注意git clone 的网址其实是在库code里的，不是直接clone的 

![gitclone](C:\Users\DanicaYang\stack\content\post\hello-world\gitclone.png)

git clone问题的三个解决办法

- 首先就是梯子tune模式（全局模式，正常的梯子在终端是不适用的，所以开tone偶模式）

- 第二个使用ssh克隆

```bash
git@github.com:Danicayy/danicayy.github.io.git
```

后面还是不行，就直接终端代理了，因为用的是git bash所以就直接和linux一样的配置[终端配置](https://weilining.github.io/294.html)其中的代理端口要自己找

- 查找方法：控制面板-网络和internet-internet选项-连接-局域网设置

![internet](C:\Users\DanicaYang\stack\content\post\hello-world\internet.png)

### 1.3 pull or push?

pull的意思是把库里面的东西拉到本地，push的意思是把我的东西推到库里面

git是本地，github是远程，远程和本地都可以对仓库进行修改，如果在远程修改过，那么相当于远程仓库更进一步，所以在本地要进行

```bash
git pull
```

否则会报错本地和远程库不同同步

本地更改之后就是三件套

```bash
git add . //这个意思是把所有文件加到push的阵列里面
git commit -m "message" //委托一下，同时为了辨别一下加一句message
git push //直接推进去
```

workflow有一个这样的文件夹，只有触发workflow的命令的时候才会有这个message

大概是这样？记不太清整个过程了，后面再碰见再努力吧

### 1.4 git push&VScode

> 微软大战code和github

vscode上面配置git graph

然后每次打开文件夹第三个tree 看好更改之后commit之后push就可以了，可以清晰的看到远程和本地库的更改分支

![gitgraph](C:\Users\DanicaYang\stack\content\post\hello-world\gitgraph.png)

好像就这些？

## 2.网页的设置

### 2.1 hugo模板的使用

首先是hugo要配置整个go语言

整个参考了这个[博客](https://www.cnblogs.com/liumylay/articles/17936667.html),然后[官网](https://hugo.opendocs.io/)其实也有教程，注意自己找的主题模板，比如我现在用的starter本身就是一个完整的库，不要自己再创建一个库然后

```bash
git init
```

会报

```bash
.githubmodule 内容缺失的错
```

就是因为在库里面嵌套了一个库

### 2.2网页的开发者模式

正常应该是F12进开发者模式，但是很明显，小新没有这个，但是之前误打误撞发现是 ctr+shift+c（就是忘了这个是windows，当成是linux的终端发现的）

然后就这个可以对应界面是哪一段代码，里面就可以进行更改

![web](C:\Users\DanicaYang\stack\content\post\hello-world\web.png)