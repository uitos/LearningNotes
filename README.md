# 目录

[Java](Java/README.md)

[SpringCloud](SpringCloud/README.md)

[Git](Git/README.md)

[Docker](Docker/README.md)

[Lua](Lua/README.md)

[Nginx](Nginx/README.md)



[📙 Emojipedia — 😃 Home of Emoji Meanings 💁👌🎍😍](https://emojipedia.org/)

# Markdown 使用 Emoji 表情

有两种方法可以将表情符号添加到Markdown文件中：将表情符号复制并粘贴到Markdown格式的文本中，或者键入*emoji shortcodes*。

## 复制和粘贴表情符号

在大多数情况下，您可以简单地从[Emojipedia](https://emojipedia.org/) 等来源复制表情符号并将其粘贴到文档中。许多Markdown应用程序会自动以Markdown格式的文本显示表情符号。从Markdown应用程序导出的HTML和PDF文件应显示表情符号。

**Tip:** 如果您使用的是静态网站生成器，请确保将HTML页面编码为UTF-8。.

## 使用表情符号简码

一些Markdown应用程序允许您通过键入表情符号短代码来插入表情符号。这些以冒号开头和结尾，并包含表情符号的名称。

```text
去露营了！ :tent: 很快回来。

真好笑！ :joy:
```

呈现的输出如下所示：

去露营了！⛺很快回来。

真好笑！😂

**Note:** 注意：您可以使用此[表情符号简码列表](https://gist.github.com/rxaviers/7360908)，但请记住，表情符号简码因应用程序而异。有关更多信息，请参阅Markdown应用程序的文档。

# Git 提交规范

commit message = subject + ：+ 空格 + message 主体

例如：feat:：增加用户注册功能

常见的 subject 种类以及含义如下：

1. feat: 新功能（feature）


- 用于提交新功能。
- 例如：feat: 增加用户注册功能

2. fix: 修复 bug

- 用于提交 bug 修复。
- 例如：fix: 修复登录页面崩溃的问题


3. docs: 文档变更

- 用于提交仅文档相关的修改。
- 例如：docs: 更新README文件


4. style: 代码风格变动（不影响代码逻辑）

- 用于提交仅格式化、标点符号、空白等不影响代码运行的变更。
- 例如：style: 删除多余的空行


5. refactor: 代码重构（既不是新增功能也不是修复bug的代码更改）

- 用于提交代码重构。
- 例如：refactor: 重构用户验证逻辑


6. perf: 性能优化

- 用于提交提升性能的代码修改。
- 例如：perf: 优化图片加载速度


7. test: 添加或修改测试

- 用于提交测试相关的内容。
- 例如：test: 增加用户模块的单元测试


8. chore: 杂项（构建过程或辅助工具的变动）

- 用于提交构建过程、辅助工具等相关的内容修改。
- 例如：chore: 更新依赖库


9. build: 构建系统或外部依赖项的变更

- 用于提交影响构建系统的更改。
- 例如：build: 升级webpack到版本5


10. ci: 持续集成配置的变更

- 用于提交CI配置文件和脚本的修改。
- 例如：ci: 修改GitHub Actions配置文件


11. revert: 回滚

- 用于提交回滚之前的提交。
- 例如：revert: 回滚feat: 增加用户注册功能



