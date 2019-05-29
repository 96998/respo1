## Linux下编译安装

```
 $ tar -zxf git-2.0.0.tar.gz
  $ cd git-2.0.0
  $ make configure
  $ ./configure --prefix=/usr
  $ make all doc info
  $ sudo make install install-doc install-html install-info
```

### git的升级

```
$ git clone git://git.kernel.org/pub/scm/git/git.git
```





## 运行git前的配置



### 用户信息

```
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.comS
```

### 文本编辑器

```
$ git config --global core.editor emacs
```

### 检查配置信息

```
git config --list
```

### 删除自定义标签

```
git config --unset usr.name

```







## 获取帮助

```
$ git help <verb>
$ git <verb> --help
$ man git-<verb>
$ git help config
```









## Git基础,获取Git仓库

```
$ git init
$ git add *.c
$ git add LICENSE
$ git commit -m 'initial project version'
$ git clone https://github.com/libgit2/libgit2 mylibgit			//克隆到本地的mylibgit中
```

