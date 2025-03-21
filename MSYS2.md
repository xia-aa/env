# MSYS2

```sh
pacman -Syu
```

## Git

```sh
  /d/github/env                                                                                                                                                                      15:32:49 
❯ where git
/d/Git/cmd/git
/usr/bin/git
/usr/bin/git
/d/Git/bin/git
  /d/github/env                                                                                                                                                                      15:32:54
❯ whereis git
git: /usr/bin/git.exe /usr/share/git /d/Git/cmd/git.exe /d/Git/bin/git.exe /usr/share/man/man1/git.1.gz
  /d/github/env                                                                                                                                                                      15:33:03
❯ git -v
git version 2.45.0.windows.1
  /d/github/env                                                                                                                                                                      15:33:13
❯ /usr/bin/git -v
git version 2.46.0
  /d/github/env                                                                                                                                                                                         15:33:20 
❯
```

```sh
git config list
```

```sh
# git for MSYS2
init.defaultbranch=main
user.name=aa
user.email=Nahida-aa@outlook.com
http.sslverify=false
```

```sh
# git for Windows
diff.astextplain.textconv=astextplain
filter.lfs.clean=git-lfs clean -- %f
filter.lfs.smudge=git-lfs smudge -- %f
filter.lfs.process=git-lfs filter-process
filter.lfs.required=true
http.sslbackend=openssl
http.sslcainfo=D:/Git/mingw64/etc/ssl/certs/ca-bundle.crt
core.autocrlf=true
core.fscache=true
core.symlinks=false
pull.rebase=false
credential.helper=manager
credential.https://dev.azure.com.usehttppath=true
init.defaultbranch=main
init.defaultbranch=main
user.name=aa
user.email=Nahida-aa@outlook.com
http.sslverify=false
```

### github

#### empty github repo

local repo push to empty github repo

```sh
git remote add origin git@github.com:Nahida/env.git
git branch -M main
git push -u origin main
```

modify github repo, and modify local repo, then push local repo to github repo

```sh
git pull origin main
# 解决任何可能的冲突并添加解决后的文件
# git add <冲突文件>

# 提交解决冲突后的更改（如果有冲突）
# git commit -m "解决冲突"

# 推送本地更改到远程仓库
git push origin main
```

#### no empty github repo

##### SSH

```sh
ssh -V
# windows sc:Service Control query: 查询服务的状态
sc query ssh-agent
# windows net:管理本地计算机的用户帐户、组和共享资源
# # start: net 的子命令，启动服务，服务名为 ssh-agent
net start ssh-agent
# if MSYS2
eval "$(ssh-agent -s)"
# 停止服务
net stop ssh-agent
# 测试SSH连接
ssh -T git@github.com
# 应该看到以下输出
# Hi <username>! You've successfully authenticated, but GitHub does not provide shell access.
# 如果看到以下输出，表示SSH连接失败
# ssh: connect to host github.com port 22: Connection timed out
```

#### VScode: code -> github repo

默认使用的是https协议

```sh
git remote -v
# output
origin  https://github.com/<your_username>/<repository>.git (fetch)
origin  https://github.com/<your_username>/<repository>.git (push)
```

更改为SSH协议

```sh
git remote set-url origin git@github.com:<your_username>/<repository>.git
# 更改 协议后 需要重新设置 upstream
git push --set-upstream origin main
```
