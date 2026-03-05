# post ready? ✨

<p align="center">
  <img src="https://img.shields.io/badge/post%20ready%3F-%E2%9C%A8-e63946?style=for-the-badge&labelColor=1d3557" alt="post ready? logo" width="280"/>
</p>

<p align="center">
  <strong>Your AI bestie that tells you if your photo actually slaps.</strong><br/>
  Runs 100% on-device · Zero uploads · No account needed · No cap.
</p>

🌐 **Live Demo**: [2796gaurav.github.io/post_ready](https://2796gaurav.github.io/post_ready/) | 🤗 **HF Spaces**: [huggingface.co/spaces/your-username/post-ready](https://huggingface.co/spaces/your-username/post-ready) *(coming soon)*


<p align="center">
  <a href="https://2796gaurav.github.io/post_ready/" target="_blank">
    <img src="https://img.shields.io/badge/Live%20Demo-457b9d?style=for-the-badge&logo=github&logoColor=white"/>
  </a>
  <img src="https://img.shields.io/badge/AI-On--Device-52b788?style=for-the-badge&logo=brain&logoColor=white"/>
  <img src="https://img.shields.io/badge/Privacy-100%25_Private-1d3557?style=for-the-badge&logo=lock&logoColor=white"/>
  <img src="https://img.shields.io/badge/Model-Qwen3.5_0.8B-9d4edd?style=for-the-badge&logo=huggingface&logoColor=white"/>
  <img src="https://img.shields.io/badge/PWA-Installable-f4a261?style=for-the-badge&logo=pwa&logoColor=white"/>
</p>

---

## 🔥 What is this?

**post ready?** is a zero-backend, fully private AI photo analyzer that lives in a single HTML file. Drop in a photo and the AI — running entirely inside your browser on your own GPU — gives you a vibes breakdown, post score, caption ideas, and glow-up tips before you post.

No server. No API key. No account. Your photos never touch the internet.

<p align="center">
  <img src="https://img.shields.io/badge/Made%20with-HTML%20%2B%20CSS%20%2B%20JS-e63946?style=flat-square"/>
  <img src="https://img.shields.io/badge/Size-~90KB%20(HTML)-457b9d?style=flat-square"/>
  <img src="https://img.shields.io/badge/Model-~1GB%20(download)-52b788?style=flat-square"/>
</p>

---

## ✨ Features

| Feature | Details |
|---------|---------|
| 📸 **Post Check** | Upload any photo and get a full AI vibe breakdown with scores, captions, and tips |
| 🎥 **Live Mode** | Point your camera, tap "Vibe Scan" — get real-time scores on captured frames |
| ⚔️ **Battle Mode** | Upload 2–4 photos and let the AI crown the best one with a side-by-side analysis |
| 🔒 **100% Private** | Model runs locally via WebGPU/WASM. Zero data leaves your device |
| ⚡ **PWA** | Install to home screen for instant offline-capable loads after the first download |
| 🎨 **Scoring** | 8 dimensions: Main Character Energy, Vibe Check, Lighting Slay, Color Story, Composition Drip, Authenticity Meter, Caption Worthy, Scroll-Stop Factor |

---

## 📊 Score Breakdown

The AI rates every photo across 8 dimensions (0–100 each):

```
🌟 Main Character Energy  — Subject presence & command of frame
✨ Vibe Check             — Mood coherence & overall aesthetic
💡 Lighting Slay          — Light quality, direction & softness
🎨 Color Story            — Palette harmony & visual pop
📐 Composition Drip       — Framing, balance & rule-of-thirds
🌿 Authenticity Meter     — Real & candid vs. over-staged
💬 Caption Worthy         — Storytelling & context potential
🛑 Scroll-Stop Factor     — Thumb-stopping power at a glance
```

**Verdicts** range from `not it 💀` → `giving nothing 😐` → `has potential ✨` → `lowkey fire 🔥` → `main character approved ⭐` → `iconic era 🏆`

---

## 🚀 Quick Start

### Option 1 — Just open it (Try it now!)

```bash
# Clone the repo
git clone https://github.com/2796gaurav/post_ready.git
cd post_ready

# Open in browser
open index.html   # macOS
start index.html  # Windows
xdg-open index.html  # Linux
```

> ⚠️ For camera access, serve over `https://` or `localhost`. File:// URLs block camera APIs.

### Option 2 — Local server (recommended for Live mode)

```bash
# Python 3
python3 -m http.server 8080

# Node.js
npx serve .

# PHP
php -S localhost:8080

# Then open: http://localhost:8080
```

---

## 🧠 How It Works

```
┌─────────────────────────────────────────────────────────────┐
│                        Browser                              │
│  ┌───────────────────────────────────────────────────────┐  │
│  │      @huggingface/transformers (CDN)                  │  │
│  │  ┌─────────────────────────────────────────────────┐  │  │
│  │  │    Qwen3.5-0.8B-ONNX (HuggingFace Hub)          │  │  │
│  │  │  ┌──────────────┐  ┌─────────────┐  ┌────────┐  │  │  │
│  │  │  │AutoProcessor │  │VisionEncoder│  │Decoder │  │  │  │
│  │  │  │  (tokenize)  │  │ (read img)  │  │(stream)│  │  │  │
│  │  │  └──────────────┘  └─────────────┘  └────────┘  │  │  │
│  │  └─────────────────────────────────────────────────┘  │  │
│  └───────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
```

1. **First load**: ~500MB–1GB model downloads to your browser cache (IndexedDB). This is a one-time cost.
2. **Subsequent loads**: Model loads from cache instantly (no re-download).
3. **Inference**: Runs on **WebGPU** (fast, uses your GPU) with automatic fallback to **WASM** (slower, CPU-only).
4. **Output**: Model streams structured JSON with scores, captions, and tips. The UI parses and animates the results.

### Model Details

| Property | Value |
|----------|-------|
| Model | `onnx-community/Qwen3.5-0.8B-ONNX` |
| Quantization | `q4` decoder + `fp16`/`fp32` vision encoder |
| Runtime | `@huggingface/transformers` (Transformers.js) |
| Download size | ~500MB–1GB (one time) |
| Inference speed | ~40–90s first run; faster with WebGPU |

---

## 📱 PWA Install

**post ready?** is a fully installable Progressive Web App.

| Platform | How to Install |
|----------|----------------|
| **Android/Chrome** | Tap the install banner or *⋮ → Add to Home Screen* |
| **iOS/Safari** | Tap *Share → Add to Home Screen* |
| **Desktop/Chrome** | Click the install icon in the address bar |

After install, the app loads instantly and works offline (model stays cached).
---

## 🛡️ Privacy & Security

- ✅ **Zero telemetry** — no analytics, no tracking, no logging
- ✅ **Zero uploads** — images never leave your device
- ✅ **Zero accounts** — no sign-in, no profile
- ✅ **Open source** — you can read every line of code in the HTML
- ✅ **Offline capable** — after first load, works with no internet
- ✅ **HTTPS only** — camera APIs require secure context

The model runs entirely inside your browser using WebAssembly + WebGPU APIs. Your photos are processed in memory and discarded when you close the tab.

---

## ⚡ Browser Compatibility

| Browser | Support | Notes |
|---------|---------|-------|
| Chrome 113+ | ✅ Full | WebGPU + WASM |
| Edge 113+ | ✅ Full | WebGPU + WASM |
| Firefox | ⚠️ Partial | WASM only (no WebGPU yet) |
| Safari 18+ | ⚠️ Partial | WebGPU experimental |
| Mobile Chrome | ✅ Good | WASM (WebGPU device-dependent) |
| Mobile Safari | ⚠️ Limited | WASM fallback, slower |

WebGPU is strongly recommended for inference speeds under 60s. On WASM, expect 2–5 minutes per analysis.

---

## 🐛 Troubleshooting

### Model won't load / stuck at downloading
- Check your network connection
- Try disabling browser extensions (some block CDN fetches)
- Clear site data and reload: *Settings → Privacy → Clear browsing data*

### Camera not working in Live mode
- Must be served over `https://` or `localhost` — `file://` URLs block camera APIs
- Grant camera permissions in browser settings
- On iOS, use Safari (not Chrome) for camera access

### Analysis takes forever
- First inference always takes 40–90s+ for shader compilation
- Subsequent analyses are faster
- Enable WebGPU: ensure Chrome Flags → `#enable-unsafe-webgpu` is on (Chrome < 113)

### JSON parse errors / fallback scores
- Small models occasionally produce malformed JSON — the app catches this and shows fallback 50/100 scores
- Try again — results vary slightly each run


---

## 🤝 Contributing

Contributions are welcome! This is a fun project, so keep it light and creative.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

Please ensure your changes don't break the single-file nature of the app (unless absolutely necessary).

---

## 📄 License

MIT License — do whatever you want with it. Attribution appreciated but not required.

```
Copyright (c) 2024 post ready?

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
```

---

## 🙏 Acknowledgments

- [Hugging Face](https://huggingface.co/) for Transformers.js and the model hosting
- [ONNX Runtime](https://onnxruntime.ai/) for the inference engine
- [Qwen](https://github.com/QwenLM/Qwen) team for the amazing vision-language model

---

<p align="center">
  Made with ✨ and zero backends<br/>
  <strong>post ready?</strong> — because your camera roll deserves an honest friend<br/><br/>
  <a href="https://2796gaurav.github.io/post_ready/">🚀 Try it Live</a>
</p>
