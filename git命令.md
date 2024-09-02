# 1. 将本地代码推到远程仓库的命令

1.初始化,把这个目录变成git可以管理的仓库

```bash
git init
```



2.把文件天骄到版本库中,使用命令添加到暂存区去

```bash
git add .
```

可选项:

```bash
git add -A  提交所有变化
git add -u  提交被修改(modified)和被删除(deleted)文件，不包括新文件(new)
git add .  提交新文件(new)和被修改(modified)文件，不包括被删除(deleted)文件
```

3.告诉git把文件提交到远程仓库

```bash
git commit -m 'first commit'                                                        
```

4.关联远程仓库

```bash
git remote add origin 你的远程库地址
```

5.获取远程仓库与本地合并(如果远程仓库不为空,则必须执行这一步)

```bash
git pull --rebase origin master
```

6、把本地库的内容推送到远程，使用 git push命令，实际上是把当前分支master推送到远程。执行此命令后会要求输入用户名、密码，验证通过后即开始上传。

```bash
git push -u origin master
```

## **2 将本地代码推到远程仓库的步骤如下（除了第一次）：**

> 可以直接执行（如果没有新文件）：

```bash
git commit -am '说明'   
git push
```

>  如果有新文件产生(见上面)

```bash
git add -A

git commit -m "first commit"

git pull --rebase origin master

git push -u origin maste
```

