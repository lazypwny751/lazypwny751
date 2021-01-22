# Visit https://github.com/lowlighter/metrics/blob/master/action.yml for full reference
name: Metrics
on:
  # Schedule updates
  schedule: [{cron: "0 * * * *"}]
  # Lines below let you run workflow manually and on each commit
  push: {branches: ["master", "main"]}
  workflow_dispatch:
jobs:
  github-metrics:
    runs-on: ubuntu-latest
    steps:
      - uses: lowlighter/metrics@latest
        with:
          # Your GitHub token
          token: ${{ secrets.METRICS_TOKEN }}
          # GITHUB_TOKEN is a special auto-generated token restricted to current repository, which is used to push files in it
          committer_token: ${{ secrets.GITHUB_TOKEN }}

          # Options
          user: lazypwny751
          template: terminal
          base: header, activity, community, repositories, metadata
          config_animated: yes
          config_timezone: Europe/Istanbul
          plugin_activity: yes
          plugin_activity_days: 14
          plugin_activity_filter: all
          plugin_activity_limit: 5
          plugin_isocalendar: yes
          plugin_isocalendar_duration: full-year
          plugin_languages: yes
          plugin_languages_ignored: bash
          plugin_pagespeed: yes
          plugin_pagespeed_url: https://github.com/lazypwny751
