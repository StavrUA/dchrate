# DisChargeRate

`dchrate` (or `DisChargeRate`) is a [SwiftBar](https://swiftbar.app/) plugin for macOS. Copy
one of the scripts into SwiftBar's plugin folder, for example:

```sh
~/Documents/SwiftBar\ Plugins
```

and make it executable:

```sh
chmod +x dchrate.5m.py
```

The plugin samples `pmset -g batt` and stores the history in
`~/Library/Application Support/SwiftBar/dchrate-history.json`. It removes samples older than 30 days.
While discharging, the menu bar displays the average rate as `X%/hr` (for example, `4.2%/hr`).
The average is calculated from the oldest and newest discharging samples in the rolling 30-day window;
`--%/hr` is shown until enough samples exist. When charging, it shows `🔌`.

Set `DCHRATE_HISTORY_FILE` to override the history location, which is useful
for testing or backing up the data.

## Manual refresh

The menu contains a `Refresh now` item. Clicking it calls SwiftBar's refresh action, so the plugin updates immediately without waiting for the 5-minute interval.

## Faster updates

SwiftBar decides the refresh interval from the filename suffix:

- `dchrate.5m.py` — updates every 5 minutes
- `dchrate.30s.py` — updates every 30 seconds
- `dchrate.1m.py` — updates every minute

If you want the battery value to react faster when plugging/unplugging the charger, use a shorter interval such as `dchrate.30s.py` instead of `dchrate.5m.py`.

Example:

```sh
cp dchrate.30s.py ~/Documents/SwiftBar\ Plugins/dchrate.30s.py
chmod +x ~/Documents/SwiftBar\ Plugins/dchrate.30s.py
```

This works because SwiftBar reads the filename suffix and refreshes the plugin based on that interval.
