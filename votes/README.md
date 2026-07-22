# votes/

Deze map wordt gevuld door de `process-vote`-workflow (`.github/workflows/process-vote.yml`),
nooit rechtstreeks door een pull request. Elk bestand hier komt uit een goedgekeurde stem-issue.

Structuur:

```
votes/
  home-assistant/<component>/<versie>/<github-username>.json
  home-assistant/<component>/<versie>/_verdict.json
  hacs/<owner>/<repo>/<versie>/<github-username>.json
  hacs/<owner>/<repo>/<versie>/_verdict.json
  devices/<merk>/<model>/<versie>/<github-username>.json
  devices/<merk>/<model>/<versie>/_verdict.json
  apps/<app-slug>/<versie>/<github-username>.json
  apps/<app-slug>/<versie>/_verdict.json
```

Zie de root-README voor uitleg van het systeem.
