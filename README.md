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

The Releases page is the canonical download and update location. If that page
is empty, no signed public installer has been released yet.

## What stays local

Videos travel from Google Photos to this Mac and then to YouTube. Photo Relay
does not operate a cloud video relay. Its transfer ledger, temporary media,
posters, and diagnostics remain in the current user's private macOS Application
Support directory. Google access and refresh tokens use macOS Keychain when
available, with an owner-only local fallback.

The app includes the publisher's Google Desktop OAuth configuration so users do
not create a Google Cloud project. Google's generated `client_secret` field in
that configuration is extractable public desktop-app data; it is not a user
credential and grants no account access by itself. User OAuth tokens are never
part of the installer.

Read the [privacy notice](PRIVACY.md) and [terms](TERMS.md) before connecting
Google. For help, use
[Issues](https://github.com/socraticsurge/photo-relay-downloads/issues). For a
security concern, follow [the private reporting instructions](SECURITY.md).

The optional Codex companion is currently a local, repository-installed plugin.
It is not a hosted service or a public OpenAI Plugin Directory listing. The
desktop app remains responsible for transfers, and its Google consent, Photos
selection, and manual cleanup steps still require the user.

## Requirements

- macOS 12 or newer.
- A Google account with a YouTube channel.
- Enough free space for one selected video at a time.

The application is distributed as an installer; users do not install Python,
clone source code, create a Google Cloud project, supply an API key, or
configure n8n.
