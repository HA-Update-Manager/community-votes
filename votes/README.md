# votes/

This directory is populated by the `process-vote` workflow
(`.github/workflows/process-vote.yml`), never directly by a pull request.
Every file here comes from an approved vote issue.

One flat JSON file per destination version, holding every jump (every
distinct version people upgraded *from*) that's been rated for it, and every
voter's own entry within that jump:

```
votes/
  home-assistant/<component>/<to-version>.json
  hacs/<owner>/<repo>/<to-version>.json
  devices/<manufacturer>/<model>/<to-version>.json
  apps/<app-slug>/<to-version>.json
```

Each file's shape:

```json
{
  "jumps": {
    "<from-version>": {
      "votes": {
        "<github-username>": {
          "verdict": "healthy",
          "reason_category": null,
          "notes": null,
          "link": null,
          "weight": 1,
          "created_at": "...",
          "updated_at": null
        }
      },
      "verdict": {
        "healthy_count": 1,
        "problematic_count": 0,
        "quorum": 3,
        "quorum_reached": false,
        "auto_install_eligible": false,
        "updated_at": "..."
      }
    }
  }
}
```

One file per destination version, not one per jump or one per voter: a
dialog reviewing a specific pending update always already knows the
destination version, but not which jumps have been rated for it, so a single
fetch of this one file answers both "how did my own jump go" and "how did
other jumps landing here go" at once. Deliberately not merged one level
further (e.g. one file per repo covering every version ever released) --
that would mean fetching a repo's entire multi-year vote history just to
render one pending update.

See the root README for an explanation of the whole system.
