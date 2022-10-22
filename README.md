视频地址：https://www.bilibili.com/video/BV1vy4y1s7k6?p=1&vd_source=ffc935d7e1b5bbef786d8450078dc072


# 第一章 Git概述
git官网https://git-scm.com/  目前最新版本是2.37.1

### 1） 版本控制
Git是分布式版本控制系统，可以记录文件内容变化；最重要的是可以记录文件修改历史，用户能查看历史版本，方便版本切换。
### 2） Git工作机制
工作区：代码存放的磁盘目录
暂存区：工作区的代码添加到暂存区（临时存储，还没有历史版本，可以删掉）
本地库：历史版本生成，版本是改不掉了
示意图：(工作区)-git add ->(暂存区）-git commit -m ''->(本地库)
### 3） git和代码托管中心
代码托管中心是基于网络服务器的远程代码仓库，一般简单称为远程库
局域网：GitLab
互联网：GitHub、Gitee

# 第三章 Git常用命令

命令名称
```			作用
git config --global user.name 	用户名设置用户签名
git config --global user.email 	邮箱设置用户签名
git init			初始化本地库
git status			查看本地库状态
git add 			文件名添加到暂存区
git commit -m "日志信息" 	文件名添加到本地库
git reflog查看历史版本		git reset --hard 版本号版本穿梭
```

### 1）设置用户签名
```
git config --global user.name 用户名
git config --global user.email 邮箱
```
注意 
Git首次安装必须设置用户签名，否则代码无法提交
这里的设置用户签名和将来登录GitHub（或其他代码托管中心）的账号没有有人关系


### 2）版本穿梭
```
git reset --hard 版本号
git reset --soft 版本号
```
git reset中的hard与soft
 git reset --hard的作用是代码强制回溯到某节点，对于当前节点->回溯节点中间已commit的内容就会全部消失，而git reset --soft模式下与hard模式会有所不同，他会保存当前节点->回溯节点之间已保存的内容。
 --hard场景：1.当我们发现提交的某个commit思路不正确，或与业务有很大的出入时，我们此时可以选择使用–hard去回退版本(–hard)。
 --soft场景：1.当我们不小心把还没有添加完毕的功能commit提交上去时，这个时候我们可以使用–soft去回退我们误提交的commit，完成此功能后，在重新提交commit。
https://blog.csdn.net/liu19721018/article/details/124123527

# 第四章 Git分支操作
### 1）什么是分支，分支的好处略。
### 2）分支的操作
命令名称作用git branch 分支名创建分支git branch -v 查看分支git checkout 分支名切换分支git merge 分支名把指定的分支合并到当前的分支上
### 3) 合并分支产生冲突
 - 表现：后面状态为MERGING
 - 冲突产生原因：合并分支时，两个分支在同一个文件的同一个位置有两套完全不同的修改，Git无法替我们决定使用哪一个。必须人为决定新代码的内容。
 - 处理冲突：打开文件，决定>>>>和<<<<中间用什么内容
 - 处理冲突后，需要重新添加文件到暂存区+重新提交（注意：此时git commit 命令不能带文件名）
#### 原理：分支名（如master，hot-fix）其实都是指向具体版本记录的指针，当前所在的分支，其实是由HEAD决定的，所以创建分支的本质其实是多创建一个指针。切换分支的本质就是移动HEAD指针。

# 第五章 Git团队协作机制
### 5.1 团队内协作
```
1）git push 把代码从本地库推送到代码托管中心的远程库 ，协作者push时需要获得权限
2）git clone 把代码从远程库克隆到本地库
3）git pull 把远程库中的代码拉取到本地库，并更新本地库代码 
### 5.2 跨团队协作
1）fork A fork is a copy of a repository. Forking a repository allows you to freely experiment with changes without affecting the original project.
2）pull request 把代码从其他远程库拉到自己的远程库，需要审核和merge

# 第六章 GitHub操作
远程仓库操作
命令名称作用
```
git remote -v		查看当前所有远程地址别名
git remote add 别名 	远程地址起别名
git push 别名 		分支推送本地分支上的内容到远程仓库
git clone 远程地址 	将远程仓库的内容克隆到本地
git pull 远程库地址别名	远程分支将远程仓库对于分支最新内容拉下来后与当前本地分支直接合并
```
