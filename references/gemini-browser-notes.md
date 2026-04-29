# Gemini Browser Image Notes

Use this reference only when the workflow relies on browser-based Gemini image generation.

## Preconditions

- Chrome is running with remote debugging enabled, commonly port `9222`.
- The Chrome profile must already be logged in to Gemini.
- `mcporter` and `chrome-devtools-mcp` are available if this environment uses MCP browser control.

## General sequence

1. Check whether Chrome is listening on the debug port.
2. Open `https://gemini.google.com`.
3. Take a fresh page snapshot.
4. Find the current prompt textbox.
5. Fill an English prompt and press Enter.
6. Wait long enough for image generation.
7. Take a fresh snapshot.
8. Find the current download button.
9. Download the image.
10. Copy/rename it into the article folder.

## Important operational rules

- Element IDs/UIDs change often. Never reuse a previous textbox or download button ID without a fresh snapshot.
- Wait patiently. Image generation can take 45–60 seconds or longer.
- Download and copy each image immediately after it is generated.
- Use English prompts for better image quality.
- Keep prompts concrete: subject, scene, style, composition, lighting, intended article use.

## Image set

Typical article assets:

- `cover.png`: 2.35:1, strong click-through, clean composition, no dense text.
- `img0.png`: illustrates the first key point.
- `img1.png`: illustrates the second key point.
- `img2.png`: illustrates the third key point.
- `img3.png`: ending/interaction image, optional.

## Safer prompt patterns

Cover prompt pattern:

```text
Professional editorial cover image for a WeChat article about <topic>, <specific scene>, modern Chinese city/public-service/news style, clean composition, cinematic lighting, high quality, 2.35:1 aspect ratio, no text
```

Body image prompt pattern:

```text
Editorial illustration for article section about <point>, <specific everyday scene>, realistic but polished, warm natural light, high quality, 16:9 aspect ratio, no text
```

## Avoid likely filter triggers

Avoid direct prompts involving:

- graphic violence or war scenes
- explicit military conflict terms
- sensitive geopolitical maps
- oil/gas conflict framing
- real-person defamation or manipulated political imagery

Use abstract or neutral alternatives:

- `international meeting` instead of conflict-specific scenes
- `public service counter` instead of sensitive bureaucracy claims
- `city skyline and residents` instead of identifiable controversy scenes
- `abstract data dashboard` instead of risky political maps
