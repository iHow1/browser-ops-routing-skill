# Examples

This directory contains short examples that show how to invoke the skill in real workflows.

## 中文示例

### 1. 登录后台前先分流

```text
使用 $browser-ops-routing 处理这个登录后的后台任务，先判断是否必须用浏览器；如果需要浏览器，再决定走结构化自动化还是视觉模式，并在提交前停下来确认。
```

### 2. 识别高风险动作

```text
使用 $browser-ops-routing 审查这个网页操作流程，指出哪些步骤应该直接执行，哪些步骤必须人工确认。
```

### 3. OpenClaw 浏览器策略

```text
Use $browser-ops-routing for this OpenClaw browser task and apply the OpenClaw-specific guidance from references/openclaw.md.
```

## English examples

### 1. Route a dashboard workflow

```text
Use $browser-ops-routing to handle this dashboard task, prefer API/CLI if possible, and only escalate to browser control if the workflow truly requires it.
```

### 2. Review a risky browser flow

```text
Use $browser-ops-routing to review this browser workflow and identify where human confirmation is required before login approval, posting, deletion, or payment.
```

### 3. Choose between structured and visual control

```text
Use $browser-ops-routing to decide whether this page should be handled with structured browser automation or visual browser control.
```
