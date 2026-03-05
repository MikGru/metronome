# Metronome PWA

**Ultra-precise metronome Progressive Web App**  
© 2024 Mike Grudzinskas · MIT License

---

## Features

- ⚡ **Ultra-precise timing** — Web Audio API scheduler (lookahead scheduling, not `setInterval`)
- 👆 **Tap Tempo** — tap multiple times to detect BPM
- 🎵 **Time Signatures** — 2/4, 4/4, 3/4, 6/8, 5/4, 7/8
- 🔀 **Subdivisions** — quarter notes, 8ths, triplets, 16ths
- 💡 **Visual beat indicator** — animated beat grid + pendulum
- 📲 **Installable PWA** — works offline, installs like a native app
- ⌨️ **Keyboard shortcuts** — Space (play/stop), T (tap), ↑↓ (BPM)

## Usage

### Local / Hosted
Open `index.html` in a modern browser. For PWA installation and service worker support, serve over HTTPS or `localhost`.

### Quick serve (Python)
```bash
cd metronome-pwa
python3 -m http.server 8080
# Open http://localhost:8080
```

### Quick serve (Node)
```bash
npx serve .
```

## File Structure

```
metronome-pwa/
├── index.html      # Main app (all-in-one HTML/CSS/JS)
├── manifest.json   # PWA web manifest
├── sw.js           # Service worker (offline caching)
├── LICENSE         # MIT License
├── README.md       # This file
└── icons/
    ├── icon-192.png
    └── icon-512.png
```

## Keyboard Shortcuts

| Key         | Action            |
|-------------|-------------------|
| `Space`     | Play / Stop       |
| `T`         | Tap Tempo         |
| `↑`         | BPM +1            |
| `↓`         | BPM −1            |

## Technical Details

The scheduler uses a **look-ahead Web Audio technique**:
- A `setTimeout` loop fires every 25ms
- Clicks are scheduled 120ms ahead into the `AudioContext` timeline
- This avoids the jitter of relying solely on `setTimeout` for timing

## License

MIT — see [LICENSE](./LICENSE)
