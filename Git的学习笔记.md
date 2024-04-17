# Git的学习笔记

<img src="C:\Users\iY\AppData\Roaming\Typora\typora-user-images\image-20240323224255193.png" alt="image-20240323224255193" style="zoom: 50%;" />

## 一、实际场景

1. 备份

2. 代码还原
3. 协同开发
4. 追溯问题代码人和编写时间

## 二、版本控制器的方式

1. 集中式版本控制工具

> 集中式版本控制工具，版本库集中放在中央服务器。每个人工作时从中央服务器下载代码，工作时必须联网，局域网和互联网，结束工作时提交到中央版本库。举例**SVN**  或  **CVS**。

2. 分布式版本控制工具	 

> 分布式版本控制工具没有 “中央服务器 ”，无需联网，因为每个人的电脑就是一个完整的版本库。多人协作只需各自推送给对方。举例**Git**

### 1、优势

1. 速度快
2. 简单的设计
3. 对非线性开发模式的强力支持
4. 完全分布式
5. 高效管理超大的规模项目

## 三、Git工作流程图

![](E:\图片\u=3754743631,1950876194&fm=253&fmt=auto&app=138&f=PNG.webp)

```
1. clone（克隆）: 从远程仓库中克隆代码到本地仓库

2. checkout （检出）:从本地仓库中检出一个仓库分支然后进行修订

3. add（添加）: 在提交前先将代码提交到暂存区

4. commit（提交）: 提交到本地仓库。本地仓库中保存修改的各个历史版本

5. fetch (抓取) ： 从远程库，抓取到本地仓库，不进行任何的合并动作，一般操作比较少。

6. pull (拉取) ： 从远程库拉到本地库，自动进行合并(merge)，然后放到到工作区，相当于fetch+merge

7. push（推送） : 修改完成后，需要和团队成员共享代码时，将代码推送到远程仓库
```

### 3.1配置用户名和邮箱

打开 Git Bash Here 命令行输入两行带代码。

`$ git config --global user.name " 你的用户名"`

`$ git config --global user.email " 你的邮箱"`

## 四、基本操作指令

---

![image-20240322230522779](C:\Users\iY\AppData\Roaming\Typora\typora-user-images\image-20240322230522779.png)

---

### 4.1. 查看修改的状态（status）

- 作用：查看修改的状态
- 命令形式：`git status`

### 4.2. 添加工作区到暂存区（add）

- 作用：将工作区中的新文件或者修改的文件添加到暂存区中。
- 命令形式：`git add 文件名1 文件名2|通配符`
  - 将所有当前目录文件添加到暂存区`git add .`

### 4.3. 提交暂存区到本地仓库（commit）

- 作用：提交暂存区内容到本地仓库的当前分支
- 命令形式：`git commit -m "注释内容"`

### 4.4. 查看提交日记（log）

- 作用：查看提交日记
- 命令形式：`git log [options]`
  - options
    - --all 显示所有分支
    - --pretty=oneline 将提交信息显示为一行
    - --abbrev-commit 使得输出的commit id更简便
    - --graph 以图的形式显示

### 4.5. 版本回退

- 作用：版本切换
- 命令形式：`git reset --hard commitID`
  - commitID 可以使用 `git log `查看

- 如何查看已经删除的记录
  - `git refolg`

### 4.6.添加文件至忽略列表

开始前

![image-20240323000836192](C:\Users\iY\AppData\Roaming\Typora\typora-user-images\image-20240323000836192.png)

- 作用：忽略的文件不会提交到暂存区

- 创建一个文件 `.gitignnore`文件，把需要忽略的文件的后缀名添加到 `.gitignore`中

例子：

​	创建 `.gitignnore`文件

- 命令：`touch .gitignore`

<img src="C:\Users\iY\AppData\Roaming\Typora\typora-user-images\image-20240322235910580.png" alt="image-20240322235910580" style="zoom: 50%;" />	

将需要忽略的文件的后缀名添加到`.gitignnore`文件中

<img src="C:\Users\iY\AppData\Roaming\Typora\typora-user-images\image-20240323000109590.png" alt="image-20240323000109590" style="zoom: 50%;" />	

注意：进入vi编辑器后要按键盘上的（i）切换至==文件模式==，将忽略的文件的后缀名写进去，需要在后缀名前加==*==号，按==ESC==退出文本模式，进入末行模式输入==:wq==保存退出即可。

<img src="C:\Users\iY\AppData\Roaming\Typora\typora-user-images\image-20240323000451231.png" alt="image-20240323000451231" style="zoom: 50%;" />	

<img src="C:\Users\iY\AppData\Roaming\Typora\typora-user-images\image-20240323000637294.png" alt="image-20240323000637294" style="zoom:50%;" />



最后使用以下命令可查看状态

- 命令：`git status`

完成后

![image-20240323000754312](C:\Users\iY\AppData\Roaming\Typora\typora-user-images\image-20240323000754312.png)

## 五、分支

> 几乎所有的版本控制系统都以某种形式支持分支，可以把工作从开发主线上分支出来进行重大的BUG的修改，开发新功能，以免影响开发主线。

### 5.1. 查看分支

- 作用：查看分支
- 命令形式：`git branch`

### 5.2.创建分支

- 作用：创建分支
- 命令形式：`git bransh 分支名`

### 5.3. 切换分支

- 作用：切换分支
- 命令形式：`git checkout 分支名`
  - 创建并切换命令：`git checkout -b 分支名`

### 5.4. 合并分支

- 作用：合并分支（可以是多个分支）
- 命令形式：`git merge 分支名`

### 5.5. 删除分支

**不能删除当前分支，只能删除其他分支**

- 作用：删除分支
- 命令形式：`git branch -d 分支名` 删除分支时，做各种检查
  - `git branch -D 分支名`强制删除分支，不做检查

### 5.6. 解决冲突

文件发生冲突时，手动解决冲突。

1. 处理文件冲突的地方
2. 将解决冲突的文件加入到暂存区
3. 提交到仓库（commit）

### 5.7 配置SSH

在<kbd>Git Bash Here</kbd>输入 `ssh-keygen -t rsa ` 获取ssh公钥，再输入 `cat ~/.ssh/id_rsa.pub`查看配置的ssh公钥，复制到<kbd>gitee</kbd>或者<kbd>github</kbd>配置即可。

---

## 六、操作远程仓库

### 6.1. 添加远程仓库

**此操作是先初始化本地仓库，然后与已经创建的远程仓库进行对接。**

- 命令：`git remote add <远端名称> <仓库路径>`
  - 远端名称 ，默认是<kbd>origin</kbd> ,取决于远端服务器设置
  - 仓库路径，从远端服务器获取URL

### 6.2.查看远程仓库

- 命令：`git remote`

### 6.3 推送远程仓库

- 命令：`git push [-f] [--set-upstream] [远端名称 [本地分支名] [:远端分支名]] 
  - 如果远程分支名和本地分支名称相同，则只写本地名称
    - 命令：`git push origin master`
  - 推送远端的同时并建立和远端分支的关联关系
    - 命令：`git push  --set-upstream origin master`
  - 如果当前分支已经和远端分支失联。可以省略分支名和元端名
    - 命令：`git push` 将master分支推送到已关联的元端分支

### 6.4.查看本地分支与远程分支关联关系	

- 命令：`git branch -vv `

### 6.5.克隆远程仓库

- 命令：git clone <仓库路径> [本地目录]
  - 本地目录可以省略，会自动生成一个目录

### 6.6.从远程仓库抓取和拉取

远程分支和本地分支一样，可以进行 `merge`操作，只需要把远程仓库里的更新文件下载到本地。

- 抓取命令：`git fetch [remote name] [branch name]`
  - 抓取就是将远程仓库更新的文件都抓取到本地，不会进行合并
- 拉取命令：`git pull [remote name] [branch name]` 
  - ​	拉取就是远端仓库的修改拉到本地自动进行合并，等同于 `fetch +merge `
  - 如果不指定远端名称和分支名，则会抓取所有更新当前分支。

<img src="C:\Users\iY\AppData\Roaming\Typora\typora-user-images\image-20240323191726156.png" alt="image-20240323191726156" style="zoom:33%;" />	