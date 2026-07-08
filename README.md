# The "I'm bad at flirting" QR page 🫣

A single, self-contained HTML page for the QR code on the t-shirt. Someone scans the
shirt, gets a humorous 5-question quiz, a rigged 94–99% "compatibility score", and two
ways to actually reach you:

- **WhatsApp** — opens a chat to your number with their name + quiz answers pre-filled
- **SMS fallback** — same message via their texting app

There is **no backend and no data collection** — everything happens on their phone, and
their answers travel inside the WhatsApp/SMS message they send you.

## 1. Put in your real details

Open `index.html` and edit the `CONFIG` block near the top of the `<script>`:

```js
const CONFIG = {
  myName: "Chris",
  whatsappNumber: "REPLACE_ME", // digits only, with country code, e.g. "447712345678"
  smsNumber: "+REPLACE_ME",     // e.g. "+447712345678"
};
```

Feel free to also edit the questions in the `QUESTIONS` array — they're just text.

## 2. Host it (free, ~2 minutes)

Any static host works, it's one file:

- **GitHub Pages**: put `index.html` in a repo (ideally a personal one, not this CRM
  repo!), enable Pages in repo settings → you get `https://<you>.github.io/<repo>/`
- **Netlify Drop** (easiest): go to <https://app.netlify.com/drop> and drag the file in
- **Vercel / Cloudflare Pages**: import the folder as a static project

Tip: the URL will be visible to whoever scans it, so a short/cute domain or a
`is.gd`/short-link on top is a nice touch.

## 3. Generate the QR code for the shirt

Point any QR generator at your hosted URL — e.g. <https://www.qrcode-monkey.com>
(free, no account, high-res PNG/SVG for printing). For shirts:

- Use **high error correction (H)** so it still scans with fabric wrinkles
- Dark code on a light patch scans best; print it at least ~10 cm wide
- **Test-scan the actual printed shirt** before wearing it into battle

## 4. Test it

Open the page on your phone, run through the quiz, and tap the WhatsApp button —
it should open a chat with *your own* number with the message pre-filled.

## How this is published

The live site is served from the `gh-pages` branch (root `index.html`).
To update the page: edit `index.html` on `main`, then copy it to `gh-pages` and push:

```bash
git checkout gh-pages && git checkout main -- index.html && git commit -am "Update page" && git push && git checkout main
```
