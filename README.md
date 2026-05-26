# Agentic Code Review Pipeline

An autonomous AI pipeline that triggers on every GitHub Pull Request, fetches the code diff, and generates a structured code review using DeepSeek via OpenRouter — all orchestrated with n8n.

## How It Works

```
GitHub PR Opened → Webhook → Extract PR Data → Fetch PR Diff → DeepSeek AI Review → Format Review Output → Build Review Summary
```

## Pipeline Nodes

| Node | Role |
|---|---|
| Webhook | Receives GitHub PR events |
| Extract PR Data | Parses PR metadata (title, author, repo, diff URL) |
| Fetch PR Diff | Downloads the actual code diff |
| DeepSeek AI Review | Sends diff to DeepSeek via OpenRouter for analysis |
| Format Review Output | Parses the AI response |
| Build Review Summary | Structures the final review output |

## Tech Stack

- **n8n** : workflow orchestration
- **DeepSeek** (via OpenRouter) : AI code review
- **GitHub Webhooks** : event trigger
- **ngrok** : local webhook tunnel (for development)

## Setup

1. Import `workflow.json` into your n8n instance
2. Add your OpenRouter API key in the DeepSeek AI Review node
3. Set up a GitHub webhook pointing to your n8n webhook URL
4. Open a PR - the pipeline runs automatically

## Demo

The pipeline catches real issues - on a test PR it flagged a misleading title, identified a commented-out line of code, and returned 4 structured categories of feedback.
