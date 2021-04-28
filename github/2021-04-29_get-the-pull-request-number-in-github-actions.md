---
title: Get the Pull Request Number in Github Actions
createdAt: 2021-04-28T16:02:36Z
---

# Get the Pull Request Number in Github Actions

- If you use `${{github.event.number}}` you will get the PR number on pull request event.
- If you use `${{github.event.issue.number}}` you will get the PR number on any issue event e.g. updates.

https://github.com/actions/checkout/issues/58#issuecomment-812259610