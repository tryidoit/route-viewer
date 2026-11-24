# Route Viewer

A single-file viewer for location logs. Open `index.html`, drop in a file, and browse your routes on a map. Nothing is uploaded; only map tiles are fetched from the internet.

Live: https://tryidoit.github.io/route-viewer/

The original, feature-heavy version lives on the `original` branch.

## Features

- Day-by-day browsing with a Days / Stops / Places panel
- Route colored by speed for a single day, overview of all days
- Replay a day with a scrubber and adjustable speed
- Stops are decluttered by zoom, so big histories stay readable
- Export the current view as GPX, or its stops as CSV
- Light and dark themes

## Data format

A plain text file (`.txt`, `.csv` or `.log`), one reading per line, comma-separated:

```
date time, label, id, latitude, longitude, address
```

```
2025-03-14 08:15:03,Phone,1,37.774929,-122.419418,1 Market St, San Francisco, CA
2025-03-14 08:15:33,Phone,1,37.775110,-122.418700,Market St, San Francisco, CA
```

| Field | Notes |
| --- | --- |
| date time | `YYYY-MM-DD HH:MM:SS` (a `T` works too, fractional seconds OK). Local time. |
| label, id | Any text without commas. Ignored, but both must be present. |
| latitude, longitude | Decimal degrees. |
| address | Optional, may contain commas. |

Lines that don't match (headers, blanks) are skipped. Readings are sorted by time automatically. The app shows this format in a popup on first launch and whenever a file can't be read.
