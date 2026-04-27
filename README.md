# 🎵 Beat Painter

> Draw music. Every stroke is a note. Every note leaves a trail.

![Beat Painter](https://img.shields.io/badge/status-live-brightgreen) ![HTML](https://img.shields.io/badge/built%20with-HTML%20%2F%20Web%20Audio-orange) ![No Dependencies](https://img.shields.io/badge/dependencies-zero-green) ![License](https://img.shields.io/badge/license-MIT-lightgrey)

---

## ✨ What It Does

Beat Painter is a browser-based creative toy that turns your mouse strokes into live music. Draw slow curves for ambient drones, scribble fast for chaotic percussion, or carefully trace a melody one note at a time.

The **Y-axis is your pitch**. The **speed of your stroke** is your rhythm. The **colour** is your mood.

---

## 🚀 Live Demo

**[→ Try it on GitHub Pages](https://chethanprem.github.io/beat-painter)**

---

## 🎮 How to Play

| Action | Result |
|--------|--------|
| **Draw** on the canvas | Plays notes, leaves glowing trails |
| **Draw high** on canvas | Higher pitch notes |
| **Draw low** on canvas | Lower pitch notes |
| **Draw fast** | Rapid note bursts |
| **Draw slow** | Sustained, spaced notes |
| `Space` | Clear the canvas |
| `R` | Start / stop recording |

---

## 🎛️ Controls

### Scale
Choose the musical scale that all notes snap to:

| Scale | Character |
|-------|-----------|
| **Pentatonic** | Safe, always sounds good — great for beginners |
| **Major** | Bright and happy |
| **Minor** | Moody and emotional |
| **Dorian** | Jazz-flavoured minor |
| **Blues** | Gritty, soulful |
| **Chromatic** | All 12 notes — no rules |

### Instrument
Six synth voices built with the Web Audio API:

| Instrument | Sound Character |
|------------|----------------|
| 🎹 Piano | Triangle + sine blend, natural decay |
| 🎛️ Synth | Sawtooth + square, punchy attack |
| 🪘 Marimba | Short sine burst, percussive |
| 🎵 Flute | Soft sine, slow attack, long release |
| ⚡ Electric | Sawtooth detune, sharp and bright |
| 🔔 Bells | Long-decay sine, shimmery |

### Effects
Stack audio effects on your sound:

- **Reverb** — synthetic convolution reverb (2.5s tail)
- **Delay** — echo with 0.28s delay time and 38% feedback
- **Distort** — waveshaper soft-clipping
- **Chorus** — LFO-modulated delay for thickness

### Colour
8 colour options including **🌈 Auto** mode which maps pitch → hue automatically — so you can literally see the melody.

### Brush Size
Controls stroke thickness and note sustain duration. Bigger brush = longer notes.

### Note Speed
Controls how frequently notes trigger as you draw. Lower = spacious, Higher = rapid-fire.

---

## ⏺️ Recording & Playback

1. Hit **Record** (or press `R`)
2. Draw your melody on the canvas
3. Hit **Stop**
4. Your exact timing plays back automatically

Recording captures note frequency and timestamp — playback re-synthesises everything fresh through the audio engine.

---

## 🔊 How the Audio Works

```
Mouse position (Y)
       ↓
Scale quantisation → frequency (Hz)
       ↓
Dual oscillator (osc1 + osc2, slight detune)
       ↓
ADSR envelope (instrument-specific)
       ↓
FX chain (distort → chorus → reverb / delay)
       ↓
Master gain → AudioContext destination
```

Built entirely on the **Web Audio API** — no audio files, no libraries. Every sound is synthesised in real time from oscillators and gain nodes.

---

## 📁 Project Structure

```
beat-painter/
├── index.html        # Single-file app — everything lives here
└── README.md
```

Zero build steps. Zero npm installs. Just open and draw.

---

## 🔧 Run Locally

```bash
git clone https://github.com/chethanprem/beat-painter.git
cd beat-painter
open index.html
```

> ✅ Works from `file://` — no server required. Web Audio API is fully local.

---

## 🌐 Deploy to GitHub Pages

1. Push `index.html` to the `main` branch
2. Go to **Settings → Pages → Source → main / root**
3. Live at `https://chethanprem.github.io/beat-painter`

---

## 🎨 Visual Features

- **Glowing trails** with slow canvas fade — each colour maps to a pitch range
- **Ripple rings** that expand outward on every note trigger
- **Note popup** — the note name flashes at your cursor position
- **Waveform visualiser** in the bottom bar that pulses with each note
- **Background pitch grid** — subtle horizontal bands show the note zones
- **Light / Dark theme** toggle
- **Trail toggle** — switch between glowing trails and clean strokes

---

## 🧠 Technical Notes

- **Oscillator detuning** — every instrument uses two oscillators with a +2 cent frequency offset for natural width
- **ADSR per instrument** — attack, decay, and release times are tuned individually for each voice character
- **Note throttling** — adjustable minimum gap between note triggers prevents accidental chord clusters at high speeds
- **Scale quantisation** — Y position maps to a 3-octave range (C3–C5) snapped to the chosen scale's intervals
- **Reverb** — synthetic impulse response generated procedurally (no audio file required)

---

## 📄 License

MIT — use it, fork it, make music with it.

---

*Built by [Chethan Prem](https://github.com/chethanprem)*
