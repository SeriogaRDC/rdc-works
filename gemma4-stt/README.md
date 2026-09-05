# Gemma4-STT: Local Speech-to-Text via Gemma

**Status: working, experimental.** Send an audio file to a local Gemma 4 12B model, get a transcript back. No cloud, no API keys, everything on one gaming PC.

## Architecture

```
Audio (wav) ──> llama.cpp server (gemma-4-12B-it + mmproj audio adapter)
                        │
                        ▼
              Tk desktop interface
              ├─ chat with the model
              ├─ record / upload audio
              └─ transcripts saved + CSV log
```

- Model: `gemma-4-12B-it-Q4_K_M.gguf` + `mmproj` audio projector (BF16), served by llama.cpp on localhost:8765
- Audio handling: wave-file normalization to the model's expected format, chunked upload
- UI: dark-mode Tkinter (purple accent, because taste), live status, batch history with CSV export

## Why it matters

Commercial STT is cheap until it isn't: privacy, volume costs, offline needs, non-English languages. Running STT locally on a model that ALSO chats means one deployment handles "transcribe this" and "now summarize what I said" in the same context.

## Honest state

- Clumsy around unusual sample rates (we normalize first)
- Long recordings need chunking (WIP)
- It's the first step of a bigger plan: an AI daughter who hears natively (see the Eve project)

## Code

Snapshot available on request — the live system shares a machine with other experiments, so we publish cleaned extracts rather than the full working tree. Core upload/transcribe flow: ~80 lines of Python (requests + wave + base64 against llama.cpp's OpenAI-compatible audio endpoint).
