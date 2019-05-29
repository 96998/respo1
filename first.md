# Git入门的基础知识

## 参考书

```
https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-Git-%E5%9F%BA%E7%A1%80
```



## 软件的安装

```
https://tortoisegit.org/
https://git-scm.com/
```



## 基础概念介绍

```
add是加入暂存区
commit是提交到本地仓库

```



```
git init
```



## 连接github

### SSH连接

```
ssh-keygen -t rsa
github->setting->SSH and GPG keys
TortoisrGit的网络中选择Git/usr/bin/ssh.exe
git->远端->Putty密中加入私钥
```





## git的三种状态

```
好，请注意。 如果你希望后面的学习更顺利，记住下面这些关于 Git 的概念。 Git 有三种状态，你的文件可能处于其中之一：已提交（committed）、已修改（modified）和已暂存（staged）。 已提交表示数据已经安全的保存在本地数据库中。 已修改表示修改了文件，但还没保存到数据库中。 已暂存表示对一个已修改文件的当前版本做了标记，使之包含在下次提交的快照中。
```



## Linunx使用git

```
  $ tar -zxf git-2.0.0.tar.gz
  $ cd git-2.0.0
  $ make configure
  $ ./configure --prefix=/usr
  $ make all doc info
  $ sudo make install install-doc install-html install-info
  
  
  更新git
   $ git clone git://git.kernel.org/pub/scm/git/git.git
```

