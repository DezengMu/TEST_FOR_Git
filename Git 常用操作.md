# Git 常用操作

## 1. 分支与合并

### 1.1 git merge

![1638010446957](C:\Users\dezengmu\AppData\Roaming\Typora\typora-user-images\1638010446957.png)

### 1.2 git rebase

![1638011078398](C:\Users\dezengmu\AppData\Roaming\Typora\typora-user-images\1638011078398.png)



## 2 撤销变更

### 2.1 git reset

`git reset HEAD~<num>`,可以将**本地分支**回退到上一个提交记录；**但是只对本地提交记录有效，对远程分支无效**

![1638012703693](C:\Users\dezengmu\AppData\Roaming\Typora\typora-user-images\1638012703693.png)

### 2.2 git revert

![1638012862820](C:\Users\dezengmu\AppData\Roaming\Typora\typora-user-images\1638012862820.png)

`git revert HEAD`,其实只是在本地把之前的一次提交，重新提交了一次，正如上图中所说，c2'其实就是c1的副本，而且之后还需要push 到远程仓库的

### 注意：

* git reset 和 git  revert 的参数并不一样，如果想回到上一个提交记录，需要使用以下其中一个命令：
  * `git reset HEAD~1`
  * `git revert HEAD`

## 3. 复制及修改分支顺序

![1638012037397](C:\Users\dezengmu\AppData\Roaming\Typora\typora-user-images\1638012037397.png)

### 3.1 git cherry-pick

1. `git cherry-pick <提交号>`

   **将一些提交号==复制==到当前位置（HEAD)下面**

2. `git rebase -i  HEAD~num`

   **将当前位置之前的一些提交号==修改其顺序==，并且可以==删除某些提交**==



