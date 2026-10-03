# Contributing

## Adding or correcting a vector

1. Fork the repo and edit `vectors.json`.
2. Follow the existing object shape:
   ```json
   {
     "slug": "kebab-case-id",
     "icon": "LucideIconName",
     "tags": ["short", "signal", "keywords"],
     "categories": ["Broad Category"],
     "label": "Short display name",
     "h1": "Longer descriptive heading",
     "seoTitle": "...",
     "seoDescription": "...",
     "tagline": "One punchy sentence.",
     "intro": ["Paragraph 1.", "Paragraph 2."],
     "mechanics": [{ "title": "Short name", "text": "How this specific mechanism works." }],
     "redFlags": ["Observable signal 1.", "Observable signal 2."],
     "ifHit": ["Step 1.", "Step 2."]
   }
   ```
3. Regenerate `GLOSSARY.md` from `vectors.json` (or update both by hand, keeping them in sync) before opening a PR.
4. Base new entries on real, documented cases where possible — link a source in your PR description.
5. Red flags should be *observable before the loss happens* — not just "this was a scam in hindsight."

## Reporting an error

Open an issue. If a mechanism described is outdated (e.g. a wallet UX change that mitigates a specific drainer technique), include a source for the correction.

## Code changes

`index.html` is intentionally dependency-free (no build step, no frameworks). Please keep it that way, or open an issue first to discuss a change that needs one.

## Code of conduct

Be respectful. This project exists to help people avoid losing money to fraud.
