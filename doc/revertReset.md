# 项目回滚

## 一 使用`git revert`安全回滚

### 1. 概述

`git revert`命令用来撤销一个已经提交的版本。但是它是通过一个用来撤销改动的新的提交来实现的。也就是说，新的用来撤销修改的提交版本覆盖之前的提交版本。因此，所有的历史版本都会保留，所以是安全的回滚。

### 2. 命令

```javascript
git revert <commit>
```

### 3. 例子

```javascript
λ git revert 96a1d64
CONFLICT (modify/delete): doc/checkout.md deleted in parent of 96a1d64... update: checkout and modified in HEAD. Version HEAD of doc/checkout.md left in tree.
error: could not revert 96a1d64... update: checkout
hint: after resolving the conflicts, mark the corrected paths
hint: with 'git add <paths>' or 'git rm <paths>'
hint: and commit the result with 'git commit'
```
