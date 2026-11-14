# 第 0 课：准备教材，保存第一份学习记录

## 本节目标

知道教材和自己的作品分别在哪里；用自己的话记录学习目标；亲手保存一次 Git 版本。

## 已检查的环境

- 学习仓库：D:\code\rag\llm-learning-lab，有 Git 历史，当前分支 main。
- 入门教材：D:\code\rag\llm-universe-main。
- 进阶教材：D:\code\rag\all-in-rag-main。
- 下载的 PDF：D:\code\rag\file\v1.pdf（已确认文件存在，尚未核对内容与章节）。
- Python：3.11.1。

下载 ZIP 适合阅读和运行教材，缺少 Git 历史不影响学习。教材不是你的原创作品，不需要整体复制到学习仓库。后续借鉴代码时注明来源。

## 先填写学习笔记

打开同目录的 01-learning-goals.md，把三个“待填写”换成自己的回答，然后保存。

## Git 的三个位置

工作区：你当前编辑的文件。
暂存区：你选中准备放入下一次提交的改动。
本地历史：commit 保存的版本记录。

GitHub 是远程副本。commit 保存到电脑，push 才把提交发送到远程。

## 亲手操作（CMD 和 PowerShell 均可）

逐条执行，每条执行后先看输出：

```shell
cd D:\code\rag\llm-learning-lab
git status
git add docs/00-start-here.md docs/01-learning-goals.md
git diff --cached
git commit -m "docs: record LLM learning goals"
git log --oneline -3
git status
```

第一次 status 应显示 docs/ 下有未跟踪文件。add 选择这两个文件，不会上传；diff --cached 显示待提交的内容；commit 保存一个本地版本。最后应看到新提交和 working tree clean。

按 q 可以退出 Git 的分页查看界面。

仓库已有提交者姓名和邮箱配置。如果 commit 报错，保存完整输出，不需要重新初始化仓库。

## 上传前处理远程地址

检查时发现 origin 为 https://ghfast.top/https://github.com/iliyuan/llm-learning-lab.git。
这是经过第三方中转的地址。向自己仓库上传前，改回官方地址：

```shell
git remote set-url origin https://github.com/iliyuan/llm-learning-lab.git
git remote -v
```

set-url 只改变本地保存的远程地址，不会删除本地文件或远程仓库。
确认地址后再学习 push。如果官方连接仍被重置，继续排查本地代理端口；本地 commit 不依赖网络，不受影响。

## 下一节预习：给模型提供资料

假设我们要做一个招聘知识库助手，有一条虚构资料：

岗位 A：要求 Python、SQL、RAG；不要求有模型训练经验。

用户问：“岗位 A 要求微调经验吗？”

模型没有这条资料时，可能猜错或表示不知道。把这条资料连同问题交给模型，就提供了作答依据。等资料变成数千条，系统需要先挑出相关内容，这就是我们学习检索的动机。

给模型提供资料，不会自动修改模型参数；模型也仍可能读错。因此后续要学习引用来源、拒答和评估。

本节不需要安装教材的全部依赖，也不需要购买模型服务。
