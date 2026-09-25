# dchrate

`dchrate.5m.py` is a [SwiftBar](https://swiftbar.app/) plugin for macOS. Copy
the script into SwiftBar's plugin folder and make it executable:

```sh
chmod +x dchrate.5m.py
```

The plugin samples `pmset -g batt` every five minutes, stores samples in
`~/Library/Application Support/SwiftBar/dchrate-history.json`, and removes
samples older than 30 days. While discharging, the menu bar displays the
average rate as `X%/hr` (for example, `4.2%/hr`). The average is calculated
from the oldest and newest discharging samples in the rolling 30-day window;
`--%/hr` is shown until enough samples exist.

Set `DCHRATE_HISTORY_FILE` to override the history location, which is useful
for testing or backing up the data.