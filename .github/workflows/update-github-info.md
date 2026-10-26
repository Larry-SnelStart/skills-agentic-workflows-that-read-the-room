---
name: update-github-info
description: Updates the GitHub Info page from the GitHub Blog and Changelog and opens a pull request for Mona to review.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
engine:
  id: copilot
  copilot-sdk: true
tools:
  edit:
  web-fetch:
network:
  allowed:
    - defaults
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    title-prefix: "[github-info] "
    draft: true
---

# Update GitHub Info

Refresh the GitHub Info page with the latest updates from GitHub.

## Steps

1. Read `notes/mona-notes.md` and follow its guidance.
2. Use web-fetch to read https://github.blog/latest/.
3. Use web-fetch to read https://github.blog/changelog/.
4. Update `site/content/github-info.md` with short, practical summaries of relevant new items. Cite the GitHub Blog or GitHub Changelog as the source for each change.
5. If nothing meaningful changed, make no edits and do not open a pull request.
6. Otherwise, open a pull request with your changes for Mona to review. Never push directly to `main`.
