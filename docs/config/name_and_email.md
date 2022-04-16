# 用户名和邮箱

## 作用

当你提交代码时会展示，谁提交的代码。意思是作者是谁。

## 配置默认用户和邮箱

1. 打开git bash here

2. 设置`user.name`和`user.email`配置信息 【默认全局配置】

   ```bash
   git config --global user.name "你的GitHub用户名"
   git config --global user.email "你的GitHub注册邮箱"
   ```



>[!TIP]
>
>用户名和邮箱不一定要和GitHub上一样。一般都是和GitHub一样。

**查看配置；**

```bash
 git config --list # 查看所有配置。
 git config user.name  # 只查看user.name字段配置
```

## 添加新用户和邮箱

```bash
git config --global --add user.name "用户名" #
git config --global --add user.email "邮箱" #
```

## 删除用户和邮箱

```bash
git config --global --unset user.name "要删除的用户名"
git config --global --unset user.email "要删除的邮箱"
```



## 修改用户名或邮箱配置

直接重新执行一遍配置用户名和密码的命令，覆盖之前的内即可。

