# Live Internet Meter

Real‑time **ping, download, and upload** monitoring that runs entirely in your browser - no installs, no backend. A single, self‑contained HTML file with live gauges, sparklines, a rolling history chart, automatic nearest‑server selection, and network/location info.

![Type](https://img.shields.io/badge/type-static%20web%20app-0d9488)
![Built with](https://img.shields.io/badge/built%20with-HTML%20%C2%B7%20CSS%20%C2%B7%20JS-1d4ed8)
![No build step](https://img.shields.io/badge/build-none-c2410c)
![License](https://img.shields.io/badge/license-MIT-15803d)

> **Live demo:** `https://kathan555.github.io/live-internet-meter/`
> _(available once enable GitHub Pages)

---

<!--
## 🎥 Demo

> _Demo video coming soon._
-->

<!--
  To embed your video: open a new GitHub Issue on this repo, drag‑and‑drop the
  video file into the comment box, copy the generated
  https://github.com/<user>/<repo>/assets/... URL it produces, and paste that
  URL on its own line here. GitHub renders it as an inline player.
-->

## 📸 Screenshot
<img width="1917" height="911" alt="First" src="https://github.com/user-attachments/assets/dee359d2-9c2b-4162-aec4-af4b6466a474" />
<img width="1917" height="791" alt="Second" src="https://github.com/user-attachments/assets/62f16e00-3f0b-4bd6-8c89-9f6add0eba19" />
<img width="1917" height="907" alt="Third" src="https://github.com/user-attachments/assets/3cbffb07-88fc-41f7-bb81-5ea0cfbe165c" />
<img width="487" height="847" alt="Fourth" src="https://github.com/user-attachments/assets/6053f287-0ac9-4e90-98f2-e68b8234c481" />

---

## ✨ Features

**Live metrics**
- **Ping latency** with min / max / avg / jitter, a sparkline, and a quality badge.
- **Download** and **upload** speed on auto‑scaling speedometer gauges, with peak / average / sample counts. Click the unit pill to switch units.
- **Rolling history chart** of the last 60 data points (Chart.js).

**Smart server selection**
- Discovers public **iperf3** servers near you (by IP geolocation) from the community [R0GGER server list](https://github.com/R0GGER/public-iperf3-servers), plus Cloudflare anycast anchors.
- Ranks reachable servers by latency and lets you **click any reachable server** to use it; keeps finding more in the background.

**Context**
- **Network info** : IP, ISP, ASN, effective connection type, and the browser's downlink/RTT estimates.
- **Location** : city, region, country, timezone, and coordinates (via the browser Geolocation API, with a clear permission flow).
- **Offline detection** : a banner when the connection drops and a toast when it returns.

**Experience**
- Clean, readable light UI with smooth transitions, tabular figures (so numbers don't jitter), full keyboard focus styles, and reduced‑motion support.
- Responsive from mobile to desktop.
- **Settings panel** to toggle each widget, set the ping interval (200 ms – 5 s), turn sparklines on/off, and re‑scan servers.

---

## 🧱 Tech stack

- **Vanilla** HTML / CSS / JavaScript. no framework, no bundler.
- [Bootstrap 5.3](https://getbootstrap.com/) (grid + layout)
- [Font Awesome 6.5](https://fontawesome.com/) (icons)
- [Chart.js 4.4](https://www.chartjs.org/) (history chart)
- [Inter](https://rsms.me/inter/) + [JetBrains Mono](https://www.jetbrains.com/lp/mono/) (typography, via Google Fonts)

All dependencies load from CDNs, so the page needs an internet connection to run (which it does anyway, being an internet meter).

---

## 🚀 Run locally

It's one file. The simplest way:

```bash
# clone, then open the file in your browser
git clone https://github.com/<your-username>/live-internet-meter.git
cd live-internet-meter
```

Open `index.html` in a modern browser. For full functionality (the **Location**
card uses the Geolocation API, which prefers a secure context), serve it over
`http://localhost` instead of `file://`:

```bash
# Python 3
python -m http.server 8080
# then visit http://localhost:8080
```

---

## 🌐 Deploy to GitHub Pages

Because it's a static `index.html`, you get a free hosted demo:

1. Push this repo to GitHub (see [below](#-push-to-github)).
2. On GitHub: **Settings → Pages**.
3. Under **Source**, choose **Deploy from a branch**, pick **`main`** and **`/ (root)`**, then **Save**.
4. After a minute your app is live at
   `https://<your-username>.github.io/live-internet-meter/`.

---

## ⚙️ How it works & accuracy

- **Download/upload** are *estimates* of throughput to Cloudflare's public speed
  endpoints (`speed.cloudflare.com`). They are useful and live, but **not an
  ISP‑grade speed test** — browsers can't open raw sockets, so true iperf3
  throughput isn't possible from a web page.
- **Ping** is the latency to the selected server (an HTTPS request timed
  round‑trip), not an ICMP ping.
- **Third‑party services** are contacted to make this work: Cloudflare (speed),
  `ipapi.co` / `api.ipify.org` (IP & network info), and the R0GGER iperf3 list
  (server discovery). Your IP is therefore visible to those services. Geolocation
  data stays in your browser and is used only to rank nearby servers.

---

## 🗺️ Roadmap

- [ ] Lightweight **desktop widget** (always‑on‑top mini view) — _in progress_.
- [ ] Optional self‑hosted dependencies for fully offline‑resilient loading.

---

## 🤝 Contributing

Issues and pull requests are welcome. For larger changes, open an issue first to
discuss what you'd like to change.

---

## 📄 License

Released under the [MIT License](LICENSE).

---

## 👤 Author

**Kathan** — [Portfolio](https://kathanpatel.vercel.app/)

## 🙏 Acknowledgements

- [Cloudflare Speed Test](https://speed.cloudflare.com/) endpoints
- [R0GGER/public-iperf3-servers](https://github.com/R0GGER/public-iperf3-servers)
- Bootstrap, Font Awesome, Chart.js, and the Inter & JetBrains Mono typefaces
