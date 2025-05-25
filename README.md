# llama-cpp-python-tanya

> **CUDA-accelerated Python bindings for `llama.cpp`, integrated into Tanya — a local tactical AI assistant.**

This repository contains a modified, performance-optimized version of [`llama-cpp-python`](https://github.com/abetlen/llama-cpp-python) configured to run on NVIDIA GPUs using GGML_CUDA. It powers the LLM runtime for **TANYA** (Tactical Artificial Neural-Yielded Assistant), a locally-hosted voice-controlled AI system developed for high-speed interaction, autonomous speech, and real-time CUDA inference.

---
---

## 🖥️ Development Notes & System Environment

This entire project is developed and tested on a **2017 Alienware Aurora R6** desktop system. It was important to build on legacy hardware to show that CUDA-accelerated AI systems like Tanya can run on older machines — and that users with more modern hardware will experience even better performance.

**Base System:**
- 💻 Model: Alienware Aurora R6
- 🧠 CPU: Intel Core i7-7700K @ 4.20GHz
- 🎮 GPU: NVIDIA GeForce RTX 3060 Ti (Driver Model: WDDM 3.0)
- 🧬 RAM: 32 GB
- 💾 Storage: NVMe SSD
- 🧱 OS: Windows 10 Pro (Build 19045)

Despite being several generations behind the latest desktop platforms, this configuration is more than capable of running local LLM inference, real-time TTS, and Whisper audio processing with CUDA acceleration.

---

## 🎯 Purpose & Vision

This project is not intended for commercial use or production deployment. It’s a **learning-focused, hobby-level build** made to explore what’s possible with open-source tools and modern AI models.

I am **not a professional developer** — I have no formal experience with Python. Everything in this repository was built using the help of **OpenAI’s ChatGPT**, which I’ve used to generate, troubleshoot, and iterate code in real time.

**Tanya is being built purely for fun, learning, and exploration.**

If you’re here following the same dream — welcome. You don’t have to be a coder to start building something amazing. Just start asking the right questions and go from there.

---

---

## 🧠 What Is Tanya?

**TANYA** stands for **Tactical Artificial Neural-Yielded Assistant** — a fully local, GPU-powered AI system designed to run independently on your hardware with no internet dependency, no OpenAI API, and no external servers.

Tanya is more than a chatbot. She is a **customizable voice-interactive digital assistant** built with:

- A CUDA-accelerated LLM backend via `llama.cpp`
- Fast and lightweight Python bindings using `llama-cpp-python`
- Seamless integration with TTS (via `edge-tts`) for lifelike responses
- Optional voice recognition (via `speech_recognition` or Whisper)
- Dynamic personality and behavioral modes (elegant, flirty, assertive)
- Runtime memory management to simulate ongoing conversation
- Modular architecture for easy expansion and evolution

Tanya is designed to be:
- 🔒 **Fully private** (runs 100% offline)
- 🎙️ **Voice-controllable**
- 💻 **Resource-conscious** (capable on older systems)
- ❤️ **Fun to interact with**, especially for creative and experimental use cases

Whether you're building a virtual companion, a self-hosted digital secretary, or just experimenting with AI locally — Tanya gives you a fully open, real-time assistant framework to build from.

---


---

## 🚀 Features

- ✅ CUDA support via `GGML_CUDA=ON` build
- ✅ Integrated with Tanya’s speech output and memory stack
- ✅ Works offline — no OpenAI, no cloud, fully local
- ✅ Ready to plug into `TANYA_OS.py`

---

## 📦 Requirements

- Python 3.10+
- CUDA Toolkit 11.8 or 12.x
- Visual Studio 2022 with C++ Desktop Tools
- `llama.cpp` compiled with `GGML_CUDA=ON`
- ffmpeg (for `pydub` or TTS playback)

---

## 🛠️ Build Instructions

1. Clone this repo:
```bash
git clone https://github.com/YOUR_USERNAME/llama-cpp-python-tanya.git
cd llama-cpp-python-tanya
```

2. Clone the CUDA-enabled `llama.cpp`:
```bash
git clone https://github.com/ggerganov/llama.cpp
```

3. Replace the vendor folder:
```bash
rm -rf ./vendor/llama.cpp
mv ../llama.cpp ./vendor/llama.cpp
```

4. Set CUDA build flags:
```powershell
$env:GGML_CUDA = "1"
$env:CMAKE_ARGS = "-DGGML_CUDA=ON"
```

5. Build it:
```bash
pip install . --force-reinstall --no-binary llama-cpp-python
```

6. Copy the compiled `llama.dll` into:
```
llama_cpp/lib/llama.dll
```

---

## 🔍 Verify GPU Backend

```python
from llama_cpp import llama_backend_cuda_supported
print("CUDA Supported:", llama_backend_cuda_supported())
```

---

## 📜 License

This project inherits the MIT license from `llama-cpp-python`. Tanya-specific modifications © 2024 Kenneth Salmon (MCOGraphics).

---

## ❤️ Credits

This project exists because of the outstanding open-source work of two creators whose efforts made it possible to bring Tanya to life:

- **[@ggerganov](https://github.com/ggerganov)** – for creating [`llama.cpp`](https://github.com/ggerganov/llama.cpp), a fast and lightweight C++ inference engine for LLaMA models. His dedication to performance and simplicity forms the backbone of the local LLM runtime used here.

- **[@abetlen](https://github.com/abetlen)** – for building [`llama-cpp-python`](https://github.com/abetlen/llama-cpp-python), a powerful and user-friendly Python binding for `llama.cpp`. His work bridges C++ with Python seamlessly, enabling direct integration into AI assistant systems like Tanya.

Both of these projects are distributed under the MIT license, and this fork extends their efforts only to adapt for CUDA acceleration and voice-based AI assistant usage.

**Respect and thanks to both authors for their incredible contributions to the open-source AI community.**

---
