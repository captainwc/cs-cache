# git操作指南



## 连接github

### 连接

1. 首先要在你的github上面，new一个github与你电脑之间连接用的ssh-keys，把你的公钥粘贴进去

2. 然后`ssh -T git@github.com`，测试网络是否通畅。这一步连接不通后面就不用做了

3. 成功后，`git remote add origin git@github.com:username/reposityname`，添加远程主机。远程主机名字为 origin
4. `git remote -v`查看一下



### 初始化

直接`push origin`似乎是会出现一些问题的

如果你在建立仓库时，创建了一个README.md，等，反正是已经有了一个提交，则你后面的提交会提示你，不能直接push、不能合并没有关系的两个历史记录等等错误

这时候，需要：

1. `git git config pull.rebase true`
2. `git pull origin main`
3. `git push origin main`

第一步选择rebase false，即用merge的话，会提示不能merge

