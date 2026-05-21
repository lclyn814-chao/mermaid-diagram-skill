---
name: mermaid-diagram
description: Use when you need to visualize product flows, business logic, page navigation, system architecture, or any process as a Mermaid diagram. Triggers on natural language descriptions or existing requirement documents.
---

# Mermaid Diagram

## Overview

将自然语言需求或文档转换为 Mermaid 流程图/架构图，保存为 `.md` 文件供开发和产品使用。

## 输入方式

两种输入都支持：

- **自然语言**：直接描述需求，如"用户登录后如果有账号跳首页，没有去注册"
- **文件路径**：读取 PRD 或需求文档，如"读取 docs/prd.md"

输入不够清晰时，先问一个最关键的问题，不要猜测。

## 图类型选择

根据需求自动判断，无需用户指定：

| 场景 | 图类型 |
|------|--------|
| 页面跳转、用户路径 | `flowchart TD` |
| 业务逻辑、判断分支、状态变化 | `flowchart LR` |
| 接口调用、时序、系统交互 | `sequenceDiagram` |
| 模块关系、系统架构、数据流 | `graph TD` |

用户说"改成时序图"等指令时，立即切换图类型重新生成。

## 执行步骤

1. 读取输入（自然语言或文件）
2. 判断图类型，如不确定先问用户
3. 生成 Mermaid 代码
4. 保存文件到 `docs/diagrams/YYYY-MM-DD-<主题>.md`
5. 告知文件路径 + 说明选择了哪种图类型及原因

## 输出文件格式

```markdown
# <主题>

> 图类型：flowchart TD | 生成时间：YYYY-MM-DD

```mermaid
...
```

## 节点说明

- **节点名**：含义说明
```

## 节点命名规范

- 用中文标注节点，保持与需求语言一致
- 判断节点用问句，如"已登录?"
- 终态节点标注"结束"或具体页面名

## 常见错误

- 节点 ID 不能有空格，用下划线：`user_login` 而非 `user login`
- `sequenceDiagram` 中参与者名称避免中文空格
- 嵌套子图用 `subgraph`，不要用多个独立图拼接
