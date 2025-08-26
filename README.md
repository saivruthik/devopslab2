name: Generate Snake Animation

on:
  schedule:
    - cron: "0 0 * * *" # Runs daily
  workflow_dispatch:

jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      - name: Generate Snake Animation
        uses: Platane/snk@master
        with:
          github_user_name: venupagilla2004
          outputs: dist/github-snake.svg
      - name: Commit and Push Snake SVG
        run: |
          git config --global user.name "github-actions[bot]"
          git config --global user.email "github-actions[bot]@users.noreply.github.com"
          git add dist/github-snake.svg
          git commit -m "Updated GitHub Contribution Snake"
          git push
