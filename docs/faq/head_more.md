# git reset --hard HEAD^后显示more

## 问题分析

```
fatal: ambiguous argument 'HEAD
': unknown revision or path not in the working tree.
Use '--' to separate paths from revisions, like this:
'git <command> [<revision>...] -- [<file>...]'
```


这是因为cmd控制台中换行符默认是^，而不是\ ，所以它的more？的意思是问你下一行是否需要再输入，而^ 符号就被当做换行符而被git命令忽略掉了。

## 解决

1. 加引号：

   `git reset --hard "HEAD^"`

2. 加一个^：

   `git reset --hard HEAD^^`

   换成 `git reset --hard HEAD~` 或者 `git reset --hard HEAD~1~` 

   后面的数字表示回退几次提交，默认是一次

当然还可以换成git bash，powershell等就不会出现这种问题了



> git reset --hard HEAD^后显示more?的解决方案
>
> https://blog.csdn.net/qq_32623363/article/details/78968077