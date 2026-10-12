---
name: update-github-info
description: Refresh Mona's GitHub Info page with useful updates from the GitHub Blog and Changelog.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
tools:
  edit: true
  web-fetch: {}
safe-outputs:
  create-pull-request:
    draft: false
    allowed-files:
      - site/content/github-info.md
network:
  allowed:
    - defaults
    - github.blog
    - github.com
---

# Update GitHub Info

## Task

1. Read `notes/mona-notes.md` before drafting any changes.
2. Use the web-fetch tool to read:
   - https://github.blog/latest/
   - https://github.blog/changelog/
3. Identify recent, factual updates that are useful to developers and fit Mona's editorial angle. Prefer practical information; do not repeat existing content or infer details not supported by the sources.
4. Update `site/content/github-info.md` with concise summaries and links to the relevant source pages. Preserve the existing themes and structure where practical.
5. If the file changed, submit the patch using the configured `create-pull-request` safe output. Open a pull request for Mona to review, with a clear title and a body summarizing the changes and linking to the source pages. Do not write directly to the default branch or use another write mechanism.

If there is no useful, non-redundant, verifiable update, leave the file unchanged and use `noop` with a brief explanation instead of opening an empty pull request.
