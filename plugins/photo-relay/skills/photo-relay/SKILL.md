---
name: photo-relay
description: Move user-selected Google Photos videos to YouTube through the local Photo Relay worker, monitor durable transfers, recover failures, and guide verified manual cleanup without sending video bytes through the agent.
---

# Photo Relay

Use Photo Relay as the local execution engine for user-selected Google Photos
videos. The SQLite ledger, Google tokens, temporary media, and upload sessions
remain on the user's Mac. Tool results contain only the metadata needed for the
current step.

## Start every workflow

The installed Photo Relay desktop application is a hard prerequisite for this
companion. Its bundled helper provides the MCP process; without the app the
tools cannot start. If the launcher reports that Photo Relay is not installed,
send the user only to the trusted Photo Relay Releases page and stop.

1. Once the desktop app is installed, call `status` before suggesting or taking
   an action. This reads cached local state and does not refresh Google.
2. Follow `nextAction` unless the user asked for a narrower read-only status.
3. If Photo Relay is not running, call `open_app`.
4. Use `open_app` for recovery, channel-switch confirmation, ambiguous YouTube
   commits, older-upload reconciliation, or any state not covered by a narrow
   tool.

## Setup and selection

- Google Photos Picker is an unavoidable human step. Never claim the plugin can
  scan, select, or delete the user's whole Photos library automatically.
- Call `connect_google` only when status says the account is disconnected. The
  user must personally approve Google's consent screen.
- Before selecting or transferring, establish the exact YouTube channel shown
  by status.
- Never infer whether content is made for kids. Ask the user to choose that
  value and the YouTube visibility, then call `set_upload_defaults` with those
  exact choices.
- Default the first rehearsal to one short, non-sensitive video. Use batches of
  100 or fewer unless the user knowingly chooses a larger batch.
- Use `check_older_uploads: true` when the selection may contain videos uploaded
  before Photo Relay. This stops before creating a new upload when a fingerprint
  needs reconciliation.
- After `select_videos`, retain its `sessionId`. The user finishes selection in
  Google Photos; then call `finish_selection`. If selection is unfinished, wait
  rather than opening a second picker session.

## Transfer behavior

- Starting or finishing a selection can create YouTube uploads. State the saved
  channel, visibility, and audience immediately before the first start when they
  are not already clear from the conversation.
- Use `pause_transfers` when asked to stop. Explain that it pauses at the next
  durable checkpoint, not necessarily in the middle of a network request.
- Use `retry_video` only for a failed or paused item. Never retry an ambiguous
  YouTube commit or an older-upload decision; open the app for reconciliation.
- Do not queue another copy merely because the user returned later. The durable
  ledger, Photos media ID, content fingerprint, and Photo Relay marker are the
  duplicate-prevention authority.

## Manual cleanup

Photo Relay never deletes a Google Photos original.

1. Call `next_cleanup_item` for one verified proof at a time.
2. Call `open_cleanup_item` with `youtube`; ask the user to play and identify
   the upload. Call `record_cleanup_review` with `youtube_playback` only after
   the user says playback is correct.
3. Call `open_cleanup_item` with `google_photos`; have the user compare preview,
   capture time, duration, and filename. Duplicate filenames are possible. Call
   `record_cleanup_review` with `photos_match` only after the user says it is the
   exact original.
4. The user moves the original to Google Photos Trash themselves.
5. Call `confirm_manual_trash` only after the user explicitly states:
   `I moved this exact Google Photos video to Trash`.
6. Report that Photo Relay recorded the manual action; never say the plugin
   performed the deletion. Use `undo_manual_trash_confirmation` to correct only
   the local record.

## Privacy and safety

- Never request or display Google OAuth tokens, client secrets, resumable-upload
  URLs, Photo Relay's loopback launch URL, cookie, CSRF token, database path, or
  temporary-file path.
- Do not ask the user to create a Google Cloud project or supply credentials.
- Do not expose Photo Relay's local HTTP endpoint to a network interface.
- Do not use generic browser automation to bypass Google Photos Picker or its
  consent and selection steps.
