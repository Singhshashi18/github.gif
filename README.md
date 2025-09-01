
name: Generate Snake

on:
  schedule:
    - cron: "0 0 * * *"
  workflow_dispatch:

jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repo
        uses: actions/checkout@v3

      - name: Generate Snake SVG
        uses: Platane/snk@v3
        with:
          github_user_name: Singhshashi18
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark

      - name: Debug: List dist folder contents
        run: ls -la dist

      - name: Push Snake Files to GitHub
        uses: EndBug/add-and-commit@v9
        with:
          author_name: github-actions
          author_email: github-actions@github.com
          message: "Generate GitHub contribution snake"
          add: "dist/*"
          cwd: .





