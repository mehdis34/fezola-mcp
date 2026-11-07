<p align="center">
  <img src="assets/logo.png" alt="Fezola" width="96" height="96">
</p>

<h1 align="center">Fezola MCP</h1>

<p align="center">
  <b>One MCP connector for every inbox and chat you own.</b><br>
  Gmail, iCloud, OVH, IONOS, Gandi or any IMAP mailbox, plus Google Chat and Telegram, in Claude, ChatGPT, Perplexity, Cursor, VS Code and any MCP client.
</p>

<p align="center">
  <a href="https://app.fezola.com">Website</a> ·
  <a href="https://app.fezola.com/en/docs">Documentation</a> ·
  <a href="https://youtu.be/NPiCLqNoL_0">Demo video</a> ·
  <a href="https://app.fezola.com/en/pricing">Pricing</a>
</p>

---

The official Gmail connectors in Claude and ChatGPT see one Google account. Most people have more: a personal address, a work one, a custom domain on iCloud or OVH, a Google Chat, a Telegram. Fezola is a **hosted remote MCP server** that puts all of them behind a single connector, so your assistant can answer "what needs my reply today?" across everything.

[![Fezola demo](assets/demo.jpg)](https://youtu.be/NPiCLqNoL_0)

> This repository holds the public documentation and client configuration for the hosted Fezola service. The server itself is closed source and runs at `https://api.fezola.com/mcp`.

## Connect

| | |
|---|---|
| **Server URL** | `https://api.fezola.com/mcp` |
| **Transport** | Streamable HTTP |
| **Authentication** | OAuth 2.1 with PKCE and dynamic client registration. You sign in to Fezola and approve the assistant on a consent screen. No API key to copy. |
| **Registry** | Official MCP Registry: `com.fezola.app/fezola` |

First create a free account at [app.fezola.com](https://app.fezola.com) and add your mailboxes and chats. Then add the connector to your client:

### Claude (claude.ai, Desktop, mobile)

Settings > Connectors > **Add custom connector**, name it `Fezola`, paste `https://api.fezola.com/mcp`, then sign in.

### ChatGPT

In ChatGPT, open Settings > Apps & Connectors > Advanced settings and turn on **Developer mode**. Back in Apps & Connectors, click **Create**, name it `Fezola`, paste `https://api.fezola.com/mcp` and choose **OAuth**. Paid plans only (Plus, Pro, Business), on chatgpt.com.

### Perplexity

Settings > Connectors > **+ Custom connector**, choose **Remote**, name it `Fezola`, paste the URL and choose **OAuth**. Pro and Max plans.

### Claude Code

```bash
claude mcp add --transport http fezola https://api.fezola.com/mcp
```

### Cursor

`~/.cursor/mcp.json`

```json
{
  "mcpServers": {
    "fezola": { "url": "https://api.fezola.com/mcp" }
  }
}
```

### VS Code

`.vscode/mcp.json`

```json
{
  "servers": {
    "fezola": { "type": "http", "url": "https://api.fezola.com/mcp" }
  }
}
```

Any other client that supports remote MCP servers with OAuth works the same way: give it the URL and follow the sign-in.

## What you can ask

- "What needs my reply today?" One briefing across every mailbox, Google Chat and Telegram.
- "Find the OVH invoice from last month." One search over all accounts, attachments included (PDF, Word, images).
- "Summarize the thread with Paul and draft a reply." The draft lands in the mailbox that received the email; you review and send.
- "Archive the newsletters from this week" or "move this to Receipts."

## Tools

| Area | Tools |
|---|---|
| Accounts | `list_accounts`, `test_connection`, `rename_account`, `remove_account`, `get_connect_link`, `get_connection_help` |
| Mail: read | `list_recent`, `search_messages`, `get_message`, `get_thread`, `get_attachment`, `list_folders` |
| Mail: drafts | `create_draft`, `reply_draft`, `forward_draft`, `update_draft`, `list_drafts`, `delete_draft` |
| Mail: organize | `mark_as_read`, `mark_as_unread`, `flag_message`, `move_message`, `archive_message`, `trash_message`, `mark_as_spam` |
| Google Chat (read-only) | `list_chat_spaces`, `list_recent_chat`, `search_chat`, `get_chat_thread` |
| Telegram (read-only) | `list_telegram_chats`, `list_recent_telegram`, `search_telegram`, `get_telegram_chat` |
| Profile and access | `get_profile`, `update_profile`, `list_connected_assistants`, `revoke_assistant` |
| Plan | `get_plan`, `get_upgrade_link`, `get_billing_portal_link`, `list_invoices` |

`send_message` exists but is **off by default**: Fezola saves drafts and you send them yourself. Every tool carries MCP annotations (read-only, destructive, idempotent) so clients can ask for confirmation where it matters.

## Security and privacy

- Messages are read live when the assistant asks. Fezola does not store your emails or chats.
- Mailbox passwords and OAuth tokens are encrypted at rest and never leave the server.
- Each access token only sees the accounts of the user who approved it. You can revoke any assistant at any time.
- Google Chat and Telegram access is read-only.
- Full details: [privacy policy](https://app.fezola.com/en/privacy). Vulnerability reports: [security.txt](https://app.fezola.com/.well-known/security.txt).

## Plans

- **Free**: 2 sources.
- **Pro**: up to 20 sources, 9 EUR or USD per month or 90 per year, 7-day free trial.

## Screenshots

| Your sources | The connector | Consent |
|---|---|---|
| ![Sources](assets/app-sources.png) | ![Connector](assets/app-connector.png) | ![Consent](assets/app-consent.png) |

## Support

- Email: [support@fezola.com](mailto:support@fezola.com)
- Issues and feature requests: [open an issue](../../issues) in this repository. Which channel should come next: Outlook, Slack, WhatsApp Business?

## License

The documentation and configuration examples in this repository are under the [MIT License](LICENSE). The Fezola service is proprietary.
