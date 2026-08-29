# Photo Relay support

Photo Relay is a local macOS application. Before requesting help, open Settings
and confirm the app version, destination channel, and update status.

## Common recovery steps

1. Reopen Photo Relay from Applications. It reconnects to an existing local
   transfer process or resumes from the durable ledger.
2. Use the in-app recovery action for the affected video. Never delete the
   Google Photos original until Photo Relay marks the YouTube upload verified
   and you have played it yourself.
3. Check the private diagnostic log at
   `~/Library/Application Support/Photo Relay/photo-relay.log`. Remove filenames
   or other personal context before sharing excerpts.
4. Check for a newer signed release in Settings.

For a reproducible problem, open a report at
[github.com/socraticsurge/photo-relay-downloads/issues](https://github.com/socraticsurge/photo-relay-downloads/issues)
with the Photo Relay version, macOS version, stage that failed, and sanitized
error text. Do not attach OAuth tokens, a client configuration, the SQLite
ledger, or personal videos.

## Security reports

Do not post credentials or an exploitable security report in a public issue.
Use GitHub's private vulnerability reporting for the Photo Relay repository
when available. Revoke the application's Google access immediately if an OAuth
token may have been exposed.
