# OpenClaw implementation notes

Use this reference only when the task needs to map the shared browser-routing
policy onto OpenClaw's browser stack.

## Preferred browser lanes

- Default recommendation: use the isolated managed browser profile.
- Use the extension relay only when the task explicitly requires taking over an
  already-open system browser tab.
- If the workflow needs a persistent AI-owned login state in a real browser, a
  dedicated browser profile with CDP attach is acceptable and follows the same
  separation model as Codex.

## Why not default to Browser Relay

Browser Relay is useful, but it adds extra moving parts:

- extension installation
- relay reachability
- tab attachment state
- token and auth checks

That makes it a weaker default when the goal is stable, repeatable browser
automation.

## Browser profile guidance

- managed profile: isolated browser, best default for OpenClaw-native runs
- extension relay profile: only for takeover-style use
- remote or dedicated CDP: acceptable when a real persistent browser session is
  intentionally part of the workflow

## Model note

The routing choice is mostly a browser-control architecture choice, not a model
choice.

Use the same policy:

- API/CLI first
- structured browser automation second
- visual control third
- human confirmation for high-risk actions
