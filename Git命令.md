# Git命令

## 1.仓库初始化

```shell
git init
```

## 2.查看文件状态

```shell
git status
git status -s #精简方式显示
```

## 3.添加到暂存区

```shell
git add 文件名字
```

## 4.添加到仓库

```shell
git commit -m '描述信息'
```

## 5.撤销对文件的修改

```shell
git checkout -- 文件名字
```

## 6.一次性添加多个文件

```shell
git add  .
```

## 7.取消暂存的文件

```shell
git reset HEAD 要移出的文件名称
git reset HEAD . #所有文件移除暂存区
```

## 8.跳过暂存区

```shell
git commit -a -m '描述信息' #文件必须是已经追踪过的
```

## 9.移除文件

```shell
# 从 Git仓库和工作区中同时移除 index.js 文件
git rm -f index.js
# 只从 Git 仓库中移除 index.css，但保留工作区中的 index.css 文件
git rm --cached index.css
```

## 10.查看提交历史

```shell
# 按时间先后顺序列出所有的提交历史，最近的提交在最上面
git log

# 只展示最新的两条提交历史，数字可以按需进行填写
git log -2

# 在一行上展示最近两条提交历史的信息
git log -2 --pretty=oneline

# 在一行上展示最近两条提交历史信息，并自定义输出的格式
# &h 提交的简写哈希值  %an 作者名字  %ar 作者修订日志  %s 提交说明
git log -2 --pretty=format:"%h | %an | %ar | %s"
```

## 11.回退指定版本

```shell
#一定要是nothing状态
git status
# 在一行上展示所有的提交历史
git log --pretty=oneline

# 使用 git reset --hard 命令，根据指定的提交 ID 回退到指定版本
git reset --hard <CommitID>

# 在旧版本中使用 git reflog --pretty=online 命令，查看命令操作的历史
git reflog

# 再次根据最新的提交 ID，跳转到最新的版本
git reset --hard <CommitID>
```

## 12.创建gitee仓库链接

```shell
git remote add origin 你的仓库地址 #添加  origin 别名 默认
```

## 13.推送本地代码到云仓库

```shell
git push -u origin "master" # 第一次设置
git push #第二次以后提交
```

## 14.删除 gitee 仓库链接

```shell
git remote remove origin
```

## 15.生成ssh key

```shell
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

## 16.测试 ssh key 是否配置成功

```shell
ssh -T git@gitee.com
```

## 17.克隆仓库到本地

```shell
git clone Url仓库地址
```

## 18.查看分支列表

```shell
git branch
```

## 19.创建分支

```shell
git branch 分支名字
```

## 20.切换分支

```shell
git checkout 分支名字 #切换分支之前一定要是nothing
```

## 21.快速创建并切换分支

```shell
git checkout -b  分支名字
```

## 22.合并分支

```shell
git checkout master
git merge 分支名字
```

## 23.解决分支冲突

```shell
git checkout master
git merge 分支名字
#此时出现了冲突  4选1
git add .
git commit -m '告诉git已经解决了冲突'
```

## 24.将本地分支推送到远程仓库

```shell
# -u 表示把本地分支和远程分支进行关联，只在第一次推送的时候需要带 -u 参数
git push -u 远程仓库的别名 本地分支名称:远程分支名称

# 实际案例
git push -u origin login:loginer

# 如果希望远程分支的名称和本地分支名称保持一致，可以对命令进行简化
git push -u origin login
```

## 25.查看远程分支列表

```shell
git remote show origin
```

## 26.跟踪分支(将远程分支克隆到本地)

```shell
# 示例
git checkout login

# 从远程仓库中，把对应的远程分支下载到本地仓库，并把下载的本地分支进行重命名
git checkout -b 本地分支名称 远程仓库名称/远程分支名称

# 示例
git checkout -b loginer origin/login
```

## 27.拉取代码到本地

```shell
git pull #更新所有分支
git pull origin reg #更新具体某一个分支
```

## 28.删除远程分支

```shell
# 删除远程仓库中，制定名称的远程分支
git push 远程仓库名称 --delete 远程分支名称

# 示例
git push origin --delete login
```

## 29.删除本地分支

```shell
git branch -d 分支名字 #删除已合并的分支
git branch -D 分支名字 #强制删除
```

## 30.强制删除本地文件

- rm -rf 文件名  (只能在 git bash 里面使用)