# 0.git常用命令

```bash
# 检查所在分支,和哪些代码没提交的缓冲区
git status 

# 检查所在分支,和哪些代码没提交
git status 

# 查看日志(包含版本号)
git reflog

# 检查详细日志 
git log

# 版本回溯,可以应本地的文件回推到某个日志节点.在没有提交到远程仓库之前,仅在提交了本地库的情况下,进行回溯,再提交的时候,
# 会发现,报错说本地比远程多一个commit------这是由于每一个版本的内容依赖于上一个版本,不能跳跃!!!!


git reset --hard 版本号

```



# 

```bash

```



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
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQC5Xz4EqXhUUnrqP5QUS65ZajwXK8UunctV734HFhGlG4UzslQOiDe4GqVfxp8cJX0WpXSQ4P+HJfFbwsCZUZmXR/3ek1o7EXWo5OdNxEJ88Gq2e6LD4QzmL8EhP8dYmwzGJhILJX2Qb7q6XUtJklQ7IkPY6hBxpz8MdBfdSgmKxZeiqd7aV7uYs5QZD8IS0+T+VLVrjFU1swyy5fOLMGLgyQvG+H1MpSDFcljZ0YQ/gdbOHC4JSOYQPU5MxSRFKEkbreROYI9Y/l3NCWALQWgLakWnZIBVLGZ4hA5gCcdHsq6X4e+a6WnDx18k2FD9woK+BahTGxFdzwYgcMXvxWQ7uiHIIi+8qwKEtCPAM8p+87WLPDDMvyh7GlDx9tmaTIdXwLoNj+860YCQx1VNgVkVa1rmBc2PLnpBzCxEVWr4BS75kfHiDhXcTMapr5/Ndn+3iWzCtid+Zs2KnEn7GGn+BVgfrl6tWK9Ey+VwZ/T34JX+N4uvFALEt/PXK8khxPk= 972849883@qq.comgit remote add origin 你的远程库地址
git remote add origin 远程url
```

5.获取远程仓库与本地合并(如果远程仓库不为空,则必须执行这一步)

```bash
git pull --rebase origin master
```

6、把本地库的内容推送到远程，使用 git push命令，实际上是把当前分支master推送到远程。执行此命令后会要求输入用户名、密码，验证通过后即开始上传。

```bash
git push -u origin master
```

# 2 将本地代码推到远程仓库的步骤如下（除了第一次）：

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

# 3.设置用户签名

首次安装git需要设置一下命令,保证能区分你的身份

```bash
git config --global user.name 用户名
git config --global user.email 邮箱
```

在C:/用户/yangz/.gitconfig文件中能查看设置的用户名和邮箱

# 4. 遇到的报错

1. 在GIT BASH Here中,修改完代码 ,然后 git commit -am "1234"  , git push 后报错

> （学习过程所遇问题）Git: fatal: unable to access 'https://github.com/zhangruiNo1/HUASUAN.git/': OpenSSL SSL_read: SSL_ERROR_SYSCALL, errno 0

解决方法 :

```BASH
 终端中输入

//取消http代理

git config --global --unset http.proxy

//取消https代理

git config --global --unset https.proxy

然后通过设置中查看代理的端口

终端中再次输入

git config --global http.proxy http://127.0.0.1:代理端口
```

注意代理端口去哪里找? ,设置--> 网络与 Intnet --> 编辑  



2. 在IDEA中commit完代码后,点击push报错

   > push to origin/master was rejected

解决方法:

```bash
1.切换到自己项目所在的目录,右键选在GIT BASH Here

2. 在窗口依次输入命令
git pull

git pull origin master

git pull origin master --allow-unrelated-histories

```







1. 每次在idea中push到远程仓库，都需要重新输入token

   解决方法：

   ```bash
   # 在输入token成功登陆后，在git Bash Here中输入以下命令,两年之内都记得
   git config --global credential.helper 'cache --timeout=63072000'
   ```

   





3. ![image-20240926174923914](https://hahaha310.oss-cn-qingdao.aliyuncs.com/image-20240926174923914.png)

   由于内容不符合校验,commit错误

   解决方法:  

   ```bash
   git commit -m "域名版本,完全上线" --no-verify
   
   ```

   4. fatal: unable to access 'https://github.com/yzhsuisuis/big-market.git/': OpenSSL SSL_read: SSL_ERROR_SYSCALL, errno 0

      或者

      unable to access 'https://github.com/yzhsuisuis/big-market.git/': OpenSSL SSL_connect: SSL_ERROR_SYSCALL in connection to github.com:443

      解决方法:(两个方法都试一下)

      方案一:

      ```bash
      git config --global http.sslVerifyfalse
      
      git config --global --unset http.proxy
      
      git config --global --unset https.proxy
      
      git config --global http.sslBackend "openssl"
      
      ```

      方案二

      ```bash
      //取消http代理
      git config --global --unset http.proxy
      //取消https代理
      git config --global --unset https.proxy
      //这里去查自己的代理端口
      git config --global http.proxy http://127.0.0.1:7890
      
      ```

      

      