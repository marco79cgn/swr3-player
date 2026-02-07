# 🎵 SWR3 Web Radio Player

A sleek, web-based radio player for [SWR3](https://www.swr3.de) with live stream playback, DVR rewind capability, and real-time track metadata.

![Player Screenshot](https://img.shields.io/badge/SWR3-Live%20Radio-blue?style=for-the-badge)

## Features

- 🔴 **HLS Live Stream** — High-quality audio via Akamai CDN
- ⏪ **DVR Rewind** — Scrub back through the stream buffer (up to ~1h depending on CDN)
- ⏩ **Skip Controls** — Jump 30 seconds forward/backward
- 🎵 **Live Metadata** — Song title, artist & cover art from the ARD API (updates every 20s)
- 🎨 **Cover Art** — Album artwork displayed when available
- 🔊 **Volume Control** — Built-in volume slider
- 📱 **Responsive** — Works on desktop and mobile
- 🍎 **Safari Compatible** — Uses native HLS on Safari/iOS, hls.js on other browsers

## Usage

Just open `index.html` in your browser. No build step, no dependencies to install, no server needed.

```bash
# Clone and open
git clone https://github.com/marco79cgn/swr3-player.git
cd swr3-player
open index.html
```

Or serve it locally:

```bash
python3 -m http.server 8080
# → http://localhost:8080
```

## How It Works

- **Audio**: HLS stream via [hls.js](https://github.com/video-dev/hls.js/) (with Safari native fallback)
- **Metadata**: Polled every 20 seconds from the [ARD Programm API](https://programm-api.ard.de/radio/api/publisher?publisher=urn:ard:publisher:73c0dd2d4e1e1514)
- **Zero dependencies**: Single HTML file, external CDN for hls.js only

## Customization

Want to use this for a different ARD radio station? Update these two constants in `index.html`:

```javascript
const STREAM_URL = 'https://...';  // HLS stream URL
const META_URL = 'https://...';    // ARD publisher API URL
```

## License

MIT
