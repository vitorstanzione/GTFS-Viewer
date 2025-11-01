# GTFS Viewer (Pure HTML)

A lightweight, browser-only static GTFS viewer that loads standard GTFS `.txt` files so you can visualize tables, filter, sort, and more — no server, no build step, just open the HTML file.

> **Why?** Sometimes you just want to inspect GTFS feeds quickly without installing tooling or spinning up a backend.

## Features
- 🔍 View static GTFS tables directly in your browser
- 🔄 Client-side filtering, sorting, and (optionally) multi-column sort
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
4. Click on "Import".
5. Start exploring.

> Tip: If your browser blocks local file access for some features, serve the folder with a tiny static server (e.g., `python -m http.server 8000`) and open `http://localhost:8000`.

## Usage Notes
- You can load a full `.zip` feed or select individual `.txt` files.
- Sorting: click a column header. (Planned) **Shift+Click** to add secondary sort.
- Colors: if `route_color` / `route_text_color` are valid hex (e.g., `2c8976`), they’ll render.
- File size: uploads around 30 MB have worked in testing; a 60 MB feed currently fails to import.
- Validation: the missing-file checker covers whether required/forbidden files are included for the current context, but it doesn’t yet confirm required headers, field formats, or file contents.

## Roadmap / Ideas
- Multi-column sorting (Shift+Click)
- Column show/hide and re-order
- Persistent filters (saved in localStorage)
- Basic charts (e.g., trips per route, stops per route)
- Keyboard navigation and accessibility improvements
- Very large feed optimization (virtualized tables)

## Development
- Pure front-end (HTML + JS + CSS). No build tools required.
- This repository is read-only: I maintain the original version myself.
- If you’d like to modify or extend it, please **fork** the project and make changes in your own copy.

## Testing

### Manual verification
- **Chrome (latest stable):** Import a large GTFS text file (200 MB+). Confirm the import status updates incrementally without falling back to `blob.text()`.
- **Firefox (latest stable):** Repeat the large file import and ensure streaming progress is reported continuously.
- **Safari (latest stable):** Import the same large feed and verify chunked parsing completes without triggering the legacy `blob.text()` path.

## Contributing
This repository does **not accept pull requests or direct changes**.
If you’d like to build upon it, feel free to fork it or clone it and create your own version.
You don’t need permission — just give credit if you want to.

## License
This project is released under **The Unlicense** (public domain).  
You’re free to copy, modify, and use it in your own projects.  
See [`LICENSE`](./LICENSE) for details.
