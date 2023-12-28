### GIT

1. 查看版本

```bash
git -v
```

2. 配置

   name

~~~bash
git config --global user.name "wp"
~~~

​		email

~~~bash
git config --global user.email "wupeng_paddy@163.com"
~~~

3. 使用git

- 查看当前仓库的状态

```bash
git status 
```

- 初始化仓库

```bash
git init
```

刚刚添加到项目中文件是未跟踪状态

- 未跟踪--> 暂存

```bash
git add <filename> #将文件切换到暂存状态
git add * #将所有已修改(未跟踪)的文件暂存
```

- 暂存 --> 未修改 

```bash
git commit -m "xxxx"  #将暂存的文件存储到仓库中
git commit -a -m "xxxx"  #提交所有已修改的文件(未跟踪的文件不会提交)
```

- 未修改 --> 修改

~~~bash
#修改代码后,文件会变为修改
~~~

4. 常用的命令

   1.重置文件

~~~bash
git restore <filename> # 恢复文件
git restore --staged <filename>  # 取消暂存状态 
~~~

​		2. 删除文件

~~~bash
git rm <filename> #删除文件
git rm <filename> -f #强制删除文件
~~~

​		3. 移动文件

```bash
git mv from to # 移动文件 重命名文件
```

### 分支

git在存储问价时,每一次代码提交,都会创建一个与之对应的节点,git就是通过一个一个节点,记录代码的状态.

节点会构成一个树状结构,树状结构,就意味着树会存在分支.默认情况下只有一个分支,命名为master

在使用git时,可以创建多个分支,分支之间相互独立,在一个分支上修改代码,不会影响其他的分支

```bash
git branch # 查看当前分支
git branch <branch name> # 创建新的分支
git branch -d <branch name> # 删除分支
git switch <branch name> # 切换分支
git switch -c <branch name> # 创建并切换分支

```

在开发中,都是在自己的分支上编写代码,代码编写后,再合并到主分支上

### 变基(rebase)

在开发者中,除了通过merge来合并分之外,话可以通过变基来完成分支的合并

我们通过merge合并分支时,在提交记录中会将所有的分支创建和分支合并的过程全部显示出来,

这样当项目比较复杂的时候,开发过程比较波折时,必须要反复的创建、合并、删除. 这样一来会使得我们代码的提交记录极为混乱

原理(变基时发生了什么):

1. 当发起变基时,git会首先找到两只分支的最近的共同的祖先
2. 对比当前分支相对于祖先的历史提交,并且将它们提取出来存储到一个临时文件中
3. 将当前部分指向目标的基底
4. 以当前基底开始,重新执行历史操作

变基和merge 对于合并分支来说,最终的结果都是一样的,但是变基会使得代码的提交记录更整洁更清晰! 大部分情况下,合并和变基时可以互换的.但是如果分支已经提交给远程仓库了.这时尽量不不要使用变基.

### 远程仓库(remote)

目前我对于git所有操作都是在本地进行的.在开发中显然不能这样的,这时就需要一个远程的git仓库.远程的git仓库和本地的本质上没有什么区别.不同点在于远程仓库可以多人同时访问,方便我们协同开发.在实际开发中,git的服务器通常由公司搭建,内部使用或是购买一些公共的私有git服务器.学习阶段直接使用一些开放的公共git仓库.

目前常用的库:GitHub和Gitee(码云)

将本地库上传到git

```bash
git remote add origin https://github.com/wupengpaddy/git-demo.git
# git add <remote name> 
git branch -M main
# 修改分支的名字为main
git push -u origin main
# git push 将代码上传服务器上
```

将本地仓库上传到gitee

```bash
git remote add gitee https://gitee.com/wupeng_paddy/gitdemo.git
git push -u gitee "main"
```

























