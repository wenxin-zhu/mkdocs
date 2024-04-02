# git

[link](https://blog.csdn.net/bjbz_cxy/article/details/116703787?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522168879325716800211587219%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=168879325716800211587219&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-116703787-null-null.142^v88^control,239^v2^insert_chatgpt&utm_term=git%20&spm=1018.2226.3001.4187)

## Gitee上传代码

### 1	首次上传

1.1	在Gitee上创建远程仓库git_test

1.2	配置用户名和邮箱

```bash
git config --global user.name "zwx"
git config --global user.email "1728026380@qq.com"
# 检查配置
# git config user.name
# git config user.email
```

1.3	本地仓库

```bash
# 进入本地项目目录

# 初始化本地仓库
git init

# 添加项目目录下所有文件至暂存区
git add . 
# 查看当前git状态
# git status

# 提交到本地仓库
git commit -m '本次提交的说明'
```

1.4	远程仓库

```bash
# 在远程仓库复制http链接
# 如 https://gitee.com/zxmh/git_test.git

# 将本地仓库与远程仓库相连接
git remote add origin https://gitee.com/zxmh/git_test.git

# 将本地仓库中的文件推送至远程仓库中
git push -u origin master
```

### 2	继续上传

```bash
git add . 
git commit -m '本次提交的说明'
git push -u origin master
```

### 3	拉取上传

```bash
# 拉取代码
git clone https://gitee.com/zxmh/git_test.git

# 上传
cd git_test
git add . 
git commit -m '本次提交的说明'
git push -u origin master
```

## log

```bash
# 显示日志
git log 
# 图形化显示日志
git log --all --graph --decorate
# 更紧凑的视图（最好用）
git log --all --graph --decorate --oneline
```

## diff

```bash
# 显示当前状态与上一次commit的不同
git diff
# 显示当前状态与commit1的不同
git diff commit1
```

## branch

```bash
# 创建分支
git branch name
# 切换分支
git checkout name
# 创建并切换分支
git checkout -b name

# 查看分支
git branch
# 查看分支详细信息
git branch -vv

# 合并name分支到当前分支上来
git merge name
```

##  remote 

```bash
# 查看本地仓库的远程仓库
git remote 
# 添加远程仓库（origin是远程仓库的约定俗成的名字）（url可以是网址或者本地路径）
git remote add <name> <url>
# 上传
git push <remote name> <local branch>:<remote branch>
# 下载
git clone <url> <dir name>
# 不获取版本历史信息，更加快速
git clone <url> <dir name> --shallow

# 同步远程仓库的更改到本地
git fetch <remote name>
# 同步远程仓库的更改到本地并与当前分支合并
git pull <remote name>
```

## stash

```bash
# 将工作目录恢复到上一次提交的状态
git stash
# 撤回stash的恢复
git stash pop
```



```bash
# 拉取代码
git clone https://gitee.com/zxmh/git_test.git

# 创建分支
git branch name
# 切换分支
git checkout name

cd git_test
# 将当前文件夹加入到暂存区
git add . 
# 提交到本地仓库
git commit -m '本次提交的说明'
# 提交到远程仓库
git push -u origin master

# 显示日志
git log --all --graph --decorate --oneline

# 更新远程仓库
git fetch --all
```



