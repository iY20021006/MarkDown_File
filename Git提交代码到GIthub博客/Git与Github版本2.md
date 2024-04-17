# Git与Github版本2
> 这篇文章主要讲解如何使用git提交代码到github，比较适合新手学习的文章。


## 下载Git
***[Git官网](https://git-scm.com/download/win)***\
安装无脑下一步即可\
下载安装Git之后，在(win11打开显示更多选项)桌面鼠标右击会出现`Open Git Bash hele`
如下图所示

<img src="C:\Users\iY\AppData\Roaming\Typora\typora-user-images\image-20240417193600450.png" alt="image-20240417193600450" style="zoom: 67%;" />

## 进行Git配置环境
我们下载Git之后是需要进行配置的，接下里就一起来配置。

### 配置Git

在你的电脑上，创建个文件夹，这个文件夹存放的文件是用来待会提交到github，当然空文件也可以。\
打开刚刚创建好的文件夹，右击鼠标点击`Open Git Bash hele`，会出现下图界面，按ctrl+滑动滚轮可以放大字体。



#### 1、初始化文件夹 
输入这条指令
<kbd>git init</kbd>\
这条指令初始化我们的文件夹


![image-20240417193612364](C:\Users\iY\AppData\Roaming\Typora\typora-user-images\image-20240417193612364.png)

会在文件夹中添加这个文件夹
![image-20240417193616772](C:\Users\iY\AppData\Roaming\Typora\typora-user-images\image-20240417193616772.png)

此时提示我们已经初始化成功。

#### 2、配置邮箱和名字
  如果打开不了github网站,可以下载这个软件进行加速：
[watt Toolkit](https://steampp.net/)
- 输入以下命令配置邮箱。注意:把`"github邮箱"`替换你的github的邮箱\
<kbd>git config --global user.email "github邮箱"</kbd>

- 输入以下命令配置名字。注意:把`"github账户名"`替换你的github的账户名\
<kbd>git config --global user.name "github账户名"</kbd>

#### 3、配置ssh密钥

- 输入以下命令配置<kbd>shh</kbd>公钥,输入命令会有提示，一直按确认键就行\
<kbd>ssh-keygen -t rsa</kbd>\
如下图所示

![image-20240417193623270](C:\Users\iY\AppData\Roaming\Typora\typora-user-images\image-20240417193623270.png)

输入以下命令获取<kbd>ssh</kbd>公钥,把这段ssh复制到github中配置\
<kbd>cat ~/.ssh/id_rsa.pub</kbd>
如下图所示\

![image-20240417193629263](C:\Users\iY\AppData\Roaming\Typora\typora-user-images\image-20240417193629263.png)

### github创建仓库

打开github网站，点击右上角的加号旁边的小箭头
![image-20240417193633973](C:\Users\iY\AppData\Roaming\Typora\typora-user-images\image-20240417193633973.png)

点击`New repository`创建仓库

![image-20240417193637043](C:\Users\iY\AppData\Roaming\Typora\typora-user-images\image-20240417193637043.png)

给库起名字和描述库的用途

![image-20240417193641602](C:\Users\iY\AppData\Roaming\Typora\typora-user-images\image-20240417193641602.png)

点击`Create repository`完成创建

![image-20240417193647607](C:\Users\iY\AppData\Roaming\Typora\typora-user-images\image-20240417193647607.png)

选择`ssh`，复制该公钥

![image-20240417193652276](C:\Users\iY\AppData\Roaming\Typora\typora-user-images\image-20240417193652276.png)

### 添加远程仓库

回到`Open Git Bash hele`中，输入以下命令\
<kbd>git remote add <远端名称> <仓库路径></kbd>\
  - 远端名称 ，默认是<kbd>origin</kbd> ,取决于远端服务器设置\
  - 仓库路径，从远端服务器获取URL\
  - 查看仓库<kbd>git remote</kbd>\

![image-20240417193710591](C:\Users\iY\AppData\Roaming\Typora\typora-user-images\image-20240417193710591.png)

### 修改端口
如果我们没有修改端口，后面提交文件时会报错无法进行链接，所以修改端口必要的。

输入以下命令打开配置文件\
不会vim编辑器的，请注意操作步骤

1. 输入以下命令\
<kbd>vim ~/.ssh/config</kbd>
2. 在键盘点击<kbd>i</kbd>，vim会进入编辑模式
3. 把以下复制到<kbd>config</kbd>文件中
> Host github.com\
> Hostname ssh.github.com\
> Port 443
4. 按esc键退出编辑模式,在底部输入冒号(:) 后在输入wq，按确认键退出vim。

###　提交文件到远程仓库

把文件夹中的文件添加到远程仓库

1.  使用命令<kbd>git　add . </kbd>\
该命令是将文件夹中新文件和修改的文件添加到暂存区

![image-20240417193716510](C:\Users\iY\AppData\Roaming\Typora\typora-user-images\image-20240417193716510.png)


2. 使用命令<kbd>git commit </kbd>\
   ![image-20240417193720222](C:\Users\iY\AppData\Roaming\Typora\typora-user-images\image-20240417193720222.png)


3. 使用命令<kbd>git push origin master</kbd>
该命令将新文件和修改的文件推送到远程仓库

![image-20240417193723398](C:\Users\iY\AppData\Roaming\Typora\typora-user-images\image-20240417193723398.png)