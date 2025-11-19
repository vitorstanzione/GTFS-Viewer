<p align="center">
  <a href="https://gtfs.stanzione.com.br/" target="_blank"><strong>▶ Click here for a deployed page</strong></a>
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/vitorstanzione/GTFS-Viewer/main/favicon/android-chrome-512x512.png" width="128">
</p>

# GTFS Viewer (Pure HTML)

A lightweight, browser-only static GTFS viewer that loads standard GTFS `.txt` files so you can visualize tables, filter, sort, and more — no server, no build step, just open the HTML file.

> **Why?** Sometimes you just want to inspect GTFS feeds quickly without installing tooling or spinning up a backend.

## Features
- 🔍 View static GTFS tables directly in your browser
- 🔄 Client-side filtering and single-column sorting on every table
- 📁 Works with individual `.txt` files or a `.zip` of a GTFS feed
- 📊 “OD time table” view (requires `routes.txt`, `trips.txt`, and `stop_times.txt`)
- 🎨 Route/brand colors rendered from `route_color` / `route_text_color` when valid
- 🔗 Clickable URLs where present (e.g., `route_url`, `agency_url`)
- 💾 Export current view to CSV / JSON / clipboard

## What it loads
At minimum, the app can show any static GTFS table you provide. Some features need specific files:

- **Core tables supported:** `agency.txt`, `stops.txt`, `routes.txt`, `trips.txt`, `stop_times.txt`, `calendar.txt`, `calendar_dates.txt`, `shapes.txt`, `feed_info.txt`, etc.
- **Required for “OD time table”:** `routes.txt`, `trips.txt`, `stop_times.txt`

## Quick Start
1. Download `GTFS Viewer.html` file.
2. Open `GTFS Viewer.html` in your browser (double-click is fine).
3. Click on "Choose files" and select GTFS `.txt` files (or a `.zip` containing them).
4. Start exploring.

## Usage Notes
- You can load a full `.zip` feed or select individual `.txt` files.
- Sorting: click a column header.
- Colors: if `route_color` / `route_text_color` are valid hex (e.g., `2c8976`), they’ll render.
- File size: uploads around 30 MB have worked in testing; a 60 MB feed currently fails to import; another with 80 MB worked smoothly.
- Validation: the **Required file check** covers whether required/forbidden files are included for the current context, but it doesn’t yet confirm required headers, field formats, or file contents.

## Roadmap / Ideas
- Multi-column sorting (Shift+Click)
- Column show/hide and re-order
- Basic charts (e.g., trips per route, stops per route)
- Keyboard navigation and accessibility improvements
- Very large feed optimization (virtualized tables)

## Development
- Pure front-end (HTML + JS + CSS). No build tools required.
- This repository is read-only: I maintain the original version myself.
- If you’d like to modify or extend it, please **fork** the project and make changes in your own copy.

## Testing

### Manual verification
#### Chrome/Firefox/Safari (latest stable):
- Click **Load sample feed**, pick `sample-feed.zip`, and verify the streaming progress indicator updates while loading.
- Confirm every table renders and basic filtering/sorting works.
- Ensure parsing completes without dropping back to the legacy `blob.text()` path.
- Repeat the steps above with `Public Transport Victoria.zip`.

## Contributing
This repository does **not accept pull requests or direct changes**.
If you’d like to build upon it, feel free to fork it or clone it and create your own version.
You don’t need permission — just give credit.

## License
This project is released under the **MIT License**.
You’re free to copy, modify, and use it in your own projects, subject to the license terms.
See [`LICENSE`](./LICENSE) for details.
