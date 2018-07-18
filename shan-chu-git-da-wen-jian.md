## 删除Git记录里的大文件 {#删除git记录里的大文件}

### 仓库自身的增长 {#仓库自身的增长}

大多数版本控制系统存储的是一组初始文件，以及每个文件随着时间的演进而逐步积累起来的差异；而 Git 则会把文件的每一个差异化版本都记录在案。这意味着，即使你只改动了某个文件的一行内容，Git 也会生成一个全新的对象来存储新的文件内容。久而久之，Git 仓库会变得十分臃肿。

### 解决办法 {#解决办法}

#### step 1. 把代码拉到本地 {#step-1.-把代码拉到本地}

```
git clone git
@github
.
com:
congyucn/GAN
-102
CategoryFlower.git
```

#### step 2. 查看占用空间 {#step-2.-查看占用空间}

```
du 
-d
 1 -h

68K         ./.idea
20M         ./.git
20M         .
```

#### Step 3. 查看哪些历史提交过文件占用空间较大 {#step-3.-查看哪些历史提交过文件占用空间较大}

使用以下命令可以查看占用空间最多的10个文件：

```
git rev-list --objects --all | 
grep
"$(git verify-pack -v .git/objects/pack/*.idx | sort -k 3 -n | tail -10 | awk '{print$1}')"
```

![](http://i4.bvimg.com/653764/c82a84e5688ece07.png "Markdown")

```
rev-list 命令用来列出Git仓库中的提交，我们用它来列出所有提交中涉及的文件名及其ID。 该命令可以指定只显示某个引用（或分支）的上下游的提交。

--objects：列出该提交涉及的所有文件ID。

--
all
：所有分支的提交，相当于指定了位于/refs下的所有引用。


verify
-
pack
 命令用于显示已打包的内容。
```

#### Step 4. 重写commit，删除大文件 {#step-4.-重写commit删除大文件}

使用以下命令，删除历史提交过的大文件：

```
git 
filter
-branch --force --index-
filter
 'git rm -rf --cached --ignore-unmatch big-file.jar' --prune-empty --tag-name-
filter
 cat -- --all
```

上面脚本中的`big-file.jar`请换成你第一步查出的大文件名，或者这里直接写一个目录。

```
filter
-branch 命令可以用来重写
Git
仓库中的提交

--index-
filter
 参数用来指定一条
Bash
命令，然后
Git
会检出（checkout）所有的提交， 执行该命令，然后重新提交。

–all 参数表示我们需要重写所有分支（或引用）。
```

在重写提交的过程中，会有以下日志输出:

```
Rewrite
 6cdbb293d453ced07e6a07e0aa6e580e6a5538f4 (
266
/
266
)

# Ref 'refs/heads/master' was rewritten
```

如果显示`xxxxx unchanged`, 说明repo里没有找到该文件, 请检查路径和文件名是否正确，重复上面的脚本，把所有你想删除的文件都删掉。

#### Step 5. 推送修改后的repo {#step-5.-推送修改后的repo}

以强制覆盖的方式推送你的repo, 命令如下:

```
git push origin master 
--force
```

#### Step 6. 清理和回收空间 {#step-6.-清理和回收空间}

虽然上面我们已经删除了文件, 但是我们的repo里面仍然保留了这些objects, 等待垃圾回收\(GC\), 所以我们要用命令彻底清除它, 并收回空间，命令如下:

```
rm -rf .git/refs/original/

git reflog expire 
--expire=now --all


git gc 
--prune=now
```

至此，我们已经彻底的删除了我们不想要的文件。

