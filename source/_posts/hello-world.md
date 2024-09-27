---
title: git基础操作
cover: https://ooo.0x0.ooo/2024/09/27/O4DH6K.jpg
---
Welcome to the sunny wiki!

将本地Git文件提交到Gitee（码云）远程仓库，你需要遵循一系列步骤来配置Git、初始化仓库、添加文件、提交更改，并将这些更改推送到Gitee上的远程仓库。以下是一个详细的步骤指南：

### 1. 在Gitee上创建仓库

首先，你需要在Gitee上创建一个新的仓库。登录Gitee后，点击右上角的`+`号，选择“新建仓库”，填写仓库信息（如仓库名称、描述、是否开源等），然后点击“创建”。创建完成后，Gitee会提供一个URL（HTTPS或SSH），你稍后会用到这个URL来将本地仓库与远程仓库关联起来。

### 2. 本地配置Git（如果尚未配置）

打开终端或命令提示符，输入以下命令来配置Git的全局用户信息（如果你之前已经配置过，可以跳过这一步）：

```bash
git config --global user.name "你的用户名"
git config --global user.email "你的邮箱"
```

### 3. 初始化本地Git仓库

如果你的项目文件夹还没有被Git管理，你需要先初始化一个Git仓库。在项目文件夹中打开终端或命令提示符，然后输入：

```bash
git init
```

这会创建一个`.git`文件夹，Git会在这个文件夹中存储所有的版本控制信息。

### 4. 添加文件到仓库

将你想要添加到版本控制中的文件添加到Git仓库中。使用`git add`命令：

```bash
git add .  # 添加当前目录及子目录下所有文件
# 或者
git add <文件名>  # 只添加指定的文件
```

### 5. 提交更改到本地仓库

现在，你需要将添加的文件提交到本地Git仓库中。使用`git commit`命令，并附上一条提交信息：

```bash
git commit -m "你的提交信息"
```

### 6. 将本地仓库与Gitee远程仓库关联

接下来，你需要将本地仓库与Gitee上的远程仓库关联起来。使用`git remote add`命令，并替换`<仓库URL>`为你从Gitee上获取的仓库URL：

```bash
git remote add origin <仓库URL>
```

这里的`origin`是远程仓库的默认名称，但你可以根据需要自定义。

### 7. 将更改推送到Gitee远程仓库

最后，使用`git push`命令将本地仓库的更改推送到Gitee上的远程仓库：

```bash
git push -u origin master  # 如果你的默认分支是master
# 或者，如果你的默认分支是main（GitHub等现代仓库通常使用main作为默认分支）
git push -u origin main
```

注意：如果你遵循了Gitee的默认设置，你的默认分支可能是`master`，但GitHub等平台已经转向使用`main`作为默认分支。你需要根据你的Gitee仓库设置来选择正确的分支名。

`-u`参数表示“设置上游（upstream）”，它告诉Git在后续的`git pull`操作中自动使用这个远程分支和本地分支的组合。

完成这些步骤后，你的本地Git文件就已经成功提交到Gitee远程仓库了。你可以在Gitee的网页上看到你的仓库和其中的文件。