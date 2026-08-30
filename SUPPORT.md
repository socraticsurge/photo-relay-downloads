# Photo Relay support

Photo Relay is a local macOS application. Before requesting help, open Settings
and confirm the app version, destination channel, and update status.

## Local Codex plugin

The optional Photo Relay plugin is a local companion to the installed desktop
application. It does not replace the app, upload a user's video through Codex,
or provide a hosted Photo Relay service. The plugin requires macOS, a working
Photo Relay installation or source checkout, and a Codex version that supports
local plugins and stdio MCP servers.

If the plugin cannot find or start Photo Relay:

1. Open Photo Relay directly from Applications and confirm its interface loads.
2. Install the newest Photo Relay build before reinstalling the plugin; older
   app bundles do not contain the `photo-relay-mcp` helper.
3. Start a new Codex task after installing or updating the plugin so its skill
   and tools are reloaded.
4. If using a source checkout, run Codex from that checkout or set
   `PHOTO_RELAY_PROJECT_ROOT` to its absolute path.

Never paste an MCP transcript containing personal filenames into a public
issue. Report the plugin version, app version, and a sanitized error message.
The local plugin is supported for personal and repository-local use; it is not
currently a public Plugin Directory integration.

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

For a reproducible desktop or plugin problem, open a report at
[github.com/socraticsurge/photo-relay-downloads/issues](https://github.com/socraticsurge/photo-relay-downloads/issues)
with the Photo Relay version, macOS version, stage that failed, and sanitized
error text. Do not attach OAuth tokens, a client configuration, the SQLite
ledger, or personal videos.

## Security reports

Do not post credentials or an exploitable security report in a public issue.
Use GitHub's private vulnerability reporting for the Photo Relay repository
when available. Revoke the application's Google access immediately if an OAuth
token may have been exposed.
