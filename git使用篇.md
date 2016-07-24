### **Git Windows使用篇**

#### **<font color=red>Git 介绍</font>**

Git是一个分布式的版本控制系统，最初由Linus Torvalds编写，用作Linux内核代码的管理。在推出后，Git在其它项目中也取得了很大成功，尤其是在Ruby社区中。目前，包括Rubinius、Merb和Bitcoin在内的很多知名项目都使用了Git。Git同样可以被诸如Capistrano和Vlad the Deployer这样的部署工具所使用。

#### **<font color=red>Github、Bitbucket介绍</font>**
Github和Bitbucket均为使用了Git的版本控制系统的代码托管系统.

GitHub允许你免费创建不限数量的“公开”代码仓库，虽有总的资源限额，但一般情况下够用。如果不想公开代码，或者你的代码占用存储空间比较多，你也可以选择成为付费的会员。

Atlassian的Bitbucket，是GitHub的竞争对手。与GitHub稍有不同，Bitbucket允许你免费创建任意数量的“私有“代码仓库，只有当你要为这些私有代码仓库添加5个以上的开发成员时，才需要额外付费，所以说，如果你的（商业）团队人数少于5人，不考虑与开源社区代码共享的问题，Bitbucket可能是更好的选项。

在GitHub，想要接触高水平的软件项目，了解最前沿的技术趋势，和上微博一样简单。

Linux Tovalds也曾经提到过,程序员提升最快的方式就要遵循RTFSC原则(Read the fucking source code).即,程序员想要快速提升自己,就要多上github,多读代码,多写代码.

在国内还有很多别的代码托管系统,例如开源中国、svn999等,本文以github为例示范git的使用.

#### **<font color=red>Github安装篇</font>**

- Mac用户,git系统默认自带.Mac用户可以跳过安装篇.

- Linux用户,安装好apt-get后,在shell中执行下列代码

```
sudo apt-get install git
```

安装完成后,使用下列代码检测git是否安装,正确安装后会显示git的版本号.

```
git --version
```

- window用户
windows用户需要安装客户段,下载地址如下

[Github for Windows下载](https://github-windows.s3.amazonaws.com/GitHubSetup.exe)

安装完成后,打开github客户端,登录在github上创建的账号,登录完成后就可以使用github了.

![login](http://7xwp5w.com1.z0.glb.clouddn.com/image%E7%99%BB%E5%BD%95.png)

#### **<font color=red>代码仓库介绍</font>**

为了使用git版本控制系统,你必须要有一个存储数据的代码仓库(git repository).代码仓库里面可以放任意的文件,
可以是项目的源代码、图片、markdown格式的文档、你甚至可以存放视频.不过存储文件过大的话,使用git提交到你的远程仓库时候就会非常的耗时.

#### **<font color=red>git shell</font>**
github windows客户端安装完成后,默认会安装一个git shell,可以通过git shell完成原本需要操作图形界面完成的操作,比如检出仓库、提交代码、回溯代码等等.(Mac 下bash已经集成了,所以不要再使用windows了😄,Mac、linux真的比windows方便很多)

#### **<font color=red>本地仓库</font>**

本地仓库即为使用git进行版本控制的本地代码仓库,进行一些额外的设置后就可以把本地仓库上传到你的远程仓库

##### **<font color=red>本地仓库的创建</font>**

打开开始菜单栏中git shell,切换到需要进行版本控制的项目目录(cd命令),执行下列命令,即可完成本地仓库的创建

```
git init 
```
可能会有这样的输出

![console output](http://7xwp5w.com1.z0.glb.clouddn.com/image%E4%B8%8D%E6%AD%A3%E5%B8%B8%E8%BE%93%E5%87%BA.png)

这是在提示你,你的git shell字体可能不支持Unicode,如果命令行有异常输出的话,尝试更换TrueType类型的字体.图片中,确实有一些不明含义的乱码.更换字体就不在这里单独在讲了.到这里就可以对本地仓库进行版本控制了.

#### **<font color=red>常用操作</font>**

###### **1.提交所有更改**

```
git add .
git commit -a -m "initial commit"
```

git add . 是添加本地仓库内所有未保存的更改(新创建的文件,改动的文件,删除的文件等等)

git commit 是进行提交 -m参数后面跟的是提交信息,方便以后回溯版本.

写代码过程中,常常需要添加功能,这里就要对提交粒度进行控制,方便我们在发生一些难以恢复的错误操作时候可以找到所有的代码版本,不至于发生错误之前的功能白做.提交粒度要保证原子性,每完成一个小功能,就在本地进行一次提交.

###### **2. 新建本地分支**
在本地新建dev分支

```
git branch dev 
```

##### **3.切换分支**
切换到刚才创建的dev分支

```
git checkout dev
```

##### **4.合并分支**
将master分支与当前分支进行合并

```
git merge master
```

##### **5.clone 远程分支的代码**

```
git clone https://github.com/kyo7701/testRespository (远程分支地址:(示例))
```

##### **6.设置本地分支的远程仓库地址**

```
git remote add origin https://github.com/kyo7701/testRespository
```
需要在github web端新建一个代码仓库.

##### **7.提交到远程分支**

```
git push -u origin master
```
这里是初次提交，所以需要添加 -u参数,－u为--set-upstream,即为上游分支地址,每次代码推向的远程仓库地址.

origin 是远程源,即在第6步中设置的远程仓库地址

master是要推送的远程仓库的分支,如果远程仓库没有将会创建此分支.

进行完初次提交后,以后使用下列代码即可提交到远程

```
git push 
```

此处提交也可以使用github for windows的图形化操作

点击左上角的加号,添加刚才初始化过的本地仓库目录(必须执行本地仓库的创建操作)

![add path](http://7xwp5w.com1.z0.glb.clouddn.com/image%E6%B7%BB%E5%8A%A0%E6%9C%AC%E5%9C%B0%E4%BB%93%E5%BA%93%E7%9B%AE%E5%BD%95.png)

添加完毕后点击右上角的设置,进入respository settings

![仓库设置](http://7xwp5w.com1.z0.glb.clouddn.com/image%E4%BB%93%E5%BA%93%E8%AE%BE%E7%BD%AE.png)

点击remote,设置远程仓库地址

![设置远程仓库地址](http://7xwp5w.com1.z0.glb.clouddn.com/image%E8%AE%BE%E7%BD%AE%E8%BF%9C%E7%A8%8B%E5%88%86%E6%94%AF%E5%9C%B0%E5%9D%80.png)

设置完远程仓库地址后,点击设置图标下面的publish按钮即可将代码推送到远程仓库.

![提交到远程](http://7xwp5w.com1.z0.glb.clouddn.com/image%E6%8F%90%E4%BA%A4%E5%88%B0%E8%BF%9C%E7%A8%8B.png)

到此,git的windows使用篇就结束了,更多git的命令操作请参见[git 常用命令](http://www.cnblogs.com/cspku/articles/Git_cmds.html)

此外,我封装了一些Mac端git操作的常用命令,在shell中输入ca即可完成添加所有更改,并进行提交等等,更多命令请见
[git常用命令封装](https://github.com/kyo7701/tools)


