---
name: update-github-info
description: Draft concise website updates for Mona from official GitHub sources.
engine:
  id: copilot
  model: copilot/mai-code-1.1-flash
strict: true
on:
  workflow_dispatch:
  schedule:
    - cron: '17 9 * * *'
permissions:
  contents: read
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    title-prefix: '[Mona] '
    draft: true
    fallback-as-issue: false
    allowed-files:
      - site/content/github-info.md
sandbox:
  agent:
    model-fallback: false
    token-steering: false
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` first and follow its guidance.

Consult both official sources:

- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/
- Awesome Copilot workflows: https://awesome-copilot.github.com/workflows/

Fetch the Awesome Copilot workflows page and consider relevant, practical
information from it for Mona's website. Include a source link for any factual
update based on that page.

Use the `edit` tool to update only `site/content/github-info.md`. Add relevant,
concise, practical information that helps developers learn GitHub faster. Include
source links for every factual update, using the specific GitHub Blog or GitHub
Changelog URL that supports it. Do not modify any other file.

When there are worthwhile, evidence-backed changes, use the configured
`safe-outputs` `create-pull-request` output to open a draft pull request for Mona.
Use a title that mentions Mona or GitHub Info. In the pull request body, summarize
the proposed changes, list the source links, and explain why each update belongs
in the site. Never write directly to `main`; make all changes through the draft
pull request. Leave the pull request open for human review.

If no relevant updates are found, make no file changes and do not create a pull
request.