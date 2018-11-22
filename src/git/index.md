### 常用指令

```
git status

git add .

git commit -m 'msg' 

git push 

```


### 设置git

- 生成密钥
- 远程仓库中填上公钥
- 本地全局设置邮箱和密码
- 配置项目的仓库地址/如果有远程仓库
- 设置分支

> 初始化本地git

```
git init
```

> 设置远程地址
```

git remote add origin [url]

git remote add origin https://github.com/ranckprogram/express-blog.git   // origin 是推荐名称，这个可以改的 bigdata
``` 

> 设置分支
```
git push --set-upstream origin master
git branch --set-upstream-to origin/master master    // 指令可以关联分支 ,设置后可以直接git pull  git push
```

> 修改远程分支
```
git remote origin set-url [url]

```

> 拉取合并两个独立仓库的历史
```
git pull origin master –allow-unrelated-histories
```
