# git log 命令

## 概述

`git log`命令用来显示已经提交的历史记录。通过`git log`命令，可以列出项目历史，筛选，以及搜索特定更改。

## 用法

### 默认格式

```javascript
git log
```

使用默认格式显示完整历史。如果输出超过一屏，可以使用`空格键`滚动，按`q`退出。

### limit

```javascript
git log -n <limit>
```

`<limit>`参数用来限制提交的数量，如`git log -n 3`只会显示最近的3个提交。

```javascript
E:\git-learn (feature -> origin) (git-learn@1.0.0)
λ git log
commit 07a2513c27d3f80baea44d7066230fa952f5185e (HEAD -> feature, origin/feature)
Author: doublejan <954464727@qq.com>
Date:   Sun Dec 22 17:28:31 2019 +0800

    update: 演示status

commit 0990804442bcff3222e1eed6fdee86d47675ba9b
Author: doublejan <954464727@qq.com>
Date:   Sun Dec 22 17:27:23 2019 +0800

    update: 修改status内容

commit 26150ea71c2ee396e6e85c385fb0e46217095897 (origin/release, origin/master, release, master)
Author: doublejan <954464727@qq.com>
Date:   Sun Dec 22 16:37:15 2019 +0800

    init 初始化项目



E:\git-learn (feature -> origin) (git-learn@1.0.0)
λ git log -n 2
commit 07a2513c27d3f80baea44d7066230fa952f5185e (HEAD -> feature, origin/feature)
Author: doublejan <954464727@qq.com>
Date:   Sun Dec 22 17:28:31 2019 +0800

    update: 演示status

commit 0990804442bcff3222e1eed6fdee86d47675ba9b
Author: doublejan <954464727@qq.com>
Date:   Sun Dec 22 17:27:23 2019 +0800

    update: 修改status内容
```

### online

```javascript
git log --oneline
```

将每个提交压缩到一行。如果需要查看项目历史的上层情况时，这会很有用。

```javascript
λ git log --oneline

07a2513 (HEAD -> feature, origin/feature) update: 演示status
0990804 update: 修改status内容
26150ea (origin/release, origin/master, release, master) init 初始化项目
```

多个参数也可以连用，比如，我们只想查看前两个提交的概述信息。

```javascript
λ git log -n 2 --oneline

07a2513 (HEAD -> feature, origin/feature) update: 演示status
0990804 update: 修改status内容
```

### stat

```javascript
git log --stat
```

`stat`参数用来显示除了提交记录以外，包含哪些文件被更改了，以及每个文件相对的增删行数。

```javascript
λ git log --stat

commit 07a2513c27d3f80baea44d7066230fa952f5185e (HEAD -> feature, origin/feature)
Author: doublejan <954464727@qq.com>
Date:   Sun Dec 22 17:28:31 2019 +0800

    update: 演示status

 .gitignore    |  5 ++++-
 doc/log.md    | 23 +++++++++++++++++++++++
 doc/status.md | 38 ++++++++++++++++++++++++++++++++++++++
 3 files changed, 65 insertions(+), 1 deletion(-)
```

### p

```javascript
git log -p
```

除了基本的提交的描述信息以外，显示一个提交记录产生的所有信息，包含提交的全部差异diff，这是项目历史中最详细的查看方式。

```git
commit 0990804442bcff3222e1eed6fdee86d47675ba9b
Author: doublejan <954464727@qq.com>
Date:   Sun Dec 22 17:27:23 2019 +0800

    update: 修改status内容

diff --git a/doc/status.md b/doc/status.md
new file mode 100644
index 0000000..124206f
--- /dev/null
+++ b/doc/status.md
@@ -0,0 +1,19 @@
+# git status 命令
+
+## 概述
+
+`git status`命令用来显示工作区和缓存区（暂存区）的状态（文件修改记录）。可以用来查看哪些更改被缓存了，哪些修改还没被缓存，哪些还没被
git跟踪。
```

### author

```javascript
git log --author="<pattern>"
```

`--author`参数用来搜索特定作者的提交。`<pattern>`可以是字符串或者正则表达式

```javascript
// 字符串
λ git log --author="doublejan" -n 1

commit 07a2513c27d3f80baea44d7066230fa952f5185e (HEAD -> feature, origin/feature)
Author: doublejan <954464727@qq.com>
Date:   Sun Dec 22 17:28:31 2019 +0800

    update: 演示status

// 正则表达式，匹配部分字母
λ git log --author="[a-j]" -n 1
commit 07a2513c27d3f80baea44d7066230fa952f5185e (HEAD -> feature, origin/feature)
Author: doublejan <954464727@qq.com>
Date:   Sun Dec 22 17:28:31 2019 +0800

    update: 演示status
```

### grep

```javascript
git log --grep="<pattern>"
```

`grep`参数用来搜索提交信息中，匹配`<pattern>`的记录。`<pattern>`可以是一段字符串或正则表达式。

```javascript
λ git log --grep="init"

commit 26150ea71c2ee396e6e85c385fb0e46217095897 (origin/release, origin/master, release, master)
Author: doublejan <954464727@qq.com>
Date:   Sun Dec 22 16:37:15 2019 +0800

    init 初始化项目
```

### file

```javascript
git log <file>
```

按文件查看。

```javascript
λ git log ./doc/status.md

commit 07a2513c27d3f80baea44d7066230fa952f5185e
Author: doublejan <954464727@qq.com>
Date:   Sun Dec 22 17:28:31 2019 +0800

    update: 演示status
```

## graph

```javascript
git log --graph
```

`--graph` 标记会绘制一幅字符组成的图形，左边是提交，右边是提交信息

