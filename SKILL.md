---
name: browser-ops-routing
description: Route browser work across API/CLI, structured browser automation, visual browser control, and human confirmation. Use when tasks involve reading web content, logging into sites, operating dashboards, handling anti-bot friction, or deciding between direct browser control and safer non-browser paths in Codex, OpenClaw, or similar agent workflows.
---

# Browser Ops Routing

Use this skill when browser work needs consistent routing and risk control.

## Core policy

- Humans use their primary daily browser.
- AI uses a dedicated isolated browser or browser profile.
- Never share human and AI browser profiles.
- Prefer the least fragile path that can complete the task.

## Default routing order

1. `API/CLI`
2. Structured browser automation
3. Visual browser control
4. Human confirmation

Only escalate when the previous layer cannot reliably complete the task.

## Layer selection

### 1. API/CLI first

Use for:

- public web content retrieval
- Git hosting, mail metadata, logs, dashboards with APIs
- exports, search, structured queries
- repeatable data collection

Prefer this layer when:

- an official API exists
- a stable CLI exists
- the page is only a presentation shell over structured data

Do not switch to browser control unless:

- the needed data is only visible after page rendering
- the flow requires real page interaction
- auth or session state only exists in-browser

### 2. Structured browser automation

Use for:

- stable admin panels
- repeated form filling
- uploads, filters, table actions, exports
- sites with reliable selectors and predictable flows

Prefer this layer before visual control.

Escalate to visual control when:

- selectors break repeatedly
- the page is canvas-heavy or drag-heavy
- a rich text editor or nested modal flow blocks reliable DOM automation
- anti-bot friction makes deterministic automation brittle

### 3. Visual browser control

Use for:

- visually complex web apps
- frequent layout changes
- rich editors, canvas tools, design tools
- sites where "look then click" is more reliable than selectors

Use this as a fallback, not the default.

Stop and hand back to the human when:

- CAPTCHA appears
- SMS, email, or 2FA verification is required
- the site shows account risk or anti-abuse warnings
- the next action is irreversible or externally visible

### 4. Human confirmation

Always stop for confirmation before:

- first-time login or OAuth approval
- entering verification codes
- posting, publishing, sending, or submitting
- deleting, overwriting, or changing security settings
- payments, checkout, billing, or subscription changes
- any action likely to trigger platform review or account risk

## Browser separation rules

For local desktop workflows:

- Keep human browsing in the primary daily browser.
- Keep AI browsing in a dedicated isolated browser or profile.
- Reuse the AI browser profile for persistent login state.
- If available, prefer attaching to an already-running AI browser over launching a fresh interactive browser for each task.

## Product-specific implementation

Keep the shared policy in this file generic.

- For OpenClaw-specific browser guidance, read `references/openclaw.md`.
- For local product-specific setup, add a separate reference file instead of editing this core routing policy.

## Anti-bot and verification handling

- Do not treat visual control as a CAPTCHA bypass tool.
- If anti-bot friction appears, reduce automation aggressiveness and hand off verification to the human.
- After verification, resume from the AI browser profile that now holds the authenticated session.

## Failure fallback

- `API/CLI` fails -> try structured browser automation
- structured browser automation fails -> try visual control
- visual control hits verification or irreversible action -> stop for human confirmation

Do not jump straight to visual control without a reason.

## Output expectations

When operating under this skill:

- state which layer is being used
- state why escalation happened when moving to a higher layer
- pause clearly before high-risk actions
- keep summaries short and operational

## Environment notes

- Machine-specific certificate, proxy, or enterprise TLS issues are environment problems, not routing logic.
- Keep those notes out of the core workflow unless they directly affect the current run.
