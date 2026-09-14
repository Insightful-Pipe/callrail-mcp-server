# CallRail MCP Server by Insightful Pipe

[![MCP Compatible](https://img.shields.io/badge/MCP-Compatible-blue)](https://insightfulpipe.com/mcp-servers/callrail)
[![Insightful Pipe](https://img.shields.io/badge/Insightful_Pipe-MCP_Servers-purple)](https://insightfulpipe.com/mcp-servers)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

> **Connect CallRail to AI assistants: calls, texts, form submissions and attribution.**

Part of the [Insightful Pipe MCP Server Collection](https://insightfulpipe.com/mcp-servers) — use CallRail from Claude, ChatGPT, Cursor, and other AI assistants through the Model Context Protocol (MCP).

<img src="images/callrail-icon.png" alt="CallRail MCP Server" width="64" height="64">

## MCP Server URL

```
https://callrail.insightfulmcp.com/
```

## What is CallRail MCP?

CallRail MCP is a **remote Model Context Protocol server** hosted by InsightfulPipe. Access call tracking data, form submissions, text messages, and analytics from your CallRail account.

## Installation

### Claude

1. Copy the MCP Server URL: `https://callrail.insightfulmcp.com/`
2. Open [Claude Connectors Settings](https://claude.ai/settings/connectors)
3. Scroll to the bottom and click **Add custom connector**
4. Paste the URL and click **Add**
5. Click **Connect** on the connector to start authorization
6. Click **Authorize access** in the browser to complete the connection

### ChatGPT

Custom MCP servers are added through ChatGPT's **Developer mode**. Availability depends on your ChatGPT plan, and workspace admins may need to allow it.

1. Turn on **Developer mode** in ChatGPT settings
2. Create a new app for a remote MCP server and paste the URL: `https://callrail.insightfulmcp.com/`
3. Authorize with your InsightfulPipe account

See OpenAI's guide: [Developer mode and MCP apps in ChatGPT](https://help.openai.com/en/articles/12584461-developer-mode-and-mcp-apps-in-chatgpt)

### Claude Code

```bash
claude mcp add --transport http callrail https://callrail.insightfulmcp.com/
```

### Cursor

Add the server to `~/.cursor/mcp.json` (all projects) or `.cursor/mcp.json` (one project):

```json
{
  "mcpServers": {
    "callrail": {
      "url": "https://callrail.insightfulmcp.com/"
    }
  }
}
```

Then authorize the connection when Cursor prompts you.

## Available Actions

61 actions: 34 read, 27 write.

### Read Actions (34)

<details>
<summary>Show all 34 read actions</summary>

| Action | Description |
|--------|-------------|
| `get_account` | Get a specific account by ID |
| `get_accounts` | List all accounts accessible with the current API key |
| `get_call` | Get a specific call by ID |
| `get_call_page_views` | List page views associated with a specific call (session-tracked calls only) |
| `get_call_recording` | Get the recording URL for a specific call |
| `get_call_summary` | Get aggregated call summary statistics, optionally grouped by source, keywords, campaign, etc |
| `get_call_timeseries` | Get call data as a time series, with configurable interval (hour, day, week, month, year) |
| `get_caller_id` | Get a specific outbound caller ID |
| `get_caller_ids` | List all outbound caller IDs for a company |
| `get_calls` | List all calls for an account |
| `get_companies` | List all companies in an account |
| `get_company` | Get a specific company by ID |
| `get_form_submission` | Get a specific form submission by ID |
| `get_form_submissions` | List all form submissions in an account |
| `get_form_summary` | Get aggregated form submission summary statistics, optionally grouped |
| `get_integration` | Get a specific integration by ID |
| `get_integration_filter` | Get a specific integration filter by ID |
| `get_integration_filters` | List all integration filters (trigger criteria) for a company |
| `get_integrations` | List all integrations for a company |
| `get_lead_timeline` | Get the timeline of all interactions for a specific lead |
| `get_message_flow` | Get a specific message flow with all steps |
| `get_message_flows` | List all message flows in an account |
| `get_notifications` | List all notification subscriptions in an account |
| `get_sms_thread` | Get a specific SMS thread with paginated messages |
| `get_sms_threads` | List all SMS threads in an account |
| `get_summary_email` | Get a specific summary email subscription by ID |
| `get_summary_emails` | List all summary email subscriptions in an account |
| `get_tags` | List all tags in an account |
| `get_text_message` | Get a specific text message conversation with paginated messages |
| `get_text_messages` | List all text message conversations in an account |
| `get_tracker` | Get a specific tracker by ID |
| `get_trackers` | List all trackers (source trackers and keyword pools) in an account |
| `get_user` | Get a specific user by ID |
| `get_users` | List all users in an account |

</details>

### Write Actions (27)

<details>
<summary>Show all 27 write actions</summary>

| Action | Description |
|--------|-------------|
| `bulk_update_companies` | Bulk update settings across multiple companies |
| `create_call` | Create an outbound phone call |
| `create_caller_id` | Create a new outbound caller ID for verification |
| `create_company` | Create a new company in an account |
| `create_form_submission` | Create a new form submission |
| `create_integration` | Create a new webhook or custom integration for a company |
| `create_integration_filter` | Create a new integration filter (trigger criteria) |
| `create_message_flow` | Create a new message flow with steps |
| `create_notification` | Create a new notification subscription |
| `create_summary_email` | Create a new summary email subscription |
| `create_tag` | Create a new tag at the account or company level |
| `create_tracker` | Create a new source or session tracker |
| `create_user` | Create (invite) a new user to the account |
| `send_text_message` | Send a text message to a customer |
| `set_ignored_form_fields` | Set form field names to ignore when capturing form submissions |
| `update_call` | Update a call's tags, notes, value, lead status, or customer name |
| `update_company` | Update a company's settings |
| `update_form_submission` | Update a form submission's tags, notes, value, or lead status |
| `update_integration` | Update an integration's state or configuration |
| `update_integration_filter` | Update an integration filter's criteria |
| `update_message_flow` | Update a message flow's name or steps |
| `update_notification` | Update a notification subscription |
| `update_sms_thread` | Update an SMS thread's notes, tags, value, or lead qualification |
| `update_summary_email` | Update a summary email subscription |
| `update_tag` | Update a tag's name, color, or disabled status |
| `update_tracker` | Update a tracker's settings |
| `update_user` | Update a user's details or company access |

</details>

## Control What Your AI Can Do

You decide what AI agents can do with each connected account:

- **Turn individual actions on or off** for every connected account, so agents only see the actions you allow.
- **Connect as Read-only or Read & Write.** A read-only connection can only enable read actions.
- **Destructive actions stay off by default.** Actions such as deletes are disabled until an admin enables them.
- **Team access per account.** Restricted team members only use the accounts they are granted, with the read actions enabled on them.

## Usage Examples

```
"How many calls did we get per source last month?"
```

```
"Show form submissions from the last 7 days"
```

```
"Which campaigns drove the most first-time callers?"
```

## Explore More MCP Servers by Insightful Pipe

Visit **[insightfulpipe.com/mcp-servers](https://insightfulpipe.com/mcp-servers)** to discover our full collection of MCP servers.

- [Google Ads MCP](https://insightfulpipe.com/mcp-servers/google-ads)
- [Meta Ads MCP](https://insightfulpipe.com/mcp-servers/facebook-ads)
- [LinkedIn Ads MCP](https://insightfulpipe.com/mcp-servers/linkedin-ads)
- [TikTok Ads MCP](https://insightfulpipe.com/mcp-servers/tiktok-ads)

**[View All MCP Servers →](https://insightfulpipe.com/mcp-servers)**

## Resources

- [Documentation](https://insightfulpipe.com/docs)
- [Video Tutorial](https://www.youtube.com/playlist?list=PLJNzvjxzI5Xwe__BJJLAelSF0ewO3mEFk)
- [InsightfulPipe Blog](https://insightfulpipe.com/blog)

## Support

- **Documentation**: [insightfulpipe.com/docs](https://insightfulpipe.com/docs)
- **All MCP Servers**: [insightfulpipe.com/mcp-servers](https://insightfulpipe.com/mcp-servers)
- **Email**: support@insightfulpipe.com

---

**[Insightful Pipe](https://insightfulpipe.com)** — AI-powered marketing analytics through MCP servers. [Explore all integrations →](https://insightfulpipe.com/mcp-servers)

## License

MIT License - see [LICENSE](LICENSE) for details.
