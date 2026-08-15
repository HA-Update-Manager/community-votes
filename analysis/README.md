# analysis/

This directory is populated by the `analyze-voters` workflow
(`.github/workflows/analyze-voters.yml`), on a daily schedule (also
runnable on demand via workflow_dispatch), never directly by a pull
request.

`voters.json` is a repo-wide, plain, public JSON file (same reading model as
`votes/`: readable directly via `raw.githubusercontent.com`, no account or
API rate limit needed), one entry per person who has ever voted, anywhere in
this repo:

```json
{
  "generated_at": "...",
  "voters": [
    {
      "username": "...",
      "total_votes": 12,
      "healthy_votes": 10,
      "problematic_votes": 2,
      "agreements": 9,
      "contradictions": 1,
      "reliability_score": 0.9,
      "first_vote_at": "...",
      "last_vote_at": "..."
    }
  ]
}
```

Sorted by `total_votes`, most active first.

**How `agreements`/`contradictions`/`reliability_score` are worked out**: for
every jump someone voted on, look at every *other* voter's own verdict on
that same jump, weighted the same way a jump's own `verdict` in `votes/`
already is (see the root README's Configuration section). If the weighted
majority of everyone else agrees with this person's verdict, that's an
agreement; if it disagrees, that's a contradiction. A tie among the others
(including being the only voter on that jump) carries no signal either way,
so it's skipped rather than counted as either. `reliability_score` is
`agreements / (agreements + contradictions)`, `null` if there's no
comparable jump yet.

Someone who often votes "problematic" while most other voters on the same
jump say "healthy" scores low here; someone whose verdict usually matches
what everyone else independently concluded scores high.

**What this is for**: nothing in this repo or in ha-update-manager reads
this file yet. It exists to collect the signal now, so it's already there
once there's a concrete use for it (e.g. as inspiration for picking a
trusted voter). Not a ranking of who's "right": a low score can just as
easily mean someone tends to catch real problems early, before the rest of
the community has caught up.
