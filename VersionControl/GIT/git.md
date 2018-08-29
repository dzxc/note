# git
### git 简介
git是一款开源的分布式版本控制工具
在世界上所有的分布式版本控制工具中，git是最快、最简单、最流行的

##### git的起源
作者是Linux之父：Linus Benedict Torvalds
当初开发git仅仅是为了辅助Linux内核的开发（管理源代码）

##### git的现状
在国外已经非常普及，国内并未普及（在慢慢普及）
越来越多的开源项目已经转移到git


##### 其他版本控制工具
CVS
最早的开源、免费的集中式版本控制工具
自身设计有问题，会造成提交文件不完整，版本库莫名其妙损坏的情况

SVN
修正了CVS的一些稳定性问题，是目前用得最多的集中式版本库控制工具

ClearCase
收费的集中式版本控制工具，安装比Windows还大，运行比蜗牛还慢
能用ClearCase的一般是世界500强，他们有个共同的特点是财大气粗或者人傻钱多

VSS
微软的集中式版本控制工具，集成在Visual Studio中


### git和SVN的简单对比

速度
在很多情况下，git的速度远远比SVN快

结构
SVN是集中式管理，git是分布式管理

其他
SVN使用分支比较笨拙，git可以轻松拥有无限个分支
SVN必须联网才能正常工作，git支持本地版本控制工作
旧版本的SVN会在每一个目录置放一个.svn，git只会在根目录拥有一个.git


### git的工作流程
![](/VersionControl/GIT/images/1.png)
![](/VersionControl/GIT/images/2.png)
分布式和集中式的最大区别在于：在分布式下
开发者可以本地提交
每个开发者机器上都有一个服务器的数据库
拥有一个本地的代码仓库


##### 使用git

跟SVN一样，你可以通过命令行敲指令或者图形界面客户端使用git

在Mac上，比较好用的git图形界面客户端有
SourceTree
下载地址：http://www.sourcetreeapp.com/download/

GitHub
下载地址：https://mac.github.com
不过它是专门为GitHub网站而设计的


## git常用指令
git help ：git指令帮助手册
查看其他指令的做法：git help 其他指令

git config ：git的配置信息相关（修改的是.git/config文件）
配置用户名：git config “user.name” 用户名（用于跟踪修改记录）
配置邮箱：git config “user.email” 邮箱（用于多人开发间的沟通）
查看配置信息：git config –l
编辑配置信息：git config –e（用vim编辑，:wq是退出vim编辑器）
设置指令的别名：git config alias.别名 原指令名称
设置带参数指令的别名：git config alias.别名 “原指令名称 参数”
将此设置应用到整个系统中：git config ––gloabal

git status ：查文件的状态
查看某个文件的状态：git status 文件名
查看当前路径所有文件的状态：git status

git log ：查看文件的修改日志
查看某个文件的修改日志：git log 文件名
查看当前路径所有文件的修改日志：git log
用一行的方式查看简单的日志信息：git log ––pretty=oneline
查看最近的N次修改：git log –N（N是一个整数）

git diff ：查看文件最新改动的地方
查看某个文件的最新改动的地方：git diff 文件名
查看当前路径所有文件最新改动的地方：git diff


git init ：初始化一个空的本地仓库，生成一个.git目录，用于维护版本信息
在当前路径初始化仓库：git init
在其他路径初始化仓库：git init 仓库路径

git add ：将工作区的文件保存到暂缓区
保存某个文件到暂缓区：git add 文件名
保存当前路径的所有文件到暂缓区：git add .（注意，最后是一个点 . ）

git commit ：将暂缓区的文件提交到当前分支
提交某个文件到分支：git commit -m ”注释” 文件名
保存当前路径的所有文件到分支：git commit -m ”注释”

git reset ：版本回退（建议加上––hard参数，git支持无限次后悔）
回退到上一个版本：git reset ––hard HEAD^
回退到上上一个版本：git reset ––hard HEAD^^
回退到上N个版本：git reset ––hard HEAD~N（N是一个整数）
回退到任意一个版本：git reset ––hard 版本号（版本号用7位即可）

git reflog ：查看指令使用记录（能够查看所有的版本号）

git rm：删除文件（删完之后要进行commit操作，才能同步到版本库）

git clone：下载远程仓库到本地
下载远程仓库到当前路径：git clone 仓库的URL
下载远程仓库到特定路径：git clone 仓库的URL 存放仓库的路径

git pull：下载远程仓库的最新信息到本地仓库

git push：将本地的仓库信息推送到远程仓库

## 工作原理
如果想了解git的工作原理，有几个核心概念必须知道
工作区（Working Directory）：仓库文件夹里除.git目录以外的内容

版本库（Repository）：.git目录，用于存储记录版本信息
暂缓区（stage）
分支（master）：git自动创建的第一个分支
HEAD指针：用于指向当前分支

git add和git commit的原理
git add ：把文件修改添加到暂存区
git commit ：把暂存区的所有内容提交到当前分支


## 远程仓库
如果是多人团队开发，最好还是搭建一个远程仓库

搭建远程仓库的途径
自己搭建一个git服务器：费时费力
在GitHub上托管项目：公开项目免费、私有项目收费，很多第三方开源项目
在oschina上托管项目：完全免费，在国内访问速度快（推荐使用）
