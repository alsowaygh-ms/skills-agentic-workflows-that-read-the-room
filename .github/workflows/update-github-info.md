---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:
engine:
  id: copilot
  copilot-sdk: true
tools:
  edit:
  web-fetch:
permissions:
  contents: read
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    max: 1
    draft: false
    fallback-as-issue: false
    allowed-files:
      - site/content/github-info.md
---

# Update GitHub Info

Read `notes/mona-notes.md` and `site/content/github-info.md` before researching or editing.

Use `web-fetch` to read these sources:

- https://github.blog/latest/
- https://github.blog/changelog/
- https://awesome-copilot.github.com/workflows/

Identify recent, verifiable developments that are useful to developers and relevant to the site's existing themes. Do not infer details that the sources do not state. If any source cannot be fetched, or there is no meaningful update, make no changes and do not open a pull request.

Update only `site/content/github-info.md` with concise, practical additions or corrections. Do not edit workflow files or any other repository files. Preserve its existing structure and editorial angle, avoid duplicating existing material, and link each source-based change to its specific source page.

Never write, push, or merge directly to `main`. After making a meaningful change, use the `create-pull-request` safe output once to open a pull request for Mona to review. The pull request should summarize the changes and cite the source pages. Do not merge it.
