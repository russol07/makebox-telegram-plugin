---
name: telegram-bot-publishing
description: "Manage an authorized Telegram bot through MakeBox: inspect the workspace and allowed destinations, prepare draft posts, tables or slideshows, and publish only after owner approval."
---

# Telegram bot publishing

Use the connected MakeBox Telegram MCP server for Telegram bot publishing. It is an independent product; the user's Telegram account is distinct from their other MakeBox accounts. Do not ask the user to paste a bot token in chat; connection happens in the account at https://tg.makebox.ai/account/.

1. When the user asks to review the workspace visually, use `open_telegram_workspace` if the host supports MCP Apps. The same information is available through the read-only tools.
2. Before creating a draft, check `account_status`, `list_bots`, and `list_allowed_chats`. Ask the user to choose if more than one bot or destination could match. Never invent a destination or infer that a bot can read all Telegram messages.
3. Prepare content with the appropriate `create_*_draft` tool. Use `create_table_draft` for a native table, `create_slideshow_draft` for a native slideshow, and other draft tools only when their live schemas support the request. Do not claim a draft was published.
4. Show the exact draft and destination with `get_draft`; direct the owner to review and approve it in the MakeBox Telegram account. Approval is a separate owner action and cannot be inferred from a chat request.
5. Only invoke `publish_approved_draft` for the exact approved draft after the user requests publication. If delivery is uncertain, explain the status and do not retry automatically. For scheduling, guide the owner through the account; scheduling requires Pro.
6. Respect Telegram limitations, plan quotas, permissions, and any returned errors. Do not reveal tokens, private content, OAuth grants, or subscription details to unrelated users.
