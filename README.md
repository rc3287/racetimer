# 🏃 RaceTimer

**Progressive Web App for recording race finish times by voice — 100% offline, iOS & Android.**

Built for race officials who need to log bib numbers and arrival times quickly, hands-free, in noisy environments.

---

## ✨ Features

- 🎙️ **Voice input** — say the bib number in French, it's recorded instantly
- ⚡ **Instant or confirmed** — toggle between auto-record and manual confirmation
- 📴 **100% offline** — works with no network via Service Worker cache
- 📱 **Installable** — add to home screen on iOS (Safari) and Android (Chrome)
- ✏️ **Editable** — correct or delete any entry after the fact
- 📧 **CSV export** — send results by email at the end of the race
- 💾 **Persistent** — data survives app restarts via localStorage
- 🥇 **Visual ranking** — gold/silver/bronze medals for top 3

---

## 📸 Screenshots

> *(Add your own screenshots here)*

---

## 🚀 Getting Started

### Option 1 — GitHub Pages (recommended)

1. Fork or clone this repo
2. Go to **Settings → Pages → Deploy from branch → main**
3. Your app is live at `https://yourusername.github.io/racetimer`
4. Open the URL in **Safari (iOS)** or **Chrome (Android)**
5. Add to home screen when prompted

### Option 2 — Local / LAN

```bash
# Any static file server works
npx serve .
# or
python3 -m http.server 8080
```

Then open `http://your-local-ip:8080` on your phone.

> ⚠️ **HTTPS required for microphone access.** GitHub Pages provides this automatically. For local use, use `localhost` or set up a self-signed certificate.

---

## 📱 Installation on Device

### iPhone / iPad
1. Open the app URL in **Safari** (not Chrome)
2. Tap the **Share** button `⎙`
3. Select **"Add to Home Screen"**
4. The app launches in full-screen mode, no browser UI

### Android
1. Open the app URL in **Chrome**
2. Tap the menu **⋮** → **"Add to Home Screen"**
3. Or tap the install banner when it appears

---

## 🗣️ Voice Recognition

The app uses the browser's native **Web Speech API** with `lang: fr-FR`.

**Supported spoken formats:**
| Spoken | Recorded |
|--------|---------|
| "cent quarante-deux" | 142 |
| "quatre-vingt-dix" | 90 |
| "mille vingt" | 1020 |
| "21" | 21 |
| "soixante-dix-sept" | 77 |

**Range:** 1 to 9999

**Offline speech on iOS:**  
Go to *Settings → General → Language & Region → Siri → Language → French (France)*  
iOS will download the on-device model automatically.

---

## ⚙️ Confirmation Mode

A toggle next to the microphone button controls how arrivals are recorded:

| Mode | Behavior |
|------|---------|
| **CONFIRM ON** 🟠 | Recognized number is displayed — official must tap ✓ VALIDATE before saving |
| **CONFIRM OFF** 🔴 | Number is saved immediately upon successful recognition |

The setting persists between sessions.

---

## 📤 Exporting Results

Tap **📧 CSV** in the header. Your email client opens with:
- Subject: `Résultats course DD-MM-YYYY`
- Body: CSV data with columns `Position, Dossard, Heure arrivée, Timestamp`

CSV format:
```
Position,Dossard,Heure arrivée,Timestamp
1,142,09:23:41,1720000000000
2,87,09:24:05,1720000024000
```

---

## 🛡️ Noise Resistance

Four layers of protection against ambient noise:

1. **Deliberate press** — microphone only activates on intentional button press
2. **4-second timeout** — listening stops automatically, no passive capture
3. **Validity filter** — only numbers between 1 and 9999 are accepted
4. **Confirmation mode** — human validation before any data is written (when enabled)

---

## 📁 File Structure

```
racetimer/
├── index.html      # Main app (single file)
├── manifest.json   # PWA manifest
├── sw.js           # Service Worker (offline cache)
├── icon-192.png    # App icon
└── icon-512.png    # App icon (large)
```

---

## 🌐 Browser Compatibility

| Browser | Voice | Offline | Install |
|---------|-------|---------|---------|
| Safari iOS 16+ | ✅ | ✅ | ✅ |
| Chrome Android | ✅ | ✅ | ✅ |
| Chrome Desktop | ✅ | ✅ | ✅ |
| Firefox | ❌ | ✅ | — |
| Safari macOS | ✅ | ✅ | — |

> Firefox does not support the Web Speech API.

---

## 🔒 Privacy

All data stays on the device. Nothing is sent to any server. No analytics, no tracking.

---

## 📄 License

MIT — free to use, modify, and distribute.
