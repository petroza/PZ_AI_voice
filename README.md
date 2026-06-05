# PZ Voice Studio

PZ Voice Studio is a local Windows text-to-audio studio for generating narration, voice-over drafts and WAV/MP3 outputs from text.

The project is designed as a one-click Windows package: run `RUN_PZ_VOICE_STUDIO.bat`, open the local web UI, type or paste narration text, choose a voice engine/preset, and generate audio locally.

## Current build

This repository contains the current Voice Studio build with:

- local browser UI on `http://127.0.0.1:7867`
- one-click Windows installer / launcher
- text-to-WAV generation
- optional MP3 export
- queue-based generation
- waveform preview and click-to-play position
- GPU / CPU status display
- Piper fixed voice library for reliable male/female voice selection
- Chatterbox 500M quality mode
- Chatterbox Turbo 350M reference voice cloning mode
- Chatterbox Multilingual 500M mode
- custom voice presets saved locally
- default settings saved for the next generation
- Ctrl / Shift multiselect in the queue
- right-click queue menu for output download, settings reuse and deletion
- ZIP download for multiple finished jobs

## Quick start

1. Download or clone this repository.
2. On Windows, run:

```bat
RUN_PZ_VOICE_STUDIO.bat
```

3. Wait for the first installation to finish.
4. The app opens in the browser at:

```text
http://127.0.0.1:7867
```

After the first installation, you can start the already installed worker with:

```bat
START_INSTALLED_WORKER.bat
```

## Recommended first test

1. Select `Piper voice library - fixed voices`.
2. Select a voice such as `Piper Female US - Amy` or `Piper Male US - Ryan`.
3. Click `Download selected` in the model section.
4. Paste text into the Voice-over text box.
5. Click `Add + start`.

The first voice download can take a while. Downloaded voices are cached locally in `models/piper`.

## Engines

### Piper voice library

Piper is used for fast local generation and reliable fixed voice selection. This build downloads selected ONNX voices from the public `rhasspy/piper-voices` Hugging Face repository only when the user clicks download.

### Chatterbox

Chatterbox is used for premium local generation and reference voice cloning. Native Chatterbox generation does not guarantee deterministic male/female voice selection. For reliable voice identity, use a short reference WAV/MP3 clip in the cloning mode.

## Project structure

```text
app/app.py                         FastAPI backend and generation logic
app/web/index.html                 Browser UI
app/generate_worker.py             CLI helper worker
app/requirements_core.txt          Core Python dependencies
app/requirements_chatterbox.txt    Optional Chatterbox dependencies
RUN_PZ_VOICE_STUDIO.bat            One-click install and start script
START_INSTALLED_WORKER.bat         Start script after installation
docs/LEGAL_AND_SOURCES.md          Legal notes and upstream sources
docs/MODEL_NOTES.md                Model behavior notes
docs/SAMPLE_SOURCES.md             Sample/output notes
voices/README_reference_clips.txt  Reference clip guidance
samples/README_samples.txt         Local sample folder notes
```

Runtime folders are created locally and are intentionally not committed:

```text
_runtime/
models/
outputs/
samples/*.wav
samples/*.mp3
data/*.json
data/logs/
```

## Legal and source notes

This repository contains the application wrapper, UI, launcher scripts and documentation. It does not bundle third-party model weights, public voice samples, private voices, generated outputs or copyrighted reference clips.

Third-party models and packages are downloaded from their upstream sources by the user's local installation. Check `docs/LEGAL_AND_SOURCES.md` for the source list and usage notes.

Voice cloning should only be used with recordings that the user owns, has licensed, or is otherwise allowed to process.

## License

Application code in this repository is released under the MIT License. Third-party dependencies, models and downloaded voice weights remain under their own upstream licenses and terms.
