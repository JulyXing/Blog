#### Git 常用命令总结
---
用户配置
```
  git config --global user.name  邢柳
  git config --global user.email julyxing@163.com
```

1 克隆
```
  git clone git@github.com:JulyXing/Blog.git
```

2 更新
```
  git pull （默认拉取 master 分支代码）
  当存在分支， 为避免分支代码混乱，使用
  git pull origin bname
```

3 提交
```
  git add files                  将文件添加工作区
  git commit -m 'comment'
  git push （默认向 master 分支提交代码）
  当存在分支，为避免分支提交错误，使用
  git push origin bname
```

4 冲突
```
  git checkout Readme.md         忽略文件
  git reset e9cb6f38             回滚版本至指定 commit 版本号
  git checkout 0.0.1             回滚到指定的 tag 0.0.1 版本
```

5 标签
```
  git tag                        查看标签
  git tag -v                     查看标签名
  git tag -a tname -m 'comment'  创建 tname 标签，描述为 comment
  git push origin tname          提交标签
```
6 分支

```
  git branch                 查看本地分支
  git branch -a              查看远端分支
  git branch bname           创建分支
  git push origin bname      向远端推送分支
  git branch -d bname        删除本地分支
  git push origin :bname     删除远端分支
  git checkout bname         切换分支
  git checkout -b bname      创建并切换分支
  git merage --no-ff bname   合并分支(指向新节点)
```

注： bname 为 branch_name 缩写。