# Free QR Code Generator — Unlimited, Lifetime

A free QR code generator that makes **static QR codes that never expire**. No account, no subscription, no scan limits, no tracking. Everything runs in your browser — nothing you type is sent anywhere.

Open `index.html` and you're done. There is no build step and no backend.

## Why these codes never expire

Most "free" QR generators encode a short link like `qr.example/a7Fq` and redirect it on their own server. That lets them count scans and charge a subscription, and it means that when the trial ends or the company folds, every code you ever printed stops working.

This tool writes your actual content — the URL, the text, the Wi-Fi password — directly into the pattern. A phone reads it straight off the paper. There is no server in the middle, so there is nothing that can be switched off.

The one caveat: a code containing a *website address* is only as permanent as that website. Point codes at a domain you control. Text, Wi-Fi, contact cards and coordinates have no caveat at all.

## What it does

- **Seven content types** — website, plain text, Wi-Fi login, contact card (vCard 3.0), email, SMS, map location.
- **Live preview** — the code updates as you type, with version, module count, recovery level and byte count shown underneath.
- **Download as PNG or SVG** — PNG up to 4096 px, drawn at a whole number of pixels per module so edges land exactly on the pixel grid. SVG is resolution-free vector for print shops and design tools. Files are named from the content (`qr-wifi-workshop-2g-v3.svg`).
- **Colour presets and custom colours**, with a live contrast check so you don't ship something scanners can't read.
- **Square, rounded or dotted modules** — finder squares always stay sharp.
- **Print settings** — error-correction level, blank margin, output resolution, and a readout of the printed size, size per module, and approximate scan distance.
- **"Will it scan?" checklist** — contrast, polarity, margin, density, and a warning if you paste a link-shortener URL (which would tie your permanent code to someone else's service).
- **Capacity meter** — shows how much of the QR byte limit you're using at the current error-correction level.
- **Keep for later** — saves content in your browser's local storage so you can rebuild the same code any time. Never leaves your machine.
- **Light, dark and auto themes.**
- **Keyboard shortcut** — `Ctrl`/`Cmd` + `S` downloads the PNG.

## Run it

Just open `index.html` in a browser. It works from a plain `file://` URL.

For the clipboard buttons ("Copy image", "Copy SVG") browsers require a secure context, so serving it over localhost is nicer:

```
python -m http.server 8765
```

then open <http://localhost:8765/>.

## Host it

It's a single static file, so any static host works — GitHub Pages, Netlify, Cloudflare Pages, an S3 bucket, or a folder on your own web server.

For GitHub Pages: **Settings → Pages → Source: Deploy from a branch → `main` / root**.

## Dependencies

One: [qrcode-generator](https://github.com/kazuhikoarase/qrcode-generator) (MIT), loaded from cdnjs. Fonts come from Google Fonts with system fallbacks. If you want it to work fully offline, download `qrcode.js` next to `index.html` and change the `<script src>` to point at it.

## Privacy

The page makes no network requests of its own beyond loading the encoder script and fonts. Content you enter is processed in the page and never transmitted. The only thing stored is what you explicitly choose to "Keep for later", and that lives in your own browser's local storage.

## License

MIT — see [LICENSE](LICENSE).
