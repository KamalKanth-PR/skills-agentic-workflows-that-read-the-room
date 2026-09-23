---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:

permissions:
  contents: read

engine: copilot

tools:
  edit:
  web-fetch:

network:
  allowed:
    - github.blog
    - github.com

safe-outputs:
  create-pull-request:
    title-prefix: "[github-info] "
    labels: [automation, github-info]
    draft: true
---

# Update GitHub Info

Keep the GitHub Info website up to date with the latest GitHub Blog and Changelog stories.

## Steps

1. Read [notes/mona-notes.md](notes/mona-notes.md) for Mona's editorial angle and preferences.
2. Fetch `https://github.blog/latest/` for the latest GitHub Blog posts.
3. Fetch `https://github.blog/changelog/` for the latest GitHub Changelog entries.
4. Update [site/content/github-info.md](site/content/github-info.md) with a short, practical summary of the newest and most relevant stories, following Mona's notes (keep it concise, developer-focused, and cite the source blog or changelog entry).
5. Open a pull request with the changes so Mona can review them before anything goes live. Do not push directly to the default branch.
