---
name: commit
description: SVN commit with custom message prefix
---

# /commit - SVN 提交命令

当用户执行svn `/commit` 时，请按以下流程执行：

## 流程

1. **询问前缀** — 先问用户 commit message 要以什么开头（例如 `[任务]`、`[bug]`、`[优化]`、`[重构]` 等），让用户输入前缀文本

2. **查看改动** — 运行 `svn status` 和 `svn diff` 查看当前有哪些文件被修改、新增或删除

3. **更新代码** — 执行 `svn update` 更新工作副本。若出现冲突，先解决冲突并向用户说明冲突内容和解决方式，让用户确认后再继续后续步骤。

4. **生成 message** — 根据改动的具体内容，生成一条详细的 commit message，格式为：`[用户指定的前缀] 具体改动描述`
   - 描述应该简洁但信息丰富，列出改动的关键点
   - 如果改动涉及多个模块，可以用逗号分隔列出

5. **用户确认** — 把生成的完整 commit message 展示给用户确认

6. **执行提交** — 用户确认后，执行 `svn commit -m "完整message"`

7. **重新修改** — 如果用户不满意，重新修改直到用户确认为止