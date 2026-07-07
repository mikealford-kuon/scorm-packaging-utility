# SCORM 1.2 MP4/VTT Packager Utility

This utility is a single-page local tool that:

- Lets you select one `.mp4` video and one `.vtt` subtitle file from your machine.
- Previews the exact files in a Video.js player with a black subtitle tray below the video.
- Exposes standard Video.js caption controls in the player toolbar.
- Builds a SCORM 1.2-compliant `.zip` with:
  - `imsmanifest.xml`
  - `index.html` SCORM launch file
  - The selected media files in `media/`
  - Local Video.js assets (`css/video-js.css`, `js/video.min.js`)

## Use

1. From `/Users/mikealford/Documents/Codex/2026-07-06/bu`, run `python3 -m http.server 8080`.
2. Open `http://localhost:8080/outputs/scorm-packaging-utility/index.html` in a modern browser.
3. Enter a package title.
4. Select one `.mp4` and one `.vtt`.
5. Click **Preview video** to verify CC behavior and the black subtitle tray.
6. Click **Build SCORM 1.2 ZIP** to download the package.

## Notes

- The utility includes local copies of JSZip, FileSaver, and Video.js under `vendor/`, so the tool page does not depend on CDN script loading.
- Use the localhost URL rather than `file://` so the utility can embed local Video.js assets into generated SCORM packages.
- The subtitle tray below the player intentionally duplicates caption text from the active WebVTT cue list so it does not overlay the video.
- Generated SCORM packages embed local Video.js CSS/JS files and include basic SCORM 1.2 runtime calls for initialize, incomplete, completed, commit, and finish.
