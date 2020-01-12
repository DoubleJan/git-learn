# checkout 检出

## git checkout 命令概述

`git checkout`命令有三个不同的用法，分别是：

- 检出文件：检出文件可以查看某个文件的旧版本。
- 检出提交：会到某次提交的状态，让工作目录与某次提交时完全匹配。
- 检出分支：切换到某个分支。

## 用法

### 检出分支

```javascript
git checkout branchName
```

### 检出文件

将工作区的某个文件变成某次提交的对应文件的拷贝，并添加到缓存区。

```javascript
git checkout <commit> <file>
```

### 检出提交

更新工作区的所有文件，使得和某次提交时的文件一致。可以将commit时候的哈希字符串或者标签作为commit参数值.此时会离开默认的HEAD状态.

```javascript
git checkout <commit>
```





