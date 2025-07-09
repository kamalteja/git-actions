# 🐳 validate-compose

A lightweight GitHub Action to validate all your Docker Compose files using `docker compose config`.

---

## ✅ What it Does

- Finds all matching Compose files:
  - `docker-compose.yml`
  - `docker-compose.override.yml`
  - `docker-compose.dev.yml`, etc.
- Runs `docker compose -f FILE config` on each file
- Fails if any Compose file is invalid

---

## 🚀 Usage

```yaml
name: Validate Compose Files

on:
  push:
  pull_request:

jobs:
  validate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - uses: docker/setup-buildx-action@v3

      - name: Validate Compose files
        uses: kamalteja/git-actions/validate-compose@v1
