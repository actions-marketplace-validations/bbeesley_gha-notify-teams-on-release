# gha-notify-teams-on-release
Github Action to notify a teams channel when a release is created
## Details

This is a single workflow step to send a message to an MS Teams channel when a release is created. You'll need to set up the webhook connection in teams to get the teams webhook url, then pass that to the action as an input.

## Options

| name         | description                                | required | default |
| ------------ | ------------------------------------------ | -------- | ------- |
| webhook-link | Teams webhook link to send notification to | true     |         |

## Example Workflow

```yaml
name: notify-teams-on-release
on:
  release:
    types: [published]
concurrency: '1'
jobs:
  notify:
    runs-on: ubuntu-latest
    timeout-minutes: 5
    steps:
      - uses: bbeesley/gha-notify-teams-on-release@main
        with:
          webhook-link: ${{ secrets.TEAMS_RELEASE_WEBHOOK_LINK }}
```
