# MRPACK ZIP

A tiny, static converter that turns a Modrinth `.mrpack` into a regular ZIP containing the actual client-side files listed under `mods/`.

## Use

1. Open the website over HTTPS.
2. Drop in a `.mrpack` file.
3. Wait for the mods to download and checksums to be verified.
4. Click **Download ZIP**.

The output is named `<pack-name>-mods.zip` and keeps the `mods/` folder structure. It intentionally excludes config files, resource packs, shaders, and other overrides.

## Privacy and limitations

- The uploaded pack is read locally in your browser; it is not sent to a server.
- The converter fetches each mod directly from the HTTPS URL recorded in the pack. A source that blocks cross-origin browser requests (CORS) can prevent that mod from downloading.
- SHA-512 hashes are verified when provided. If a hash is present but the browser cannot verify it, conversion stops rather than silently skipping verification.
- For browser memory safety, the input pack limit is 250 MB. Large packs may still use substantial memory while the ZIP is generated.
- Files marked as unsupported on the client are skipped.

## Deploy with GitHub Pages

This is a static site: no Node.js, build step, database, API key, or server is required.

1. Open the repository's **Settings → Pages**.
2. Under **Build and deployment**, select **Deploy from a branch**.
3. Select branch **main** and folder **/ (root)**, then save.
4. After GitHub Pages finishes deploying, open the site URL shown in that section.

The page uses JSZip from jsDelivr; the browser needs an internet connection to load that library and fetch the listed mods.
