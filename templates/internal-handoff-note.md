# Telegram publishing handoff

- Workspace and allowed destination: identify from the connected server.
- Draft: include its returned ID, current status, and a summary of the actual content.
- Owner review: state whether the exact draft was approved in the account.
- Delivery: report the returned status and any uncertainty. Do not retry an uncertain send automatically.
- Never include bot tokens, account passwords, or OAuth credentials.
