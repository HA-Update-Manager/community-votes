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

Use the vote buttons in the Home Assistant integration.

A verdict is about a specific jump: the version you upgraded *from*, and the
one you landed on, not just the destination version alone. Going from 0.1.0
to 3.5.2 (possibly skipping several breaking changes along the way) can carry
very different risk than going from 3.5.1 to 3.5.2, even though both land on
the same version, so both fields are required. You can vote once per person
per exact jump. A second vote on the same jump overwrites your previous one
(its own `created_at` is preserved, only `updated_at` moves).

## Reading

Every file under `votes/` is a plain, public JSON file, readable directly via
`raw.githubusercontent.com`, no account or API rate limit needed. One file per
destination version holds every jump (every distinct `from_version`) that's
been rated for it, and every voter's own entry within that jump, see
`votes/README.md` for the exact structure.

## Firmware versions

A second, unrelated system lives in this same repo: a crowd-sourced mapping
from a raw Zigbee OTA integer (what Zigbee itself reports, e.g. `16786436`)
to its real, human-readable firmware version (what a vendor's own site shows
for the same firmware, e.g. `1.164.2`). There's no reliable way to decode
one into the other, so this exists purely to remember an observed fact once
it's known. Unlike a vote, this isn't an opinion: the same raw integer always
means the same real version everywhere, so a submission that conflicts with
an already-recorded value is rejected rather than overwritten.

Submitted automatically by ha-update-manager itself, via the same linked
GitHub account already used for voting (no additional permission),not
something to fill in by hand. The "Report a real firmware version" form
exists purely as the mechanism that automatic submission goes through, not
as an invitation to submit one yourself. See `firmware-versions/README.md`
for the exact structure.

## Moderation

`moderation/banned-users.json` lists GitHub usernames whose votes are no
longer processed. Only changed by the organization owners, outside the
regular voting flow. Report abuse via a comment on the relevant vote issue
(before it auto-closes) or a new issue against this repo.

## Configuration

`config/site.json` holds the quorum: the minimum number of healthy votes a
jump needs before it counts as having enough signal to be trusted at scale.
Each jump's own `verdict` (see `votes/README.md`) exposes `quorum`,
`quorum_reached`, and `auto_install_eligible` (no problematic votes at all,
and the healthy count has reached quorum) so any consuming tool can decide
for itself whether and how to act on that signal, this repo only tracks
and exposes the numbers, it doesn't install anything itself.

## Analysis

`analysis/voters.json` is a repo-wide, automatically kept up to date view
of who's voted, how active they are, and how often their verdict matches
what everyone else independently concluded on the same jump. See
`analysis/README.md` for the exact shape and how that's worked out. Not
consumed anywhere yet; collected as future inspiration for picking a
trusted voter.

## Tone

This is a collection of user opinions, not a judgment of a project or its
maintainer. Keep any problem report as factual and helpful as possible.
