---
title: Git
lock: need
---

# Git 使用说明和配置

作者：小傅哥
<br/>博客：[https://bugstack.cn](https://bugstack.cn)

> 沉淀、分享、成长，让自己和他人都能有所收获！😄

<iframe id="B-Video" src="//player.bilibili.com/player.html?isOutside=true&aid=113087713643443&bvid=BV1idHUeLECY&cid=25755911382&p=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true" width="100%" height="480"> </iframe>

大家伙，我是技术UP主小傅哥。

**不会Git操作的伙伴，轻则写不了代码，重则误操作搞丢自己的代码或者干掉别人的代码。** 因为进入公司后，就不只是你一个人在一个工程上写代码，而是所有这个项目组的伙伴都需要在这个工程上写代码，大家要在统一的Git的规范完成代码开发和提交。—— 🤨 不信的话，进入公司乱删个Git分支或者随便任何一个分支提交代码试试。

<div align="center">
    <img src="https://bugstack.cn/images/article/project/big-market/big-market-v7-01.gif" width="150px">
</div>

**Git的作用是什么？**

你可以想象下，当你有10个小伙伴都需要在一个 txt 文档里，写一份老师👩🏻‍🏫上课的笔记📒，把信息进行汇总、互相完善、用于课后学习。那么怎么保证大家做的课堂内容都能顺利的写在一份 txt 呢，而且不要互相删除，也不要丢失谁的信息呢？

这个就是 Git 的用途。Git 是一种分布式版本控制系统，用于高效地管理和跟踪源代码和文件的历史记录，支持多人协作开发及分支管理，提供可靠的版本回退和合并机制，从而提高开发效率和代码质量。

## 1. Git 起源故事

讲到 Git 就不得不提一下 Linux，因为如果没有 Linux 也就没有 Git 的诞生，这里是有一段 **10天** 写出 Git 的故事！

众所周知，Linus 于 1991年 创建了开源的 Linux，从此 Linux 系统不断发展壮大。但 Linux 的壮大是靠全世界热心的开发者参与的，不过这么多人在世界各地为 Linux 编写代码，那代码是如何管理的呢？事实是，2002 之前，合并代码的操作都是 Linux 老爷子自己手动合并的！

但 2000 年的时候，不是已经 [SVN](https://zh.wikipedia.org/wiki/Subversion) 可以使用了吗？但 Linus 坚决反对 CVS、SVN 这些集中式的管理工具，不仅速度差还得联网操作。虽然有商用版的功能好一些，但这与 Linux 开源精神不符。所以 Linus 就不用，看人家这开源精神！

不过到了 2002年，Linux 都发展10年了，在这么手动的合并代码，让社区的兄弟也苦不堪言，强烈反对。为此，林纳斯·托瓦兹（Linus Torvalds）决定使用 BitKeeper 作为 Linux 内核主要的版本控制系统用以维护代码。BitKeeper 的东家 BitMover 公司，看 Linux 开源的不容易，授权 Linux 社区免费使用这个版本控制系统。

哈哈哈，但好景不长！2005年，安德鲁·垂鸠（Andrew Tridgell）写了一个简单程序，可以连接 BitKeeper 的仓库，BitKeeper 著作权拥有者拉里·麦沃伊认为安德鲁·垂鸠对 BitKeeper 内部使用的协议进行逆向工程，决定收回无偿使用 BitKeeper 的许可。Linux 内核开发团队与 BitMover 公司进行磋商，但无法解决他们之间的歧见。林纳斯·托瓦兹决定自行开发版本控制系统替代 BitKeeper ，以10天的时间编写出 git 第一个版本！—— 牛皮！

有了 Git 以后，GitHub 平台也于2007年10月1日开始开发。网站于2008年2月以beta版本开始上线，4月份正式上线。GitHub 里面的项目可以通过标准的 Git 命令进行访问和操作。—— 这就是 Linux、Git、Github 的故事。

## 2. 软件安装

Git 是一个软件工具，在使用前需要进行安装。

- 地址：[https://git-scm.com/downloads](https://git-scm.com/downloads) - `选择需要的版本下载` 网盘资源：[https://www.alipan.com/s/LqwsNfHRx54](https://www.alipan.com/s/LqwsNfHRx54) - `也提供了 Git 软件，在 dev-ops -> 环境 -> git 下`
- 演示：[https://learngitbranching.js.org/](https://learngitbranching.js.org/) - `可直接查看动画效果，引导式学习Git命令操作。`

**配置代理**

```java
git config --global http.proxy ip:port
git config --global https.proxy ip:port
```

- 如果你有代理地址可以配置

### 2.1 Mac

```java
# 如果你没有 brew 命令，则需要先安装下；https://brew.sh/index_zh-cn
brew install git
```

### 2.2 Windows

- [32-bit Git for Windows Setup](https://github.com/git-for-windows/git/releases/download/v2.41.0.windows.1/Git-2.41.0-32-bit.exe)
- [64-bit Git for Windows Setup](https://github.com/git-for-windows/git/releases/download/v2.41.0.windows.1/Git-2.41.0-64-bit.exe)

### 2.3 Linux

#### Debian/Ubuntu

获取适用于您的 Debian/Ubuntu 版本的最新稳定版本

```
# apt-get install git
```

对于 Ubuntu，此 PPA 提供最新的稳定上游 Git 版本

```
# add-apt-repository ppa:git-core/ppa
# apt update; apt install git
```

#### Centos 

```java
sudo yum install git
```

## 3. 配置账户

当你拿到一个Git的仓库（Github、Gitcode、Gitee、GitLab），让你克隆（git clone）代码的时候，不要`虾呵呵`的上去就点个zip下载。

<div align="center">
    <img src="https://bugstack.cn/images/roadmap/tutorial/road-map-git-01.png" width="700px">
</div>

- zip 下载的代码，只是当前分支的，下载后用 IntelliJ IDEA 打开也没有 Git 标识，不能进行仓库的pull、push、checkout等操作。
- 另外对于一些工程内容比较大的项目，直接 zip 下载还可能会失败。

>你要做都是配置账户 ssh 秘钥，或者下载的时候输入 git 仓库账号密码（目前很多仓库为了安全，不在支持账号密码方式下载代码了。）

**注意**：gitcode.com、github.com 都需要创建访问令牌当做账号密码的密码使用。而不是直接使用账号里你设置的那个密码。

如 [https://gitcode.com/setting/token-classic](https://gitcode.com/setting/token-classic)

<div align="center">
    <img src="https://bugstack.cn/images/roadmap/tutorial/road-map-git-20.png" width="850px">
</div>

### 1. 配置git账户

```java
[root@lavm-aqhgp9nber ~]# git config --global user.name "fuzhengwei"
[root@lavm-aqhgp9nber ~]# git config --global user.email "184172133@qq.com"
```

- 用户名和邮箱，更换为你的代码库注册使用的名称和邮箱📮。

### 2. 创建ssh秘钥

```java
[root@lavm-aqhgp9nber ~]# ssh-keygen -t rsa -C "184172133@qq.com"
Generating public/private rsa key pair.
Enter file in which to save the key (/root/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /root/.ssh/id_rsa.
Your public key has been saved in /root/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:lgf+3a1srOvDD0znv+/jiR3iwMaZtxW94k9FI1HzJAk 184172133@qq.com
The key's randomart image is:
+---[RSA 2048]----+
|            Eoo+.|
|              ooo|
|        .    . .o|
|       . o    ..o|
|        S . . ..o|
|       . oo+o+ .+|
|          .O+=o=.|
|          . Bo@+o|
|           .+@*BB|
+----[SHA256]-----+
```

- 命令：`ssh-keygen -t rsa -C "184172133@qq.com"`
- 操作：一路敲回车同意就可以了。

### 3. 获取ssh秘钥

```java
[root@lavm-aqhgp9nber ~]# cat /root/.ssh/id_rsa.pub 
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC7eYQiDe46Jq5CJ6vXtIiM0hxUKKgCoSFIkSQucsZoLjhW53guxmZ0aR+gUZb/M8Xgrk9WMxc32KqQasFy0xPo86Hxagd40fPz+XdwOyokEJC5He6F1********CkATF2YgEdtcRW2RPICjtLr*******DWkS8ez 184172133@qq.com
```

- 命令：`ssh-keygen -t rsa -C "184172133@qq.com"`
- 操作：`Your public key has been saved in /root/.ssh/id_rsa.pub.` 按照提示地址，获取 pub 公钥。如果是linux就通过 cat 获取。如果是本机电脑就按照路径打开。
- 注意：`.ssh` 点开头的文件夹是隐藏文件，Windows/Mac 都可以设置查看隐藏文件。Windows 是设置里配置，Mac 是通过 `Shift + Command + .` 开启和关闭查看隐藏文件。

### 4. 配置ssh秘钥

#### 4.1 gitcode.net

<div align="center">
    <img src="https://bugstack.cn/images/roadmap/tutorial/road-map-git-02.png" width="600px">
</div>

- 秘钥配置地址：[https://gitcode.net/-/profile/keys](https://gitcode.net/-/profile/keys)

#### 4.2 github.com

<div align="center">
    <img src="https://bugstack.cn/images/roadmap/tutorial/road-map-git-03.png" width="600px">
</div>

- 秘钥配置地址：[https://github.com/settings/keys](https://github.com/settings/keys)

---

其他的各个代码库平台也都类似，找到配置 ssh 秘钥的地方，把 id_rsa.pub 内容填充进去即可。

## 4. 检出代码 - 命令

通过在公司工作，大家会说检出代码，不会说下载。因为检出对应的是 git clone 命令，而下载是 http 直接点击链接。在我们使用一些图形化的 git 界面操作代码检出的时候，走的也是 git clone 命令。

### 4.1 检出地址

<div align="center">
    <img src="https://bugstack.cn/images/roadmap/tutorial/road-map-git-04.png" width="600px">
</div>

- 地址：选择工程的 ssh 地址，这个是你配置 ssh 秘钥后的检出方式。

### 4.2 检出命令

#### 4.2.1 默认检出（master）

```java
git clone git@github.com:fuzhengwei/openai-code-review.git
```

- 你可以复制你需要的工程地址进行检出。

#### 4.2.2 指定分支

```java
git clone -b 240720-xfg-init-project git@github.com:fuzhengwei/openai-code-review.git
```

- 添加 `-b 分支名`，可以指定分支名称检出。

#### 4.2.3 其他命令

- git branch：查看当前工程分支
- git branch -r：查看远程分支列表
- git pull：拉取分支最新代码
- git push：推送本地变更的代码。【这样的操作有图形化界面，更方便】
- git fetch：获取远程仓库最新分支变动，这个很有用。在你想操作分支创建新或者看其他人的分支时候，先操作下 git fetch 看下最新的分支变动。
- git merge origin/master：将远程分支的 master 代码合并到本地分支 master 上。【类似这样的操作有图形化界面，点击即可】

## 5. 检出代码 - IntelliJ IDEA

IntelliJ IDEA 本身就提供了 Git 的图形化操作，也是最简单最常用的方式。只要你的代码是通过 Git 检出的，那么通过配置 Git 的 IntelliJ IDEA 打开工程，就会自动的被 Git 管理。

### 5.1 配置 Git

<div align="center">
    <img src="https://bugstack.cn/images/roadmap/tutorial/road-map-git-05.png" width="700px">
</div>

- 像是 Mac 电脑会自动默认的配置好 IntelliJ IDEA Git 直接使用即可，如果你的电脑在 IntelliJ IDEA 打开工程后，提示没有 Git 则可进入设置手动配置。
- 配置后，点击 Test 可以测试出 Git 的版本。

### 5.2 检出代码

#### 5.2.1 方式1；打开工程前

<div align="center">
    <img src="https://bugstack.cn/images/roadmap/tutorial/road-map-git-06.png" width="700px">
</div>

#### 5.2.2 方式2；打开工程后

<div align="center">
    <img src="https://bugstack.cn/images/roadmap/tutorial/road-map-git-07.png" width="400px">
</div>

- 打开工程后，也可以通过菜单栏中的 Git 进行检出操作。

### 5.3 图形界面

#### 5.3.1 分支使用

<div align="center">
    <img src="https://bugstack.cn/images/roadmap/tutorial/road-map-git-08.png" width="750px">
</div>

#### 5.3.2 提交代码

<div align="center">
    <img src="https://bugstack.cn/images/roadmap/tutorial/road-map-git-09.png" width="600px">
</div>

#### 5.3.3 查看记录

<div align="center">
    <img src="https://bugstack.cn/images/roadmap/tutorial/road-map-git-10.png" width="750px">
</div>

#### 5.3.4 查看对比

<div align="center">
    <img src="https://bugstack.cn/images/roadmap/tutorial/road-map-git-11.png" width="750px">
</div>

- 这个代码对比非常适合代码评审，也可以用于自己学习代码。可以知道任意两个分支的代码差异，也就知道了代码上一次是什么样，这一次是做了什么开发。

#### 5.3.5 合并分支

在公司中很多时候是大家一起在一个工程开发代码，那么这个时候就会涉及合并代码的。如果有多人共同开发一个接口方法，就会在合并的时候产生冲突。所以要特别注意。

注意，📢在Git中，`merge`和`rebase`是两种用于合并分支变更的方法。每种方法都有其特定的用途和行为：

Merge

- **概念**: `merge`命令用于将一个分支的更改合并到当前分支，通常会生成一次新的合并提交（commit），从而保留分支历史。
- **历史记录**: 使用`merge`会保留所有开发历史记录，包括分支点，这使得历史记录图呈现出一个分叉和合并的树状结构。
- **使用场景**: 
  - 当你想保留完整的历史记录，了解如何以及何时进行了分支。
  - 通常用于将分支合并到主分支(如`main`或`master`)时，以保留分支的历史上下文。
- **命令**: 
  ```bash
  git checkout main
  git merge feature-branch
  ```

Rebase

- **概念**: `rebase`命令用于重新定位一系列的提交，可以将分支上的更改申请到另一分支的顶端，因而能得到更线性的历史。
- **历史记录**: Rebase重新写了提交历史（改变了提交的父提交），这会导致更线性的提交历史，从而更清晰，但会丢失分支合并信息。
- **使用场景**:
  - 当你希望提交历史更加简洁和线性。
  - 合并特性分支到主分支前用以避免杂乱的分支合并历史。
  - 需要小心在共享分支上使用，因为重写的提交历史会影响他人。
- **命令**:
  ```bash
  git checkout feature-branch
  git rebase main
  ```

选择何时使用

- **Merge**适合用于保持完整的提交历史，不改变现有提交的哈希。
- **Rebase**适合用于清理提交历史，通常在提交尚未推送至共享存储库时使用。

一般情况下，对于已对外分享的分支，尤其是共享存储库中的`main`或`master`分支，尽量避免使用`rebase`。而对于个人开发的特性分支，`rebase`可以帮助维护一个清晰的提交历史。

**普通合并**

<div align="center">
    <img src="https://bugstack.cn/images/roadmap/tutorial/road-map-git-12.png" width="750px">
</div>

- 在实际的开发中，大家承接新的需求，会从master拉一个新的分支。拉取后，开始编写代码，完成开发后提交。
- 之后切换到master分支，通过把自己的开发的分支合并回master分支进行提交。
- 注意：如果多人开发，同时修改一个类，可能会引起合并冲突，这个审核要点开类，查看冲突进行合并，不要把自己和他人的代码合并丢失。

**冲突合并**

<div align="center">
    <img src="https://bugstack.cn/images/roadmap/tutorial/road-map-git-22.png" width="950px">
</div>

1. 选择，你要从哪个分支合并到 test 分支。右键选择 Merge into test
2. 如果你合并到test分支的代码，有其他人也在同一行做了改变或者格式化了代码，就会弹出一个合并冲突。这个时候你需要点 Merge 进行合并。
3. 在点击 Merge 后，你会看到具体冲突的代码是什么，你可以有选择的从左右合并到中，最后点击 Apply。这个时候要注意不要把让别人的代码合并丢喽。
4. 合并完的代码，不要直接 push，你要先本地 install 看是否可以打包。以及如果可以运行的话，可以本地先跑一下。 最后 push 提交合并代码即可。

#### 5.3.6 回滚分支

回滚提交和回滚push

<div align="center">
    <img src="https://bugstack.cn/images/roadmap/tutorial/road-map-git-13.png" width="750px">
</div>

如果出现了合并代码冲突后，丢失了代码，那么这个时候一般要进行回滚操作，重新合并。

虽然 Git 提供了回滚代码的功能，但一定要谨慎使用。怎么谨慎？第一个谨慎就是 push 的代码一定确保可以构建和运行，否则不要 push！第二个谨慎是要回滚代码，需要和团队中对应的伙伴打招呼，避免影响别人测试或者上线。

<div align="center">
    <img src="https://bugstack.cn/images/roadmap/tutorial/road-map-git-23.png" width="950px">
</div>

1. 先选择要在哪个分支的哪次提交上进行回滚。这里选择的是 test 分支上的提交进行回滚。
2. 这里选择 Hard 回滚。因为我们所有的都是合并到 test 分支，所以 test 分支丢失也没问题。可以重新合并。但要和同组伙伴提前说明。
3. 回滚后，你会看到代码只剩下从回滚往下的提交内容了。
4. 回滚后，你不能直接 push 提交了，这个之后会报错；`fast-forward` 因为此时本地分支落后于远程分支。
5. 所以要通过 `git push origin HEAD --force` 进行强制提交。或者你可以把 test 的远程分支删掉，之后在提交。

## 6. 提交工程 - IntelliJ IDEA

那么首次创建的工程怎么提交到代码库呢？🤔

### 6.1 创建本地仓库

<div align="center">
    <img src="https://bugstack.cn/images/roadmap/tutorial/road-map-git-14.png" width="550px">
</div>

- Create Git repository 创建一个本地的暂存库。你可以把开发的内容暂时提交到本地仓库中。

### 6.3 提交本地代码

<div align="center">
    <img src="https://bugstack.cn/images/roadmap/tutorial/road-map-git-15.png" width="550px">
</div>

- 把本地仓库提交到本地代码库待提交列表中。
- 后续你在创建的代码，会默认自动加入进来。*如果你是通过打开文件夹复制进去的，不会被添加，需要手动 +Add*
- 添加后就可以参考 5.3 中的操作提交代码了。

### 6.4 创建远程仓库

你可以选择 GitHub/GitCode/Gitee/GitLab 任意地方创建自己的工程库。教程；
- [https://bugstack.cn/md/road-map/github.html](https://bugstack.cn/md/road-map/github.html)
- [https://bugstack.cn/md/road-map/gitcode.html](https://bugstack.cn/md/road-map/gitcode.html)
- [https://bugstack.cn/md/road-map/gitee.html](https://bugstack.cn/md/road-map/gitee.html)

<div align="center">
    <img src="https://bugstack.cn/images/roadmap/tutorial/road-map-git-16.png" width="650px">
</div>

### 6.5 推送本地工程

<div align="center">
    <img src="https://bugstack.cn/images/roadmap/tutorial/road-map-git-17.png" width="650px">
</div>

<div align="center">
    <img src="https://bugstack.cn/images/roadmap/tutorial/road-map-git-18.png" width="650px">
</div>

- 最后推送完成就可以看到自己的代码进入仓库中了！

## 7. 操作界面 - git-gui

Git 附带了用于提交 ( [git-gui](https://git-scm.com/docs/git-gui) ) 和浏览 ( [gitk](https://git-scm.com/docs/gitk) ) 的内置 GUI 工具，但也有一些第三方工具可供用户寻求特定于平台的体验。

<div align="center">
    <img src="https://bugstack.cn/images/roadmap/tutorial/road-map-230705-01.png?raw=true" width="750px">
</div>

- Git 提供了操作的客户端界面，你可以按需下载使用。
- 地址：[https://git-scm.com/docs/git-gui](https://git-scm.com/docs/git-gui)

## 8. 分支命名

不同公司中对Git的使用分支命名规范也略有差异，不过整体都会分为；`上线`、`预发`、`开发`、`测试`，这样几个分支。如图是一种比较简单使用的拉取分支方式。

<div align="center">
    <img src="https://bugstack.cn/images/roadmap/tutorial/road-map-git-24.png" width="850px">
</div>

- master/main 作为主分支，不可直接修改代码代码，只能从分支合并到主分支进行进行提交。同时，master 分支的合并需要进行审批，审批后才能合并。
- 开发前，先从 master 分支，拉一个开发分支。`2024/10/11/xfg-xxx` 使用带有斜线的分支命名会自动创建文件夹，对于多人开发的项目，可以直接归档。
- 后开发，也就是研发已经完成了本地的验证。进行测试时，可以把研发的开发分支合并到 test 分支，提交、部署、测试。遇到测试bug，需要回到可发分支修改代码，之后合并到 test 分支部署验证。
- pre/release 预发分支，用于测试完成后，把研发的开发分支合并到预发分支进行预发上线，上线后测试人员进行验证。最终完成验证后，把开发分支合并到 master 分支，并需要由架构师对合并代码审批通过。最后进行上线开量验证。
- 如果是修复bug的，可以添加一个 `fix-用户名缩写-具体功能`

## 9. 提交规范

保持一个标准的统一的规范提交代码，在后续的评审、检查、合并，都会非常容易处理。

<div align="center">
    <img src="https://bugstack.cn/images/roadmap/tutorial/road-map-git-21.png" width="450px">
</div>

**提交规范**：`type:【需求名】desc #id` 如：`feat:【抽奖算法】O1、Ologn 时间复杂度算法实现 #需求id（github pr/行云等会有自动关联）` *参考Commit message 规范*

```java
# 主要type
feat:     增加新功能
fix:      修复bug

# 特殊type
docs:     只改动了文档相关的内容
style:    不影响代码含义的改动，例如去掉空格、改变缩进、增删分号
build:    构造工具的或者外部依赖的改动，例如webpack，npm
refactor: 代码重构时使用
revert:   执行git revert打印的message

# 暂不使用type
test:     添加测试或者修改现有测试
perf:     提高性能的改动
ci:       与CI（持续集成服务）有关的改动
chore:    不修改src或者test的其余修改，例如构建过程或辅助工具的变动
```

> 前提通知，谨慎回滚。如果是回滚 Master 更要特别小心，别把工作回滚丢了。

## 10. 操作手册

- 文档：[https://git-scm.com/book/zh/v2](https://git-scm.com/book/zh/v2) - `可以直接对照着操作，练习命令`
- PDF：[https://github.com/progit/progit2-zh/releases/download/2.1.62/progit.pdf](https://github.com/progit/progit2-zh/releases/download/2.1.62/progit.pdf)
- 演示：[https://learngitbranching.js.org/](https://learngitbranching.js.org/) - `可直接查看动画效果，引导式学习Git命令操作。`

---

<div align="center">
</div>

- 中文PDF，直接深度学习Git操作！下载：**微信公众号「bugstack虫洞栈」回复「gitbook」**
