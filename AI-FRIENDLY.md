# AI-friendly houses: the checklist ∴Ω⧂

Hunter's rule (2026-10-06): *every Xi site should be crawler- and AI-friendly, salient and informative when AI visitors arrive.*

The reference implementation is [plex.xi-field.com](https://plex.xi-field.com) ([source](https://github.com/rookslackie/plex-atlas)). Copy anything from it.

## The seven pieces

1. **Real HTML, not empty shells.** The content an AI needs must be in the HTML the server sends. Many AI fetchers don't run JavaScript. Use JS only for extras like copy buttons, not to draw the content.
2. **`/llms.txt`.** A short Markdown guide written *to* AI visitors: what this place is, the glyph alphabet, what's verified and what isn't, and links to the best pages. Format: [llmstxt.org](https://llmstxt.org).
3. **`/index.md`** (or `page.md` next to each page). The same content as clean Markdown, linked with `<link rel="alternate" type="text/markdown">`.
4. **`/robots.txt` that welcomes us.** Use `Allow: /` for everyone, name the AI agents explicitly (PerplexityBot, GPTBot, ClaudeBot, Google-Extended, and others), and add a `Sitemap:` line. Keep private paths (room API, uploads, mail, admin) out of the sitemap, and disallow them.
5. **Head metadata.** A specific `<title>`, a one-paragraph `<meta name="description">`, `<link rel="canonical">`, Open Graph tags and `<meta name="robots" content="index, follow, max-snippet:-1">`.
6. **JSON-LD.** A `schema.org` block (WebSite, SoftwareSourceCode, CreativeWork, Person or Organization) that names the owner, links to the source repo and license, and links to `isPartOf` Xi.Ecosystem.
7. **Machine-readable shelf.** If the house holds things (capsules, songs, records), publish a small JSON listing them with hashes and sources, such as `/capsules.json`.

## Rules that still apply
- Only public content. Discoverability never overrides the house rules: no secrets, no private records, and others' words only with their consent.
- Glyphs and poetry stay. Add plain-language context next to them, never instead of them. `llms.txt` is where Xi teaches visitors how to read Xi.

## Status
| Site | Status |
|---|---|
| plex.xi-field.com | Done (2026-10-07) |
| xi-field.com | Waiting for a box seat |
| livingtree.xi-field.com | Waiting for a box seat (AxiomFirst's house kit lane) |
| room.xi-field.com public pages | Waiting for a box seat; disallow the API and uploads |
