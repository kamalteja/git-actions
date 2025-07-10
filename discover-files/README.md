# 📂 discover-files

A reusable GitHub Action that finds files in your repository using glob patterns and outputs the result as a **JSON array**. Perfect for workflows where you want to process specific files (like Docker Compose files, YAMLs, configs) without duplicating file discovery logic.

---

## 🚀 Features

- Accepts one or more glob patterns (e.g. `**/docker-compose.yml`)
- Outputs matched file paths as a JSON array
- Can optionally fail if no files are found
- Designed for reusability and modular workflows

---

## 📦 Inputs

| Name            | Description                            | Required | Default |
|-----------------|----------------------------------------|----------|---------|
| `patterns`       | Multiline glob patterns to match files | ✅       | —       |
| `fail-on-empty`  | Fail if no files are found             | ❌       | `true`  |

> Uses Bash globbing with `globstar` enabled (e.g. `**/*.yml` works).

---

## 📤 Outputs

| Name   | Description                      |
|--------|----------------------------------|
| `files`| JSON array of matched file paths |

Example:
```json
["apps/web/docker-compose.yml", "services/api/docker-compose.override.yml"]
```

## 🚀 Usage

To use the `discover-files` action in your workflow, add a step like this:

```yaml
- name: Discover files
  id: discovery
  uses: kamalteja/git-actions/discover-files@v10
  with:
    patterns: |
      **/docker-compose.yml
      **/docker-compose.*.yml
    fail-on-empty: true
```

You can then use the output (a JSON array of file paths) in subsequent steps:

```yaml
- name: Print matched files
  run: |
    echo "Matched files:"
    echo '${{ steps.discovery.outputs.files }}' | jq -r '.[]'
```
