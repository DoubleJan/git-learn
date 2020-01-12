# checkout 检出

## 一 概述

`git checkout`命令有三个不同的用法，分别是：

- 检出文件：检出文件可以查看某个文件的旧版本。
- 检出提交：会到某次提交的状态，让工作目录与某次提交时完全匹配。
- 检出分支：切换到某个分支。

## 二 用法

### 1. 检出分支

```javascript
git checkout branchName
```

### 2. 检出文件

将工作区的某个文件变成某次提交的对应文件的拷贝，并添加到缓存区。可以像别的文件一样正常的推送这个文件，可以用来将某个文件回滚到特定旧版本。

#### 命令

```javascript
git checkout <commit> <file>
```

#### 例子

```javascript
git checkout 07a2513 ./doc/log.md

git status
On branch feature
Your branch is up to date with 'origin/feature'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   doc/log.md   // 说明此时log.md是保存在缓存区

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   doc/checkout.md
```

### 3. 检出提交

更新工作区的所有文件，使得和某次提交时的文件一致。可以将commit时候的哈希字符串或者标签作为commit参数值。此时会离开默认的HEAD状态。默认情况下，HEAD指向当前正在开发的本地分支，此时，HEAD会指向当前检出的一个提交。因此，在这里做的修改不会影响到当前正在开发的原状态，但是，一定要在切换回分支前，确定是否提交修改，否则，修改会被携带过去。

```javascript
git checkout <commit>
```





