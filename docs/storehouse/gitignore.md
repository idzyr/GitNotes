# .gitignore【忽略】

## 作用

告诉git忽略部分文件不被，提交。

> [!NOTE] 
>
> `.gitignore`只能忽略那些原来没有被track(没有进行`git add`)的文件，如果某些文件已经被纳入了版本管理中，则修改`.gitignore`是无效的

## 如何使用

1. 在需要和忽略文件的目录创建`.gitignore`文件。

2. 打开`.gitignore`文件 使用通配符来编写规则，每条规则占一行。


### 部分规则举例

   ```bash
   *[py]    # 匹配文件名以py结尾的文件。
   !test.py # 不要忽略此test.py文件。如果文件名称有!可以使用\!来转义。
   src/ # 表示匹配src目录。# 不会匹配到顶级目录。
   **/res # 匹配多级目录下的res
   ```



## 忽略已被track的文件

````bash
git rm -r --cached .# 清除一下相关的缓存内容
git add . # 重新提交
git commit -m 'update .gitignore'
````

`.gitignore`文件,具体的规则一搜就有.我在使用GIT的过程中,明明写好了规则,但问题不起作用,每次还是重复提交,无法忍受.其实这个文件里的规则对已经追踪的文件是没有效果的.所以我们需要使用rm命令清除一下相关的缓存内容.这样文件将以未追踪的形式出现.然后再重新添加提交一下`,.gitignore`文件里的规则就可以起作用了.



> gitignore 不起作用的解决办法
>
> https://www.cnblogs.com/sloong/p/5523244.html







