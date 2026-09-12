---
name: Diagnostic gh-aw native Auto
on:
  push:
    branches:
      - diagnostic-ghaw-native
    paths:
      - .github/workflows/diagnostic-ghaw-native.md
      - .github/workflows/diagnostic-ghaw-native.lock.yml

strict: false
timeout-minutes: 5

permissions:
  contents: read

engine:
  id: copilot
  version: "1.0.83"
  model: copilot/auto
  bare: true
  args:
    - --deny-tool
    - "*"

features:
  dangerously-disable-sandbox-agent: true

sandbox:
  agent: false

tools:
  github: false
  bash: false
  edit: false
  cli-proxy: false

safe-outputs:
  staged: true
  threat-detection: false
  report-failure-as-issue: false
  noop:
    report-as-issue: false
---

Reply with exactly OK.
Do not call any tools.
Do not read files, browse websites, execute commands, or modify anything.
This is only a model connectivity test.
