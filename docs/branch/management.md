# 管理策略

## 分支命名规范

| 分支     | 命名          | 说明                                                         | 派生     | 合并目标         |
| -------- | ------------- | ------------------------------------------------------------ | -------- | ---------------- |
| 主分支   | `master/main` | 主分支，所有提供给用户使用的正式版本，<br/>都在这个主分支上发布 |          |                  |
| 开发分支 | `dev`         | 开发分支，永远是功能最新最全的分支                           | 主分支   | 主分支           |
| 功能分支 | `feature-*`   | 新功能分支，某个功能点正在开发阶段                           | 开发分支 | 开放分支         |
| 发布版本 | `release-*`   | 发布定期要上线的功能                                         | 开发分支 | 开发分支和主分支 |
| 修复分支 | `fixbug-*`    | 修复线上代码的 bug                                           | 主分支   | 开发分支和主分支 |

## 主分支 (master)

首先，代码库应该有一个、且仅有一个主分支。所有提供给用户使用的正式版本，都在这个主分支上发布。

Git主分支的名字，默认叫做 Master 。它是自动建立的，版本库初始化以后，默认就是在主分支在进行开发。

## 开发分支(dev)

主分支只用来发布重大版本，日常开发应该在另一条分支上完成。我们把开发用的分支，叫做 Dev
这个分支可以用来生成代码的最新隔夜版本（nightly）。如果想正式对外发布，就在 Master 分支上，对 Dev 分支进行”合并”（merge）。

**流程演示；**

1. 从master分支创建dev分支

   ```bash
   git checkout -b dev master
   ```

2. 将 Dev 分支合并到Master 分支

   切换到 Master 分支

   ```bash
   git checkout master 
   ```

   合并到master分支

   ````bash
   git merge –no–ff dev
   ````

> [!TIP]
>
> 这里稍微解释一下，上一条命令的`–no–ff`参数是什么意思。默认情况下，Git执行”快进式合并”（fast-farward merge），会直接将 Master 分支指向 Dev 分支。
> 使用`–no–ff`参数后，会执行正常合并，在 Master 分支上生成一个新节点。为了保证版本演进的清晰，我们希望采用这种做法。

## 功能分支（feature）

功能分支的名字，可以采用`feature- *` 的形式命名。

1. 从dev分支创建一个功能分支

   ```bash
   git checkout -b feature-x dev
   ```

2. 开发完成后，将功能分支合并到dev 分支

   ```bash
   git checkout dev
   git merge –no-ff feature-x
   ```

3. 删除feature分支：

   ```bash
   git branch -d feature-x
   ```



## 预发布分支（release）

   第二种是预发布分支，它是指发布正式版本之前（即合并到 Master 分支之前），我们可能需要有一个预发布的版本进行测试。
   预发布分支是从 Dev 分支上面分出来的，预发布结束以后，必须合并进 Dev 和 Master 分支。它的命名，可以采用`release- *` 的形式。

1. 从dev创建一个预发布分支

   ```bash
   git checkout -b release-1.2 dev
   ```

2. 确认没有问题后，合并到master分支：

   ```bash
   git checkout master
   git merge –no-ff release-1.2
   ```

   

3. 对合并生成的新节点，做一个标签:

   ```bash
   git tag -a 1.2
   ```

4. 再合并到dev 分支

   ```bash
   git checkout dev
   git merge –no-ff release-1.2
   ```

6. 最后，删除预发布分支：

   ```bash
   git branch -d release-1.2
   ```

## 修补分支 (fixbug)

最后一种是修补bug分支。软件正式发布以后，难免会出现bug。这时就需要创建一个分支，进行bug修补。
修补bug分支是从 Master 分支上面分出来的。修补结束以后，再合并进 Master 和 Dev 分支。它的命名，可以采用`fixbug- *` 的形式。

1. 创建一个修补bug分支

   ```bash
   git checkout -b fixbug-0.1 master 
   ```

   

2. 修补结束后，合并到master分支并创建一个tag

   ```bash
   git checkout master
   git merge –no-ff fixbug-0.1
   git tag -a 0.1.1
   ```

3. 再合并到dev 分支：

   ```bash
   git checkout dev
   git merge –no-ff fixbug-0.1
   ```

   

4. 最后，删除”修补bug分支”

   ```bash
   git branch -d fixbug-0.1
   ```


> Git 分支命名规范(完)
>
> https://blog.csdn.net/qq_33858250/article/details/81047883
