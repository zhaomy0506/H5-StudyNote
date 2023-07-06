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

在git中文件分为四种状态: 未跟踪 ->已跟踪 -> 暂存 -> 未修改 -> 修改

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

## 分支

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



## 上传到远程仓库

1. `git remote add orgin 远程仓库地址` 链接远程仓库 
2. `git push -u origin master` 推送到远程仓库 



**遇到问题**:

  ```
1. 本地文件与仓库内容冲突时
	- 执行 git pull origin master
	- 修改冲突后
	- git push
2. 为了避免冲突,每天git pull
3. 空文件夹,上传会报错
4. 不能直接在仓库删除,删除过后本地仓库跟远程仓库会有冲突,可以把远程仓库的最新代码(git pull)在本地删除,再上传到远程仓库
5. 对文件增删改,都需要上传
  ```
