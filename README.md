# llama-cpp-python-tanya

> **CUDA-accelerated Python bindings for `llama.cpp`, integrated into Tanya — a local tactical AI assistant.**

This repository contains a modified, performance-optimized version of [`llama-cpp-python`](https://github.com/abetlen/llama-cpp-python) configured to run on NVIDIA GPUs using GGML_CUDA. It powers the LLM runtime for **TANYA** (Tactical Artificial Neural-Yielded Assistant), a locally-hosted voice-controlled AI system developed for high-speed interaction, autonomous speech, and real-time CUDA inference.

---

## 🧠 What Is Tanya?

Tanya is a real-time AI assistant built to run **locally on your machine**, leveraging a GPU-accelerated `llama.cpp` backend. She connects:
- 🔹 CUDA-compiled `llama.cpp`
- 🔹 `llama-cpp-python` for Python integration
- 🔹 `edge-tts` for text-to-speech
- 🔹 `speech_recognition` or Whisper for voice input
- 🔹 Custom system memory & personality modules

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
