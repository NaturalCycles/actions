# Slack on failure

Simple slack failure notifier.

Features/caveats: 
* Designed to only be called if job failed (doesn't check failure status).
* Can be run in all branches (default) or only in specific branch specified with optional `branch` input param.
* Requires input: `channel`
* Requires input: `webhook-url`

Example usage:

```yaml
  dummy-job:
    name: dummy-job
    steps:
      - uses: actions/checkout@v3
      - <...steps>
      - uses: NaturalCycles/actions/commands/slack-on-failure@v1
        if: failure()
        with:
          channel: my-alert-channel
          webhook-url: ${{ secrets.SLACK_WEBHOOK_URL }}

```