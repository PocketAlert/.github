<div align="center">

<a href="https://pocketalert.app">
  <img src="logo.svg" alt="Pocket Alert" width="96">
</a>

# Pocket Alert

**Push notifications to your phone from anything that can make an HTTP request.**

Deploys, cron jobs, backups, monitoring, AI agents: one API call and it's on your phone.

[Website](https://pocketalert.app) · [Docs](https://info.pocketalert.app) · [iOS](https://apps.apple.com/us/app/pocket-alert/id6446805143) · [Android](https://play.google.com/store/apps/details?id=com.pocketalert.app) · [Chrome extension](https://info.pocketalert.app/browser-extension)

</div>

---

## Send your first push in 10 seconds

```bash
curl -X POST "https://api.pocketalert.app/v1/messages" \
  -H "Token: YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"title": "Deploy finished", "message": "v2.4.1 is live 🚀"}'
```

Get an API key at [pocketalert.app/account/apikeys](https://pocketalert.app/account/apikeys) and install the app on your phone.

## What you get

| | |
|---|---|
| 🔔 **Alert levels** | From `silent` to `critical`. Critical alerts get through Do Not Disturb. |
| 🔘 **Action buttons** | Open a URL, call a webhook or copy text right from the notification. |
| ⏰ **Scheduled delivery** | Send at a set time or after a delay, cancel any time. |
| 🪝 **Webhooks** | Point any third-party service at a webhook URL and get its events as pushes. |
| 📝 **Forms** | Public forms whose submissions land on your phone. |
| 📱 **Multi-device** | Target one device or broadcast to all of them. |
| 🤖 **MCP server** | AI agents send you pushes and read message history as tool calls. |

## Tools

| Repo | What it does | Get it |
|---|---|---|
| [**cli**](https://github.com/PocketAlert/cli) | Send from the terminal, wrap long jobs with `exec`, watch logs, full-screen inbox in `pocketalert ui` | `brew install pocketalert/tap/pocketalert` |
| [**notification-action**](https://github.com/PocketAlert/notification-action) | GitHub Action: push on build, deploy or failure | `uses: PocketAlert/notification-action@v1.0.0` |
| [**laravel-client**](https://github.com/PocketAlert/laravel-client) | Laravel package for the Pocket Alert API | `composer require pocketalert/laravel-client` |
| [**homebrew-tap**](https://github.com/PocketAlert/homebrew-tap) | Homebrew formulae | `brew tap pocketalert/tap` |

<details>
<summary><b>CLI</b></summary>

```bash
pocketalert auth                                   # paste your API key once
pocketalert send "Backup" "Nightly backup done"
pocketalert exec -- make release                   # push with exit code, duration and last output lines
tail -f /var/log/app.log | pocketalert watch       # bursts arrive as one push
```

</details>

<details>
<summary><b>GitHub Actions</b></summary>

```yaml
- name: Notify on failure
  if: failure()
  uses: PocketAlert/notification-action@v1.0.0
  with:
    token: ${{ secrets.POCKET_ALERT_TOKEN }}
    title: "❌ Deploy failed"
    message: "${{ github.repository }}@${{ github.sha }}"
```

</details>

<details>
<summary><b>AI agents (MCP)</b></summary>

```json
{
  "mcpServers": {
    "pocketalert": {
      "type": "http",
      "url": "https://mcp.pocketalert.app/mcp",
      "headers": { "Authorization": "Bearer your-api-key" }
    }
  }
}
```

Works with Claude Code, Claude Desktop, Cursor and any MCP client. [Setup guide →](https://info.pocketalert.app/mcp)

</details>

## SDKs

Typed clients for **Node.js**, **Python**, **Go** and **PHP** are coming soon. Until then the [REST API](https://info.pocketalert.app/getting-started) works from any language.

---

<div align="center">

**[Get started free →](https://pocketalert.app)**

<sub>Questions or ideas? Open an issue in any repo.</sub>

</div>
