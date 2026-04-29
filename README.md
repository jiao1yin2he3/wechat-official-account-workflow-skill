# WeChat Official Account Workflow Skill

An AgentSkill for running a complete WeChat Official Account article workflow:

topic selection → article drafting → humanized editing → AI images → self-review → publish to WeChat draft box → cleanup.

## Install

Copy this folder into your OpenClaw/Codex skills directory, or install it through your preferred skill manager.

Required file:

- `SKILL.md`

Optional references are under `references/` and are loaded only when needed.

## What this skill does

- Helps choose traffic-oriented topics.
- Drafts WeChat-ready Markdown articles.
- Adds image placeholders for cover/body images.
- Guides AI image generation.
- Runs pre-publish self-review.
- Publishes via an existing WeChat Official Account publishing tool/skill such as `baoyu-post-to-wechat`.

## Secrets

Do **not** commit WeChat credentials.

Use environment variables or local ignored config:

```powershell
$env:WECHAT_APP_ID="..."
$env:WECHAT_APP_SECRET="..."
```

## Recommended companion skills/tools

- `baoyu-post-to-wechat` for WeChat draft publishing.
- `gemini-browser-image` or another image generation workflow for cover/body images.
- `ai-humanizer` or equivalent review tooling for reducing AI-like writing patterns.
