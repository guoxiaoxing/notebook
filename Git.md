## Branch

```
// 创建并切换到新分支
git checkout -b branchName
```
## Tag

```
// 创建新的Tag
git tag tagName
```

## 暂存修改

```
git stash  
git stash list  
git stash clear  
git stash apply  
```

## 代码回滚

- git reverse：会撤销commit并新建一个commit，相对比较安全。
- git reset：会将commit撤回暂存区。

```
// 撤销上一次commit
git reverse HEAD

// 撤销上n次commit
git reverse HEAD-n
```

```
// 查看当前的commit记录
git reflog

// 撤回本地分支到Obfafd
git reset --hard Obfafd

// 强制push到远程分支
git push -f
```

## SubModule

基本操作命令

```
git submodule --h 查看帮助
git submodule add添加子模块
```
生成.gitmodules文件

```
path = rack
url = git://github.com/chneukirchen/rack.git
```
复制代码
更新方式与普通项目一样

克隆一个带子模块的项目

```
git submodule init 初始化子模块
git submodule update 因为你所拥有的指向子模块的指针和子模块目录的真实状态并不匹配
```


