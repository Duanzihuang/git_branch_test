# git_branch_test

Git基本操作及Git分支演练

## Git的基本操作

```javascript
1、从远程仓库克隆到本地
 git clone 远程仓库地址

2、更改本地代码之后提交相关操作
 git status 查看本地仓库的状态

 git add . 把更改的添加到暂存区

 git commit -m "注释" 提交到本地仓库
    
3、回滚
 git reset --hard HEAD 回滚最近的一个版本
    
 git reset --hard 版本号 回滚到指定的版本

4、把本地的代码推送到服务器
 git push origin master -u xxx
    
5、将本地仓库和远程仓库建立关联关系
 git remote add origin git@gitee.com:manageritcast/pyg_middleware_27.git

6、推送到远程，并且建立跟踪分支
 git push -u origin master
```

## git本地仓库添加到远程仓库

> 前提：在本地通过 git init 创建好了本地仓库，在远程也建立了远程仓库

```
1、切换到要上传的项目的根目录【下面有.git文件】

2、将远程仓库与本地仓库关联
 git remote add origin git@github.com:Duanzihuang/react_redux_cart.git

3、将项目添加到本地仓库
 git add .

4、提交到本地仓库
 git commit -m "1-完成了受控组件Checkbox案例"
	
5、第一次推送【记得加上-u】
# 由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。
 git push -u origin master
	
6、如果发生错误 说明 本地仓库和远程仓库的文件有冲突，你先pull远端的版本，解决了冲突才能push
 git pull origin master / git pull origin master --allow-unrelated-histories
 git push -u origin master
 
7、建议在Github等网站新建仓库的时候，不要勾选README和.gitignore选项，统一由本地生成，这样在建立关联关系的时候就不会有冲突了
```

## 有关分支

1. 当我们创建一个远程仓库的时候，就会默认有一个主分支【创建仓库就会自带的】
2. 我们把远程仓库，克隆到本地之后，本地也有一个master分支【通过git branch查看】
3. 主分支【master】主要用于我们主线代码的开发
4. 新建分支的目的是为了，保证我们主分支继续执行的情况下，做一些其它的事情【比如bug修复或是难题攻克】


## Git分支操作
```javascript
1、查看本地有哪些分支
 git branch
    
2、切出一个新分支
 git checkout -b v1.0_bugfix_branch
    
3、把新分支推动远程仓库，做一个备份
 git push origin v1.0_bugfix_branch
    
4、切回主分支，并且把 v1.0_bugfix_branch 已经修复的代码合并会主分支
 git checkout master
 git merge v1.0_bugfix_branch
    
 做完这一步，本地的master已经拥有修改之后的代码
    
5、把本地的master的代码推送远程仓库的master
 git push origin master
```

##Git分支的其它指令

```
1、查看远程仓库信息
 git remote
 
2、查看远程仓库的版本及地址
 git remote -v
 
3、查看远程仓库的基本信息
 git remote show origin
 
4、查看本地分支
 git branch
 
5、查看所有分支【包含远程分支】
 git branch -a
```

## Git冲突处理

1. 多人在同一时间操作同一个文件的时候有冲突
2. 如果多个人要更改同一文件，最好的方式是分时间处理，比如某一个人先提交，然后另外一个人pull下来再改
3. 万一真的出现了冲突，我们先要把自己的代码备份，回退到某一个没有冲突的版本，再把代码拷贝上去，最后在由一个人去提交