# git status 命令

## 概述

`git status`命令用来显示工作区和缓存区（暂存区）的状态（文件修改记录）。可以用来查看哪些更改被缓存了，哪些修改还没被缓存，哪些还没被git跟踪。

`git status`命令的输出不包含已经提交到项目历史的信息。这种信息应该使用`git log`。

## 命令格式

```git
git status
```

## 示例

`git status`命令用来查看`git add`命令，和`git commit`命令的进展。同时，也会输出下一步可以进行的操作，主要是添加缓存，移除缓存的相关命令。

```git
λ git status
On branch feature
Your branch is up to date with 'origin/feature'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   doc/status.md

Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        deleted:    doc/index.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        doc/main.md

```

## 忽略文件

被忽略，或者不被追踪的文件有两类，一类是`.exe`, `.obj`这种二进制文件，要么是新增但未提交的文件。使用`.gitignore`文件，可以定制文件忽略规则。

### 写法

- `.gitignore`文件中，每个文件名独占一行，表示将要忽略的文件。
- 注释使用`#`开头。
- 文件夹或目录，使用`/`结尾。
- 允许使用通配符`*`。
- `!`表示取反，不忽略某某文件。

```git
# 忽略node资源目录
/node_modules

# 不忽略doc目录及下面所有文件
!/doc/*
```
