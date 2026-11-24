# firmware-versions/

This directory is populated by the `process-firmware-version` workflow
(`.github/workflows/process-firmware-version.yml`), never directly by a pull
request. Every entry comes from an approved firmware-version submission.

Unlike `votes/`, this isn't an opinion that can legitimately change over
time -- a raw Zigbee OTA integer is intrinsic to the exact firmware binary it
names, so it always maps to the same real, human-readable version string
everywhere. A submission that conflicts with an already-recorded value is
rejected, never silently overwritten.

One flat JSON file per device model, mapping every raw OTA integer known for
it to its real version string:

```
firmware-versions/
  <manufacturer>/<model>.json
```

Each file's shape:

```json
{
  "<raw-ota-integer>": "<real-version-string>",
  "16784654": "1.93.7",
  "16786436": "1.164.2"
}
```

One file per model, not one per raw integer (unlike `votes/devices/`'s own
per-destination-version files): a consuming instance wants every known
mapping for a model in one request, not one request per raw integer it
happens to encounter over time as a device keeps updating.

See the root README for an explanation of the whole system.
