# community-votes

A shared, git-based voting system: has a specific update to a Home Assistant
integration, device firmware, app, or Home Assistant itself turned out to be
**healthy** or **problematic**? Built for
[ha-update-manager](https://github.com/HA-Update-Manager/ha-update-manager),
but usable by anyone.

**Important: this is a collected opinion, not a guarantee.** A "healthy"
verdict means the people who voted so far didn't run into problems, not that
an update is guaranteed to be healthy for your specific setup. Be extra
careful with safety-relevant devices (locks, alarms, smoke detectors): a
community verdict never replaces your own judgment.

"Healthy"/"problematic" is about whether an update works as expected (no
bugs, no missed minimum HA version, no accidentally pushed dev build, no
unannounced breaking change), not about security or safety in a broader
sense.

## How to vote

Open a new issue via the "Cast a vote" form
([direct link](../../issues/new?template=vote.yml)). Fill in only the fields
that belong to the category you pick. A GitHub Action processes your vote
automatically: the corresponding file appears under `votes/`, and the issue
closes with a confirmation.

No account linking beyond a regular GitHub login is needed: this repo
requires no fork and no separate app installation on your side.

A verdict is about a specific jump: the version you upgraded *from*, and the
one you landed on, not just the destination version alone. Going from 0.1.0
to 3.5.2 (possibly skipping several breaking changes along the way) can carry
very different risk than going from 3.5.1 to 3.5.2, even though both land on
the same version -- so both fields are required. You can vote once per person
per exact jump. A second vote on the same jump overwrites your previous one
(its own `created_at` is preserved, only `updated_at` moves).

## Reading

Every file under `votes/` is a plain, public JSON file, readable directly via
`raw.githubusercontent.com`, no account or API rate limit needed. One file per
destination version holds every jump (every distinct `from_version`) that's
been rated for it, and every voter's own entry within that jump -- see
`votes/README.md` for the exact structure.

## Moderation

`moderation/banned-users.json` lists GitHub usernames whose votes are no
longer processed. Only changed by the organization owners, outside the
regular voting flow. Report abuse via a comment on the relevant vote issue
(before it auto-closes) or a new issue against this repo.

## Configuration

`config/site.json` holds the quorum (minimum number of healthy votes before
an update counts as "eligible for automatic installation"). See
`ha-update-manager`'s own `FUTURE.md` for the full background on this
requirement (100% healthy, plus quorum).

## Tone

This is a collection of user opinions, not a judgment of a project or its
maintainer. Keep any problem report as factual and helpful as possible.
