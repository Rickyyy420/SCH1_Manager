# Pack Installer — Quick Start

This README explains how to build and test a pack using the in-app Pack Installer.

## Project layout (relevant)

/your-app-root /config paths.json /logs /packs /ExamplePack pack.json /mods LocalMod.zip /plugins LocalPlugin.dll ui.py main.py  

# your app entrypoint that creates MainWindow and shows it


## 1. Configure Settings
1. Open the app and go to **Settings**.
2. Set **Mods Path** to the folder where mods should be installed (e.g., `C:\Games\ExampleGame\Mods`).
3. Set **Plugins Path** to the folder where plugin DLLs should be installed (e.g., `C:\Games\ExampleGame\Plugins`).
4. Optionally set **Game EXE** (used as fallback install root).
5. If you want to download from Nexus using an API key, set **Nexus API Key** and click **Test Key**.

Settings are saved to `config/paths.json`.

## 2. Create a test pack
1. Create a folder `packs/ExamplePack/`.
2. Copy the provided `example pack.json` into `packs/ExamplePack/pack.json`.
3. If you reference local files in `mod` fields, place them under the pack folder (e.g., `packs/ExamplePack/mods/LocalMod.zip` or `packs/ExamplePack/plugins/LocalPlugin.dll`).
4. If you use `nexus_link`, the installer will download the URL into `packs/ExamplePack/downloads/` and then extract the named DLL from the downloaded zip.

## 3. Pack manifest format
Each item in `pack.json` must be an object with these fields:
- **name**: Display name for logs.
- **type**: `"mod"` or `"plugin"` — determines destination mapping.
- **nexus_link**: (optional) URL to download (zip or file). If present, the installer downloads it into `packs/<Pack>/downloads/`.
- **mod**: Path or filename relative to the pack folder (or the expected DLL name inside a downloaded zip). Examples:
  - `"mods/LocalMod.zip"` (local zip inside pack)
  - `"plugins/LocalPlugin.dll"` (local DLL inside pack)
  - `"CoolMod.dll"` (DLL name to find inside a zip downloaded from `nexus_link`)

Example item:
```json
{
  "name": "Cool Mod",
  "type": "mod",
  "nexus_link": "https://example.com/mods/coolmod.zip",
  "mod": "CoolMod.dll"
}






## 1. Configure Settings
1. Open the app and go to **Settings**.
2. Set **Mods Path** to the folder where mods should be installed (e.g., `C:\Games\ExampleGame\Mods`).
3. Set **Plugins Path** to the folder where plugin DLLs should be installed (e.g., `C:\Games\ExampleGame\Plugins`).
4. Optionally set **Game EXE** (used as fallback install root).
5. If you want to download from Nexus using an API key, set **Nexus API Key** and click **Test Key**.

Settings are saved to `config/paths.json`.

## 2. Create a test pack
1. Create a folder `packs/ExamplePack/`.
2. Copy the provided `example pack.json` into `packs/ExamplePack/pack.json`.
3. If you reference local files in `mod` fields, place them under the pack folder (e.g., `packs/ExamplePack/mods/LocalMod.zip` or `packs/ExamplePack/plugins/LocalPlugin.dll`).
4. If you use `nexus_link`, the installer will download the URL into `packs/ExamplePack/downloads/` and then extract the named DLL from the downloaded zip.

## 3. Pack manifest format
Each item in `pack.json` must be an object with these fields:
- **name**: Display name for logs.
- **type**: `"mod"` or `"plugin"` — determines destination mapping.
- **nexus_link**: (optional) URL to download (zip or file). If present, the installer downloads it into `packs/<Pack>/downloads/`.
- **mod**: Path or filename relative to the pack folder (or the expected DLL name inside a downloaded zip). Examples:
  - `"mods/LocalMod.zip"` (local zip inside pack)
  - `"plugins/LocalPlugin.dll"` (local DLL inside pack)
  - `"CoolMod.dll"` (DLL name to find inside a zip downloaded from `nexus_link`)

Example item:
```json
{
  "name": "Cool Mod",
  "type": "mod",
  "nexus_link": "https://example.com/mods/coolmod.zip",
  "mod": "CoolMod.dll"
}
