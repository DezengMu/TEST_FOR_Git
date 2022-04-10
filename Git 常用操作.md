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
* 如果只是想撤销工作区的文件修改，可以使用如下命令：
  * git checkout --  \<file>
* 如果该文件已经“add"到了暂存区，需要用如下2条命令：
  * git reset  HEAD  \<file>
  * git checkout -- \<file>
* 如果已经“commit " 了，请用如下命令：
  * git reset --hard  \<commit_id>

## 3. 复制及修改分支顺序

![1638012037397](C:\Users\dezengmu\AppData\Roaming\Typora\typora-user-images\1638012037397.png)

### 3.1 git cherry-pick

1. `git cherry-pick <提交号>`

   **将一些提交号==复制==到当前位置（HEAD)下面**

   ![1638066934673](C:\Users\dezengmu\AppData\Roaming\Typora\typora-user-images\1638066934673.png)

   * 说明：git cherry-pick ,是可以一次性将一些提交复制到当前位置下面，但需要注意两点：

     * 只能复制其他分支的，如果复制的是当前分支的一些父节点，会被忽略本次操作
* 你复制的其他分支的提交，都会粘贴在当前位置（HEAD)后面；如果想粘贴在另一个分支下面，需要先checkout 到该分支才可以
     * ![1638081041203](C:\Users\dezengmu\AppData\Roaming\Typora\typora-user-images\1638081041203.png)

### 3.2 `git rebase -i  HEAD~num`

   **将当前位置之前的一些提交号==修改其顺序==，并且可以==删除某些提交==**

* 说明：git rebase -i 命令，后面可以跟分支名或者HEAD ，都可以
  * 个人理解，git rebase 命令，感觉就是对当前分支之前的一些提交记录做一些调整，该删的删，该提前的提前，该修改的修改
  * 适用场景：比如现阶段需要对之前某个古老的版本代码做一些修改，再重新提交，然后再调整回最初的记录，就可以用 git rebase -i 命令
  * rebase 这个命令的作用，到底是什么，可能还需要进一步理解。。。。。。。

## 4 标签



### 4.1git tag

![1638081242125](C:\Users\dezengmu\AppData\Roaming\Typora\typora-user-images\1638081242125.png)

### 4.2 git describe

![1638081612637](C:\Users\dezengmu\AppData\Roaming\Typora\typora-user-images\1638081612637.png)

![1638082013664](C:\Users\dezengmu\AppData\Roaming\Typora\typora-user-images\1638082013664.png)

![1638082030348](C:\Users\dezengmu\AppData\Roaming\Typora\typora-user-images\1638082030348.png)

## 5 多次rebase







## 6 远程仓库操作

### 6.1 git  fetch

![1638093109371](C:\Users\dezengmu\AppData\Roaming\Typora\typora-user-images\1638093109371.png)

![1638093206769](C:\Users\dezengmu\AppData\Roaming\Typora\typora-user-images\1638093206769.png)

* **git fetch 很重要的一点就是，它不会修改你本地的代码，只是把远程仓库里的最新代码下载到本地，在另一个地方放着，但不会跟你的本地代码混在一起，更不会修改你的本地代码**
* 



### 6.2 git pull

![1638093315405](C:\Users\dezengmu\AppData\Roaming\Typora\typora-user-images\1638093315405.png)

* **==git pull  就是git fetch 和 git merge的合体==**



### 6.3 rebase  VS   merge

![1638606760521](C:\Users\dezengmu\AppData\Roaming\Typora\typora-user-images\1638606760521.png)

### 6.4 远程分支跟踪

![1638607512354](C:\Users\dezengmu\AppData\Roaming\Typora\typora-user-images\1638607512354.png)



![1638607541023](C:\Users\dezengmu\AppData\Roaming\Typora\typora-user-images\1638607541023.png)

## 7 其他常用命令

* git diff  和 git diff HEAD -- \<file\>

  * 参考链接：[git diff与git diff HEAD -- file](https://blog.csdn.net/u013485584/article/details/53303858)

    ![1648971179002](C:\Users\dezengmu\AppData\Roaming\Typora\typora-user-images\1648971179002.png)

* 当你在本地修改了文件，然后“add "到了暂存区，但还没有commit ,此时，你又对本地的同一个文件做了修改，然后使用”git restore --staged \<file\> "的命令，会直接丢弃暂存区的修改，而保留最后一次本地的修改结果，换句话说：**本地的修改结果不会被暂存区的修改所覆盖**
* 

