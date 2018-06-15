## branch

```
// 创建并切换到新分支
git checkout -b branchName
```
## tag

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
