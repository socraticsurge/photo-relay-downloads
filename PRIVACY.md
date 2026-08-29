# Photo Relay privacy notice

Last updated: August 29, 2026

Photo Relay is a local-first macOS application that moves videos a user selects
in Google Photos to a YouTube channel chosen by that user. This notice describes
the released desktop application's data practices.

## Data Photo Relay accesses

With the user's Google authorization, Photo Relay accesses:

- Google Photos items the user explicitly selects through Google Photos Picker,
  including media bytes and the metadata Google returns for those selections.
- The user's YouTube channel identity.
- YouTube upload, processing, visibility, and media metadata needed to create and
  verify uploads initiated by the user.

Photo Relay never receives the user's Google password and cannot silently browse
the user's full existing Google Photos library.

## How the data is used

Photo Relay uses Google user data only to provide the user-facing transfer,
verification, duplicate-prevention, recovery, and guided cleanup features. It
does not sell user data, use it for advertising, train models on it, or transfer
it to an unrelated third party.

Video bytes travel from Google Photos to the user's Mac and then to YouTube.
Photo Relay does not operate a cloud relay or receive a copy of the video on a
publisher-controlled server.

Photo Relay's use and transfer of information received from Google APIs adheres
to the [Google API Services User Data Policy](https://developers.google.com/terms/api-services-user-data-policy),
including its Limited Use requirements.

## Data stored on the Mac

Photo Relay stores the following in the current user's private macOS Application
Support directory:

- OAuth authorization tokens, preferably protected by macOS Keychain.
- A SQLite transfer ledger, verified backups, and user-confirmed cleanup state.
- At most one working video at a time during normal transfer.
- A small local poster image and technical metadata for transfer recognition and
  recovery.
- Private diagnostic logs that avoid OAuth callback URLs and authorization
  tokens.

The full working video is removed only after YouTube processing and independent
verification succeed. The transfer ledger and poster remain until the user
removes Photo Relay's local data.

## User controls

The application provides controls to:

- Disconnect Google and revoke Photo Relay's authorization.
- Remove locally stored authorized Google/API data after transfers are stopped.
- Quit the local application.
- Export the user's own transfer and cleanup history.

Removing Photo Relay's local data does not delete videos from Google Photos or
YouTube. Users can also review or revoke Google account access from
[Google Account permissions](https://myaccount.google.com/permissions).

## Security and network access

The application binds its interface only to the local loopback address and
rejects cross-origin and invalid request-token mutations. Public installers are
Developer ID signed and notarized before publication. Release update notices
accept only Photo Relay's GitHub Release URLs; installing an update remains an
explicit user action.

## Changes and support

Material changes to this notice will be published with the corresponding Photo
Relay release. Questions, deletion help, and security reports can be opened at
[Photo Relay support](https://github.com/socraticsurge/photo-relay-downloads/issues).
