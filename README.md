# 🎵 HLS Radio Player

A sleek, web-based radio player for [ARD Audiothek](https://www.ardaudiothek.de) radio stations with live stream playback, DVR rewind capability, and real-time track metadata.

## Features

- 🔴 **HLS Live Stream** — High-quality audio via Akamai CDN
- 📻 **Station Switcher** — Switch between multiple ARD radio stations
- ⏪ **DVR Rewind** — Scrub back through the stream buffer (up to ~1h depending on CDN)
- ⏩ **Skip Controls** — Jump 30 seconds forward/backward
- 🎵 **Live Metadata** — Song title, artist & cover art from the ARD API (updates every 20s)
- 🎨 **Cover Art** — Album artwork displayed when available
- 🔊 **Volume Control** — Built-in volume slider
- 📱 **Responsive** — Works on desktop and mobile
- 🍎 **Safari Compatible** — Uses native HLS on Safari/iOS, hls.js on other browsers

## Included Stations

- **SWR3**
- **radioeins (rbb)**

More ARD stations can be easily added (see below).

## Usage

Just open `index.html` in your browser. No build step, no dependencies to install, no server needed.

```bash
# Clone and open
git clone https://github.com/marco79cgn/hls-radio-player.git
cd hls-radio-player
open index.html
```

Or serve it locally:

```bash
python3 -m http.server 8080
# → http://localhost:8080
```

## Adding Stations

Add a new entry to the `STATIONS` array in `index.html`:

```javascript
{
  id: 'my-station',
  name: 'Station Name',
  stream: 'https://...master.m3u8',
  meta: 'https://programm-api.ard.de/radio/api/publisher?publisher=urn:ard:publisher:...',
}
```

You can find stream URLs and publisher URNs via the [ARD Audiothek](https://www.ardaudiothek.de).

## How It Works

- **Audio**: HLS stream via [hls.js](https://github.com/video-dev/hls.js/) (with Safari native fallback)
- **Metadata**: Polled every 20 seconds from the [ARD Programm API](https://programm-api.ard.de)
- **Zero dependencies**: Single HTML file, external CDN for hls.js only

## License

MIT
