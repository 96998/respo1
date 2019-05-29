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

$ git config --global core.editor "'C:/Program Files (x86)/Notepad++/notepad++.exe' -multiInst -nosession"


git config core.editor notepad
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





## 记录每次更新到仓库

### 查看当前文件状态

```
git status
```

### 新建README

``` &gt; 
echo 'My Project' > README
```

### 跟踪新文件

```
git add README
```

### 状态简览

```
git status -s



$ git status -s
 M README
MM Rakefile
A  lib/git.rb
M  lib/simplegit.rb
?? LICENSE.txt
新添加的未跟踪文件前面有 ?? 标记，新添加到暂存区中的文件前面有 A 标记，修改过的文件前面有 M 标记。 你可能注意到了 M 有两个可以出现的位置，出现在右边的 M 表示该文件被修改了但是还没放入暂存区，出现在靠左边的 M 表示该文件被修改了并放入了暂存区。 例如，上面的状态报告显示： README 文件在工作区被修改了但是还没有将修改后的文件放入暂存区,lib/simplegit.rb 文件被修改了并将修改后的文件放入了暂存区。 而 Rakefile 在工作区被修改并提交到暂存区后又在工作区中被修改了，所以在暂存区和工作区都有该文件被修改了的记录。
```



### 忽略文件

```
$ cat .gitignore			//创建.gitignore文件
*.[oa]
*~
```

#### 解释

```
第一行告诉 Git 忽略所有以 .o 或 .a 结尾的文件。一般这类对象文件和存档文件都是编译过程中出现的。 第二行告诉 Git 忽略所有以波浪符（~）结尾的文件，许多文本编辑软件（比如 Emacs）都用这样的文件名保存副本。 此外，你可能还需要忽略 log，tmp 或者 pid 目录，以及自动生成的文档等等。 要养成一开始就设置好 .gitignore 文件的习惯，以免将来误提交这类无用的文件。


文件 .gitignore 的格式规范如下：
所有空行或者以 ＃ 开头的行都会被 Git 忽略。
可以使用标准的 glob 模式匹配。
匹配模式可以以（/）开头防止递归。
匹配模式可以以（/）结尾指定目录。
要忽略指定模式以外的文件或目录，可以在模式前加上惊叹号（!）取反。
所谓的 glob 模式是指 shell 所使用的简化了的正则表达式。 星号（*）匹配零个或多个任意字符；[abc] 匹配任何一个列在方括号中的字符（这个例子要么匹配一个 a，要么匹配一个 b，要么匹配一个 c）；问号（?）只匹配一个任意字符；如果在方括号中使用短划线分隔两个字符，表示所有在这两个字符范围内的都可以匹配（比如 [0-9] 表示匹配所有 0 到 9 的数字）。 使用两个星号（*) 表示匹配任意中间目录，比如 a/**/z 可以匹配 a/z , a/b/z 或 a/b/c/z 等。



```



#### 实例

```
# no .a files
*.a

# but do track lib.a, even though you're ignoring .a files above
!lib.a

# only ignore the TODO file in the current directory, not subdir/TODO
/TODO

# ignore all files in the build/ directory
build/

# ignore doc/notes.txt, but not doc/server/arch.txt
doc/*.txt

# ignore all .pdf files in the doc/ directory
doc/**/*.pdf
```

 可参考<https://github.com/github/gitignore>



## 查看变化

```
 git diff --cached 查看已经暂存起来的变化：（--staged 和 --cached 是同义词）
```



## 提交修改

```
$ git commit -m "Story 182: Fix benchmarks for speed"
[master 463dc4f] Story 182: Fix benchmarks for speed
 2 files changed, 2 insertions(+)
 create mode 100644 README
 
 git commit -a -m 'added new benchmarks'
 没有评论还提交不了
```



## 移除文件

```
git rm README			#保留在暂存区这样子就删除不掉
git rm -f README 		#将硬盘上的文件也删除
git rm -cached README	#从暂存区移除但是保留在当前目录



$ git rm --cached README
git rm 命令后面可以列出文件或者目录的名字，也可以使用 glob 模式。 比方说：

$ git rm log/\*.log
注意到星号 * 之前的反斜杠 \， 因为 Git 有它自己的文件模式扩展匹配方式，所以我们不用 shell 来帮忙展开。 此命令删除 log/ 目录下扩展名为 .log 的所有文件。 类似的比如：

$ git rm \*~
该命令为删除以 ~ 结尾的所有文件。
```



## 移动文件

```
$ git mv README.md README
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    renamed:    README.md -> README
其实，运行 git mv 就相当于运行了下面三条命令：

$ mv README.md README
$ git rm README.md
$ git add README
```





## 2.3查看提交历史

[https://git-scm.com/book/zh/v2/Git-%E5%9F%BA%E7%A1%80-%E6%9F%A5%E7%9C%8B%E6%8F%90%E4%BA%A4%E5%8E%86%E5%8F%B2](https://git-scm.com/book/zh/v2/Git-基础-查看提交历史)