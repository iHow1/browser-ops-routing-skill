# Browser Ops Routing

Browser Ops Routing is a lightweight skill for agent-driven browser work. It gives agents a simple execution policy:

- prefer `API/CLI` first
- use structured browser automation second
- use visual browser control only as a fallback
- require human confirmation for high-risk actions

It is designed for Codex, OpenClaw, and similar agent workflows where browser work needs to stay reliable, understandable, and safe.

## 中文介绍

`Browser Ops Routing` 是一个面向智能体网页操作的轻量级 skill。它的目标不是“让智能体无脑接管浏览器”，而是先做正确的分流：

- 优先走 `API/CLI`
- 其次走结构化浏览器自动化
- 视觉浏览器只作为兜底
- 遇到高风险动作必须停下来人工确认

这套规则适合 Codex、OpenClaw 以及类似的 agent 工作流，重点是提高网页任务的稳定性、可解释性和安全性。

## English Overview

This repository packages a reusable browser-routing policy rather than a product-specific setup.

It helps agents decide:

- when browser work is unnecessary
- when deterministic browser automation is enough
- when visual control is justified
- when the human must take over

## Included Files

- `SKILL.md`: shared routing policy
- `agents/openai.yaml`: UI metadata for skill pickers
- `references/openclaw.md`: OpenClaw-specific guidance that stays outside the core shared policy

## Design Principles

- Keep human and AI browser state separated.
- Use the least fragile layer that can complete the task.
- Treat login, publishing, deletion, payments, and verification as confirmation boundaries.
- Keep machine-specific setup outside the core skill.

## Suggested Uses

- browser-heavy agent workflows
- mixed API plus browser operations
- login-gated dashboards
- anti-bot-fragile web tasks
- OpenClaw or Codex browser policy standardization

## Scope

This repository intentionally ships a generic policy layer.

It does not include:

- machine-specific ports or paths
- browser-brand-specific personal preferences
- private environment fixes
- CAPTCHA bypass logic

## License

MIT
