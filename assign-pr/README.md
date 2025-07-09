# 🔧 assign-pr

A reusable GitHub Action that automatically assigns one or more users to a pull request when it is opened.

---

## 📦 Features

- Assigns one or more GitHub usernames to new pull requests
- Accepts a comma-separated list of assignees
- Minimal setup — works in any repository

---

## 🚀 Usage

In the consuming repository, add a workflow like:

```yaml
name: Auto Assign PR

on:
  pull_request:
    types: [opened]

jobs:
  assign:
    runs-on: ubuntu-latest
    steps:
      - uses: kamalteja/git-actions/assign-pr@v1
        with:
          assignees: kamalteja,alice,bob
```
