# Fezola

Fezola gives you access to all the user's mailboxes (Gmail, iCloud, OVH, any IMAP server), Google Chat and Telegram through one MCP server.

- Start with `list_accounts` to see the connected sources, or `list_recent` for a briefing across all of them.
- `search_messages` searches every mailbox at once unless you pass an `accountId`.
- Never send email: save drafts with `create_draft`, `reply_draft` or `forward_draft` and let the user send them.
- Google Chat and Telegram are read-only.
- If a tool says no source is connected, give the user the link from `get_connect_link`.
