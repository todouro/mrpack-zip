# mrpack-zip

A minimal browser-based tool that converts a Modrinth `.mrpack` into a regular `.zip` containing its downloadable client-side mod files.

**Website:** https://mrpack-zip.vercel.app/  

## How to use

1. Open [mrpack-zip.vercel.app](https://mrpack-zip.vercel.app/).
2. Drop a `.mrpack` file into the upload area, or choose one.
3. Let the tool download the mods and verify available SHA-512 hashes.
4. Select **Download ZIP**.

The output is named `<pack-name>-mods.zip` and keeps the `mods/` folder structure. Configuration files, resource packs, shaders, and other overrides are not included. Files marked as unsupported on the client are skipped.

## Features

- Drag-and-drop or file-picker upload.
- Light and dark themes that follow the system/browser preference by default.
- Remembers a user's theme choice after they manually toggle it.
- Displays conversion progress and download errors.
- Verifies SHA-512 checksums when the manifest includes them.
- No account, backend, build step, or server-side file storage.

## Privacy and limitations

- The `.mrpack` is opened locally in the browser; the pack itself is not uploaded to this project.
- Mod files are fetched directly from the HTTPS URLs listed in the pack. Hosts that block cross-origin browser requests (CORS) may prevent a file from downloading.
- If a listed SHA-512 hash cannot be verified, conversion stops rather than silently skipping verification.
- Input packs are limited to 250 MB. Converting large packs may use considerable browser memory.
- An internet connection is needed to load JSZip and DM Sans and to fetch mod files.

## Development and deployment

This is a static site; the website lives in `index.html` and requires no build tooling or package installation. Open the file in a browser for basic UI work, or serve it locally over HTTP/HTTPS for browser features and realistic testing.

The production website is hosted on Vercel at https://mrpack-zip.vercel.app/. The repository can be connected to Vercel for automatic deployment from `main`.
