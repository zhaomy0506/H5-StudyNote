# 配置git

配置name和email

```bash
git config --global user.name "用户名"
git config --global user.email "邮箱地址"
```

查看配置

```bash
git config --list
```

配置密钥

```bash
ssh-keygen -t rsa -C "邮箱地址"
```

将配置好的密匙添加到github/gite上

## 使用Git

查看当前仓库状态(重要)

```bash
git status
```

初始化仓库

```bash
git init
```

### 文件状态

在git中文件分为四种状态: 未跟踪(Untracked) -> 暂存(Staged) -> 未修改(Unmodified) -> 修改(Modified)

刚添加到文件夹中的文件处于未跟踪状态:

1. 未跟踪 -> 暂存(提交到暂存区)

```bash
git add <filename> # 将文件切换到暂存状态
git add * # 将所有已修改(为跟踪)的文件暂存
```

2. 暂存 -> 未修改(提交到本地仓库)

```bash
git commit -m "xxx" # 提交到本地仓库 -m 的意思为message
git commit -a -m "xxx" # 提交所有已修改的文件(未跟踪的文件不会提交)
```

3. 未修改 -> 修改

- 修改文件后,文件自动变成修改状态

- `git log` 查看日志

## 常用git命令

1. 重置文件

```bash
git restore <filePath> # 恢复文件 (恢复删除的文件/修改的文件为初始状态)
git restore --staged <filename> # 取消暂存状态(并不会取消操作->例如恢复删除文件)
```
2. 删除文件

```bash
git rm <filename> # 删除文件
git rm <filename> -f # 强制删除
```

3. 移动文件

```bash
git mv form to # 移动文件(重命名文件)
#示例: git mv ./1.txt ./2.txt
```

### 分支

git存储文件时,每一次代码提交都会创建一个预支对应的节点,git就是通过一个一个节点记录代码状态,节点会构成一个树状结构,也就是意味着会有分支,默认情况下,仓库只会有一个分支,名为master,在使用git时,可以创建多个分支,分支与分支之间相互独立,修改不会影响其他的分支

分支操作命令

```bash
git branch # 查看当前分支
git branch <branch name> # 创建分支
git branch -d <branch name> # 删除分支 
```

切换分支

```bash
git switch <branch name> # 切换分支
git switch -c <branch name> # 创建并切换
```

在开发中，都是在自己的分支上编写代码，代码编写完成后，在合并到主分支上

```bash
git merge <branch name># 合并指定分支到当前分支
```

### 变基(rebase)

开发中,除了通过merge来合并分支,还可以通过变基来完成合并分支

通过merge合并分支时,在提交记录中会将所有的分支创建和合并的过程显示出来,项目比较复杂时,开发过程比较波折时,需要反复创建、合并、删除，这样代码提交记录会变得极其混乱

原理：

1. 发起变基时，git会首先找到两条分支的共同祖先
2. 对比当前分支相对于祖先的历史提交，并将不同之处提取出来，存储在临时文件中
3. 将当前部分指向目标的基底，也就是最近的一次提交记录
4. 以当前基地开始，重新执行历史操作

```bash
git rebase <branch name># 将当前分支变基到指定分支
```

rebase 和 merge 对于合并分支来说,最终结果是一样的!但是变基(rebase)会使代码提交记录更加整洁和清晰



## 远程仓库(remote)

将本地库上传到远程仓库:

```bash
git remote add <remote name> <url> # 链接本地库 名字-地址
git push -u <remote name> <branch name> # 上传指定分支 到 指定库
```

远程库常用操作命令:

```bash
git remote # 列出当前关联的远程库
git remote <远程库名> <url> # 关联远程库
git remote remove <远程库名> # 删除远程库
git push -u <远程库名> <分支名> # 推送本地分支到远程库,并关联分支

# 本地库如果版本低于远程库,push默认推送不上去
# 要想推送成功,必须保证本地库和远程库的版本一致
git fetch # fetch会从远程仓库下载所有代码,使用fetch拉取,必须要进行合并
# 使用git merge 远程库名/分支名 进行合并

git pull # 拉取最新版本
```

