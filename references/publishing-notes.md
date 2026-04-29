# Publishing Notes

Use this reference before sending an article to the WeChat Official Account draft box.

## Required files

Inside the article folder:

- `article.md`
- `cover.png`
- every body image referenced by Markdown placeholders, e.g. `img0.png`, `img1.png`

## Self-review checklist

Before publishing, verify:

- Article title is strong and specific.
- Opening reaches the point quickly.
- `article.md` uses Markdown image placeholders: `![](img0.png)`, not plain text labels.
- Every placeholder file exists in the same folder or correct relative path.
- No secret values appear in article frontmatter or body.
- HTML snippets, if any, use valid syntax: `<div style="...">`.
- The selected theme fits the article.

## Theme selection

- `modern`: technology, hard analysis, finance charts, military-adjacent but safe topics.
- `grace`: business, finance, workplace, city policy, serious public-service posts.
- `simple`: emotion, lifestyle, neighborhood, warm human-interest posts.
- `default`: controversy, hot news, sharp commentary.
- If unsure, use `grace`.

## Publishing method

Prefer API publishing when configured because it is repeatable and precise.

Do not store credentials in the skill or repository. Read them from:

- environment variables
- local ignored `.env` files
- account-level private config supported by the publishing skill

Example command pattern:

```powershell
$env:WECHAT_APP_ID="<your-app-id>"
$env:WECHAT_APP_SECRET="<your-app-secret>"
cd "<article-folder>"
bun "<path-to-baoyu-post-to-wechat>/scripts/wechat-api.ts" article.md --theme grace --submit --cover "cover.png"
```

## Common failures

### Invalid credential / missing environment

Check whether the app ID and secret are available in the current shell or private config.

### IP whitelist error

WeChat Official Account API may require the current outbound IP to be allowlisted.

Useful check:

```powershell
Invoke-RestMethod -Uri "https://api.ipify.org"
```

Ask the account owner to add that IP in the WeChat Official Account backend.

### Missing image placeholders

If the publishing script reports zero placeholder images or body images do not upload, verify `article.md` contains real Markdown placeholders such as:

```md
![](img0.png)
```

### Browser publishing fallback

If API publishing is blocked, use the browser-based publishing script or manual browser workflow from the installed WeChat publishing skill. Browser workflows are more fragile and should be verified with a screenshot or draft-box check.
