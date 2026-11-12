# Telegram Archive for macOS

Telegram for macOS with one addition: everything that reaches the app is kept on your Mac, in a folder you own. That covers chats, groups, channels, secret chats, edits, deletions, photos, videos, voice notes and files.
You use it exactly like Telegram, and the archive happens by itself.

## Download

From this repository's **Releases**, take the newest version's two files:

- `TelegramArchive-<version>.dmg`: the installer (about 270 MB; it carries everything it needs, Python included).
- Its `.sha256` file: the checksum to check the download against.

## Check the download (one command)

In Terminal, in the folder holding both files (for example `cd ~/Downloads`):

```bash
shasum -a 256 -c TelegramArchive-v1.1-20261112.dmg.sha256.txt
```

It must print `TelegramArchive-v1.1-20261112.dmg: OK`. Anything else: delete the download and take it again.

## Install

1. Open the DMG.
2. Double-click **Install Telegram Archive**. Terminal opens and shows the install as it goes:
   - the app goes to `/Applications/TelegramArchive.app`;
   - its tools go to `~/telegram-macos-archive-fork`, with their own Python;
   - the two background helpers are set up;
   - then the app opens.
3. Log in with your own Telegram account. It archives from then on.

After the install, three shortcuts sit on your Desktop (and in Applications, Launchpad and Spotlight):

- **Telegram Archive** is Telegram itself.
- **Telegram Archive Viewer** opens your archive in the browser.
- **Export a Telegram Chat** exports one chat (Telegram Desktop's format, Markdown or CSV).

Your archive is in `~/telegram-macos-archive-fork/archive-output/`.

## If macOS blocks it ("Open Anyway")

The app is not notarised by Apple, so macOS may refuse to open a downloaded copy the first time:

1. Click **Done** (or **OK**) on the warning.
2. Open **System Settings → Privacy & Security** and scroll down to **Security**.
3. Next to the line about **Install Telegram Archive** (or **TelegramArchive**), click **Open Anyway** and confirm.
4. Double-click it again.

You do this once for each file macOS asks about.

## Never update it from inside the app

The app does not update itself. A newer version comes as a new DMG here. Install it over the old one: your login and your archive stay.

## What's new in Version 1.1

- **Rename this Mac in Active Sessions:** go to **Settings → Active Sessions → Rename This Device…**.
  - Choose the device name, version and system text your other devices show for this app.
  - **Use this Mac's own for all three** puts them back.
  - One setting covers every account in the app.
  - The new name shows after you quit (⌘Q) and reopen the app.
- Active Sessions now shows the app's short version (11.14.1), without a build number.
- About says **Version 1.1**.

## Remove it

```bash
~/telegram-macos-archive-fork/scripts/uninstall.sh
```

This stops the app and removes the helpers, the app and its shortcuts. Your archive stays, unless you add `--purge-archive` (it asks first).
