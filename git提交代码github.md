# git提交代码github

1. <kbd>git init </kbd>  初始化仓库

2. 添加用户邮箱和名字

   - `git config --global user.email "2650635161@qq.com"`
   - ` git config --global user.name "iY20021006"`

3. 配置ssh密钥

   1. <kbd>ssh-keygen -t rsa</kbd> 获取ssh公钥
   2. <kbd>cat ~/.ssh/id_rsa.pub</kbd>>查看密钥
   3. 到<kbd>github</kbd>中配置密钥

4. 到<kbd>github</kbd>中创建仓库，获取<kbd>ssh</kbd> 地址

5. 添加远程仓库

   此操作是先初始化本地仓库，然后与已经创建的远程仓库进行对接。

   - 命令：<kbd>git remote add <远端名称> <仓库路径> </kbd>
     - 远端名称 ，默认是<kbd>origin</kbd> ,取决于远端服务器设置
     - 仓库路径，从远端服务器获取URL
     - 查看仓库<kbd>git remote</kbd>

6. 修改端口

   1. `vim ~/.ssh/config`

   2. 在<kbd>config</kbd>添加

      > Host github.com
      >   Hostname ssh.github.com
      >   Port 443

 7. 添加文件到<kbd>github</kbd>仓库

    	1. <kbd>git add .</kbd>将所有修改的文件添加暂存区
    	2. <kbd>git commit </kbd>添加文件修改注释
    	3. <kbd>git push origin master</kbd>推送到仓库<kbd>master</kbd>分支

    