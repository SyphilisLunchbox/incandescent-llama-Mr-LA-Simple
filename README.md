# Mr LA Simple

A privacy-first temporary US phone number service. Users can get SMS verification codes without creating an account.

## What it does

- Displays a list of temporary US phone numbers
- Users select a number (reserved for 10 minutes) and enter their own phone number
- Clicking **Get Verification Code** POSTs to an external SMS API
- A cooldown prevents spam — the button disables for ~12 seconds after each send

## Tech stack

- Plain HTML, CSS, and JavaScript — no build step, no dependencies
- Hosted as a static site on Netlify

## Running locally

Open `index.html` directly in a browser, or serve it with any static server:

```bash
npx serve .
```

Or via Netlify CLI for full edge/header support:

```bash
netlify dev
```
