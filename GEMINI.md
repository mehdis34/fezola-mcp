# Fezola

Fezola gives you access to the user's accounts across tools through one MCP server, several accounts per tool: mailboxes (Gmail, Outlook.com, iCloud, OVH, any IMAP server), Google Chat, Telegram, Google Calendar, Google Ads and relayed services such as Notion.

- Start with `list_accounts` to see the connected sources, or `list_recent` for a briefing across all of them.
- `search_messages` searches every mailbox at once unless you pass an `accountId`.
- Never send email: save drafts with `create_draft`, `reply_draft` or `forward_draft` and let the user send them.
- Google Chat and Telegram are read-only. Google Calendar and Google Ads can be read and changed; Google Ads changes can be checked first with `validateOnly`.
- Relayed services (Notion...): `search_connector_tools` finds their tools, `call_connector_tool` runs one on a given account.
- If a tool says no source is connected, give the user the link from `get_connect_link`.
