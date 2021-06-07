## git的学习

- 工作区（写代码）-git commit-暂存区（临时存储）-git add-本地库（历史版本）

- git status 查看状态

- vim good.txt   创建good文件，进入编辑

- rm +文件名    删除文件

- mkdir weChat    创建wechat文件夹

- gti log //git reflog   查看历史记录

- git reset --hard 4c73f66 （索引值） 通过索引值回到另外的版本号。

- ​     (HEAD -> master) HEAD@{0}      //移动到当前版本需要的步数

- cat +文件名    查看文件内容

  

##            git分支

分支：在版本控制过程中，使用多条线同时推进多个任务

 git branch -v     查看分支版本号

 git branch +自己起的分支名，创建分支

git checkout  分支名，选择该分支

#### 合并分支：

1、切换到接受修改的分支（被合并，增加新内容）

git  checkout  [分支名]

2、执行merge命令

git merge [要合并的分支名]

## 哈希算法

## git工作流

1、集中式工作流

以中央仓库作为项目所有修改的单点实体，所有的修改都提交到

master上面。

2、gitflow工作流

gitflow工作流为功能开发，发布准备和设备维护设立了独立的分支，让发布迭代的过程更加流畅，严格的分支模型也为大型项目提供了一些非常必要的结构

3、forking工作流

在gitflow的基础上，充分利用了git的fork和pull request 的功能以达到代码审核的目的，更适合安全可靠的管理大团队的开发，而且能接受不信任者的提交。

