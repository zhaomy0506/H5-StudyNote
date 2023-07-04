## 安装git

> Git官网[下载](https://git-scm.com/) 

## 初始化git账户

1. 设置用户名

```
git config --global user.name "用户名"
```

2. 设置邮箱地址

```
git config --global user.email "邮箱地址"
```

3. 查看设置的用户名以及地址

```
git config --list
```

4. 配置密钥

```
ssh-keygen -t rsa -C "邮箱地址"
```

将配置好的密匙添加到github/gite上


## git 本地仓库

> 流程:本地文件夹 -> 变成工作区 -> 上传暂存区 -> 上传本地仓库

    1. 项目结构搭建好
    2. 初始化工作区 `git init`
    3. 上传暂存区 `git add .`
    4. 上传本地仓库 `git commit -m"描述"`  
       - 忘记写 -m  可使用:`wq+Enter`  退出
    5. 链接远程仓库 `git remote add orgin 远程仓库地址`
    6. 推送到远程仓库 `git push -u origin master`



 ```
  git status 命令 查看暂存区情况
  git checkout 文件名称 检出暂存区文件
  git log 查看上传日志
  git reset --hard"hash值" 回溯版本
 ```

## 流程

**首次推送**

- 项目结构搭建好 -> 工作区 -> 文件上传

```
  1. 项目结构搭建好
  2. 初始化工作区git init
  3. 上传暂存区 git add .
  4. 上传本地仓库 git commit -m"描述"
  5. 链接远程仓库git remote add orgin 远程仓库地址
  6. 推送到远程仓库 git push -u origin master
```

**后续修改**

- 远程仓库拿到本地 -> 开发 ->文件上传Gitee

 ```
  1. 克隆到本地git clone 远程仓库地址
  2. 开始开发
  3. 上传暂存区 git add .
  4. 上传本地仓库 git commit -m"描述"
  5. 推送到远程仓库 git push
 ```

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
