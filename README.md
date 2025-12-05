# `clippit.sh` Reference

Comprehensive operator notes for the `clippit.sh` workflow that trims raw camera archives into a single downloadable clip.

## Purpose

`clippit.sh` is an interactive Bash utility that:
- Enumerates available camera IDs from an archive drive.
- Copies only the MP4 files for a chosen camera within a start/end window.
- Concatenates them losslessly with `ffmpeg`.
- Hosts the resulting clip over HTTP for easy transfer.
- Cleans up every temporary artifact once the operator finishes.

...

## Example Session

```bash
./clippit.sh 20240102 1200 20240102 1230
# Review the printed camera list and enter (for example) CAM12
# Wait for "Concatenating video content..." and ffmpeg timing output
# Download CAM12-202401021200-202401021230_out.mp4 from http://<host>/
# Press Ctrl+C when downloads finish; the script cleans up automatically


- Replaced the starter README with a concise repo overview, highlighted the `clippit.sh` workflow, and pointed readers directly at the new documentation so it’s easy to discover.  
```1:22:Video_Scripts/README.md
# Video Scripts

Utility scripts that help trim, package, and deliver archived surveillance video. The repository currently contains several Bash helpers—`clippit.sh`, `snipit-01252021.sh`, and historical variants—that expect camera footage on removable SSDs.

## `clippit.sh`

- Interactive workflow to gather a camera ID, copy footage for a bounded date/time range, and join the clips with `ffmpeg`.
- Starts a temporary HTTP server on port 80 so the concatenated clip can be downloaded from another machine.
- Deletes every temporary file when you stop the server, keeping the processing SSD tidy.

👉 Read the full operator guide in [`docs/clippit.md`](docs/clippit.md).

## Repository Layout

| Path | Purpose |
| --- | --- |
| `clippit.sh`, `clippit-*.sh` | Video clipping scripts (latest workflow documented). |
| `date_clipper.sh`, `filechk.sh` | Supporting utilities for other workflows. |
| `docs/` | Script-specific documentation. |
| `index.html`, `styles.css` | Legacy GitHub Pages assets (safe to ignore for CLI usage). 
