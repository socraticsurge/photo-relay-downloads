# Photo Relay downloads

Photo Relay is a local-first macOS app that moves videos you select in Google
Photos to your YouTube channel one at a time. It avoids a full Google Takeout
download, keeps a restart-safe local transfer record, and never deletes your
Google Photos originals.

## Download

Signed and notarized installers will appear on the
[Releases](https://github.com/socraticsurge/photo-relay-downloads/releases)
page. Choose:

- `arm64` for Apple silicon Macs (M1 or newer).
- `x86_64` for Intel Macs.

Open the DMG, drag **Photo Relay** to **Applications**, and launch it there.
Published releases are checked by Apple notarization and include a SHA-256
checksum. Do not install artifacts from issues, comments, forks, or unofficial
mirrors.

No public installer has been released yet. This repository will remain the
canonical download and update location when the first signed build is ready.

## What stays local

Videos travel from Google Photos to this Mac and then to YouTube. Photo Relay
does not operate a cloud video relay. Its transfer ledger, temporary media,
posters, diagnostics, and Google authorization state remain in the current
user's private macOS Application Support directory.

Read the [privacy notice](PRIVACY.md) before connecting Google. For help, use
[Issues](https://github.com/socraticsurge/photo-relay-downloads/issues). For a
security concern, follow [the private reporting instructions](SECURITY.md).

## Requirements

- macOS 12 or newer.
- A Google account with a YouTube channel.
- Enough free space for one selected video at a time.

The application is distributed as an installer; users do not install Python,
clone source code, create a Google Cloud project, supply an API key, or
configure n8n.
