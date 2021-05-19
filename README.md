# Visit https://github.com/lowlighter/metrics/blob/master/action.yml for full reference
name: Metrics
on:
  # Schedule updates (each hour)
  schedule: [{cron: "0 * * * *"}]
  # Lines below let you run workflow manually and on each commit
  workflow_dispatch:
  push: {branches: ["master", "main"]}
jobs:
  github-metrics:
    runs-on: ubuntu-latest
    steps:
      - uses: lowlighter/metrics@latest
        with:
          # Your GitHub token
          token: ${{ secrets.METRICS_TOKEN }}

          # Options
          user: Bram1903
          template: classic
          base: header, activity, community, repositories, metadata
          config_timezone: Europe/Amsterdam
          plugin_achievements: yes
          plugin_achievements_secrets: yes
          plugin_achievements_threshold: C
          plugin_languages: yes
          plugin_languages_colors: github
          plugin_languages_limit: 8
          plugin_languages_threshold: 0%
          plugin_lines: yes
