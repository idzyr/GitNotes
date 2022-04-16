# 合并冲突

在合并时难免不会遇到冲突，遇到冲突我们就要通过对比冲突文件解决冲突后再提交。

## 合并时冲突<<<< HEAD是什么意思

````bash
<<<<<<< HEAD

new new new new code

=======

old old old code

>>>>>>> xxxxxxxxxxxxxxxxxxxxxxx
````

**分析：**

- HEAD 到 =======里面的new new new 是自己的commit的内容

- =========到 >>>>>>里面的old old old是下拉的内容

根据需要保留和删除代码就行了  完事把<<<<<<<    =======      >>>>>>都删掉冲突就解决了









