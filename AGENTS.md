# AGENTS.md — Mr LA Simple

## Architecture

This is a zero-dependency static site. Everything lives in a single `index.html` file with embedded CSS and JavaScript.

```
/
├── index.html        # Entire app (markup + styles + logic)
├── netlify.toml      # Publish directory + security headers
├── README.md
└── AGENTS.md
```

## Key design decisions

- **Single file**: The user requested embedded CSS/JS for instant deployability, so no build tooling is used.
- **Client-side only**: State (selected number, reservation timer, cooldown) is held in JS variables — there is no backend persistence because the numbers are static and session-local reservation is sufficient.
- **API call**: The "Get Code" button POSTs directly to an external Cloudflare-tunneled API (`fiscal-dust-odds-public.trycloudflare.com/send`). The bearer token is embedded in the JS — acceptable for a public read-only operation, not a secret.
- **Cyberpunk theme**: CSS custom properties define the palette (`--accent-red`, `--accent-green`, `--accent-amber`). Glow effects use `box-shadow` with color-matched RGBA values.

## Coding conventions

- Vanilla JS only — no frameworks, no bundler.
- DOM refs are captured once at the top of the `<script>` block.
- State mutation always triggers a full `renderNumbers()` pass so the grid stays consistent.
- CSS uses a single `:root` block for all design tokens.

## Extending

- To add/remove numbers: edit the `NUMBERS` array in `index.html`.
- To change the cooldown: adjust `COOLDOWN_SEC`.
- To change the reservation window: adjust `RESERVE_MS`.
- To add server-side number management (shared reservations across users), introduce Netlify Functions + Netlify Database (`netlify-database` skill).
