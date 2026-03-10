<div align="center">

```
███╗   ███╗ █████╗ ███╗   ██╗██╗███╗   ███╗
████╗ ████║██╔══██╗████╗  ██║██║████╗ ████║
██╔████╔██║███████║██╔██╗ ██║██║██╔████╔██║
██║╚██╔╝██║██╔══██║██║╚██╗██║██║██║╚██╔╝██║
██║ ╚═╝ ██║██║  ██║██║ ╚████║██║██║ ╚═╝ ██║
╚═╝     ╚═╝╚═╝  ╚═╝╚═╝  ╚═══╝╚═╝╚═╝     ╚═╝
```

### **The Painless Setup Guide** · 2026 Edition

[![Built with uv](https://img.shields.io/badge/built%20with-uv-DE5FE9?style=flat-square&logo=astral)](https://docs.astral.sh/uv/)
[![Python](https://img.shields.io/badge/Python-3.11%2B-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![Manim CE](https://img.shields.io/badge/Manim-Community%20Edition-00b4d8?style=flat-square)](https://www.manim.community/)

*Stop wasting 5 hours on a broken setup. This guide exists so you don't have to.*

</div>

---

## 📋 Table of Contents

- [The Right Way (Official Docs)](#-1-the-right-way-official-docs)
- [The Quick-Start Video](#-2-the-quick-start-video)
- [Battle-Tested Deductions](#-3-battle-tested-deductions-the-real-world-advice)
- [Learning Resources](#-4-learning-resources)
- [Quick Command Cheat Sheet](#️-5-quick-command-cheat-sheet)

---

## 📖 1. The Right Way (Official Docs)

> **Start here. Always.**

The official documentation is the single most up-to-date and accurate source for installation. Everything in this repo is *supplementary* - the official guide is the source of truth.

🔗 **[Manim Installation with `uv` → Official Guide](https://docs.manim.community/en/stable/installation.html)**

---

## 🎥 2. The Quick-Start Video

If you prefer to see the process live and skip the common "head-smacking" hurdles, this updated walkthrough has you covered:

🔗 **[How to Install Manim on Windows (Updated 2025/26) → Video Tutorial](https://www.youtube.com/)**

---

## 🧠 3. Battle-Tested Deductions *(The "Real World" Advice)*

### ⚡ The 2022 → 2026 Shift

| Era | What you had to do | Pain Level |
|-----|--------------------|------------|
| 🕰️ **2022** | Chocolatey + manual FFmpeg + dozens of system-level installers polluting your global PATH | 🔥🔥🔥🔥🔥 |
| ✅ **2026** | Install `uv`. That's pretty much it. | 🟢 Minimal |

**`uv`** is a Rust-based tool that handles Python versions and virtual environments automatically. It replaces Chocolatey, `pip`, `pyenv`, `virtualenv`, and half your sanity.

---

### 📁 The "Manimation" Folder Trap

Many older tutorials insist on a specific `manimation/` folder or a rigid project structure. **Ignore them.**

```
❌  Old way:  C:\Users\You\manimation\project\src\scenes\...
✅  New way:  Anywhere you want.
```

**The actual workflow:**

```sh
mkdir my_animations
cd my_animations
uv init
uv add manim
```

> 💡 **If `manim checkhealth` fails**, it's almost always an **interpreter mismatch**.
> Make sure VS Code is pointing to the `.venv` you just created — not your global Python.

---

### 🧮 The LaTeX / MiKTeX Headache

If your health check flags a LaTeX error, don't reinstall everything. Follow these three steps:

```
Step 1 → Open MiKTeX Console
Step 2 → Run ALL pending updates
Step 3 → Set "Always install missing packages on-the-fly" → YES
```

> Most "broken" LaTeX installations are just MiKTeX silently waiting for a permission prompt you never saw.

---

## 📚 4. Learning Resources

| Goal | Resource |
|------|----------|
| 🚀 **Get something working fast** | Ask Claude or any LLM to generate starter code. Manim's syntax is descriptive enough that AI handles `Square → Circle` transitions and basic graphs surprisingly well. |
| 🎓 **Actually learn Manim** | **[Manim Introduction — Slama.dev](https://slama.dev/manim/introduction/)** — a well-structured, human-written tutorial series. |
| 📖 **Deep reference** | **[Official Manim CE Docs](https://docs.manim.community/)** |

---

## 🛠️ 5. Quick Command Cheat Sheet

### Installation

```powershell
# Install uv (Windows — run in PowerShell)
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

```bash
# Install uv (macOS / Linux)
curl -LsSf https://astral.sh/uv/install.sh | sh
```

### Project Setup

```bash
# Create & enter your project
uv init my_animations && cd my_animations

# Add Manim to the project
uv add manim

# Verify everything is healthy
uv run manim checkhealth
```

### Rendering

```bash
# Low quality — fast preview (great for iteration)
uv run manim -pql main.py YourSceneName

# Medium quality
uv run manim -pqm main.py YourSceneName

# High quality — production render
uv run manim -pqh main.py YourSceneName

# 4K render
uv run manim -pqk main.py YourSceneName
```

### Quality Flags Reference

| Flag | Quality | Resolution | Use When |
|------|---------|------------|----------|
| `-ql` | Low | 480p 15fps | Drafting / debugging |
| `-qm` | Medium | 720p 30fps | General preview |
| `-qh` | High | 1080p 60fps | Final output |
| `-qk` | 4K | 2160p 60fps | Publishing |

### Useful Extras

```bash
# Render without auto-opening the file
uv run manim -ql main.py YourSceneName --disable_caching

# Save output to a specific folder
uv run manim -ql main.py YourSceneName --media_dir ./output

# List all scenes in a file
uv run manim main.py --list_scenes
```

---

<div align="center">

**Found this useful?** Drop a ⭐ — it helps others find this guide.

*Contributions welcome. Open a PR or issue if something's outdated.*

</div>
