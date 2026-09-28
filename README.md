# Listener

Press **Start** and talk. After a short pause (0.6s, `SILENCE_MS` in `index.html`) what you said is transcribed and added to the top of the list. It keeps listening until you press **Stop**.

A single static `index.html` — no build step, no dependencies. Uses the browser's built-in Web Speech API, so audio is sent to Google (Chrome) or Apple (Safari) for transcription. Doesn't work in Firefox, Arc or Brave.

## Run locally

The microphone only works on `localhost` or HTTPS, not on a file opened from disk:

```bash
python3 -m http.server 8765
```

Then open http://localhost:8765 in Chrome.

## Deploy to Vercel

No configuration needed — Vercel serves `index.html` as a static site over HTTPS.

**From GitHub:** push this folder to a GitHub repo, then in Vercel choose *Add New → Project*, import the repo, leave Framework Preset on *Other*, and click *Deploy*.

**From the command line:**

```bash
npx vercel --prod
```

## Troubleshooting

- **"Listening…" but no text appears:** Chrome's speech recognition uses the Mac's default input. Check System Settings → Sound → Input and pick your real microphone (not a virtual device like BlackHole).
- **Mic permission keeps being asked:** you opened the file directly (`file://`). Use `localhost` or the deployed HTTPS URL.
- **Language:** change `LANG` in `index.html` (e.g. `'nl-NL'` for Dutch).
