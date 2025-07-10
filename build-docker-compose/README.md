# 🐳 build-compose

A reusable GitHub Action that builds services defined in one or more `docker-compose` files using `docker compose build`.

Use this action in your CI pipelines to catch build-time issues early, such as Dockerfile syntax errors, broken `COPY` statements, or missing dependencies.

---

## ✅ Features

- Accepts a **JSON array** of Compose file paths
- Runs `docker compose -f <file> build` on each file
- Fails fast if any build fails
- Helps validate that your services compile and build correctly

---

## 🚀 Usage

You can use this action by providing a JSON array of `docker-compose` file paths manually or from another step:

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: docker/setup-buildx-action@v3

      - name: Build Compose services
        uses: kamalg/github-actions/build-compose@v1
        with:
          files: |
            ["apps/api/docker-compose.yml", "services/db/docker-compose.dev.yml"]
