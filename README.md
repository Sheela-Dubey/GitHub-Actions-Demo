# GitHub Actions Cheat Sheet for Quality Engineers

A simple guide to help Quality Engineers (QEs) understand and use GitHub Actions for CI/CD and test automation.

## What is GitHub Actions?

GitHub Actions is a **CI/CD tool** built into GitHub that helps you automate workflows like:
- Running unit tests
- Linting code
- Building and deploying apps
- Running nightly regression tests

## Key Terms

| Term       | Description                                                                 |
|------------|-----------------------------------------------------------------------------|
| Workflow   | The automation file that defines what happens and when (`.yml` format)     |
| Event      | What triggers the workflow (e.g., `push`, `pull_request`, `schedule`)      |
| Job        | A collection of steps that run on the same environment (runner)            |
| Step       | A single task, like `run tests`, `checkout code`, or `install dependencies`|
| Runner     | The virtual machine that executes the job (Linux, Windows, macOS)          |
| Action     | A prebuilt or custom reusable task (e.g., `checkout@v4`)                   |

---

## 🛠 Getting Started

### 1. Prerequisites
- A GitHub repository
- `.github/workflows/` folder (create if it doesn't exist)

### 2. Create a Workflow File

File path: `.github/workflows/github-actions-demo.yml`

```yaml
name: GitHub Actions Demo

on: [push]

jobs:
  test-job:
    runs-on: ubuntu-latest

    steps:
      - name: Print Message
        run: echo "Workflow triggered by a push event."

      - name: Print OS
        run: echo "Running on: ${{ runner.os }}"

      - name: Print Branch
        run: echo "Branch: ${{ github.ref }}"

      - name: Checkout Code
        uses: actions/checkout@v4

      - name: List Files
        run: ls ${{ github.workspace }}
