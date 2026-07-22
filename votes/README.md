# votes/

This directory is populated by the `process-vote` workflow
(`.github/workflows/process-vote.yml`), never directly by a pull request.
Every file here comes from an approved vote issue.

Structure:

```
votes/
  home-assistant/<component>/<version>/<github-username>.json
  home-assistant/<component>/<version>/_verdict.json
  hacs/<owner>/<repo>/<version>/<github-username>.json
  hacs/<owner>/<repo>/<version>/_verdict.json
  devices/<manufacturer>/<model>/<version>/<github-username>.json
  devices/<manufacturer>/<model>/<version>/_verdict.json
  apps/<app-slug>/<version>/<github-username>.json
  apps/<app-slug>/<version>/_verdict.json
```

See the root README for an explanation of the whole system.
