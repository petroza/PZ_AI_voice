# Legal notes and upstream sources

This project is an application wrapper and local user interface for text-to-audio workflows. The repository should stay clean: no bundled third-party model weights, no private reference voices, no generated outputs and no copyrighted sample clips.

## What is included in this repository

- PZ Voice Studio application code
- Windows BAT launchers
- FastAPI backend
- Browser-based UI
- Requirements files
- Documentation

## What is not included

- Piper voice model weights
- Chatterbox model weights
- User voice reference clips
- Generated WAV/MP3 outputs
- Commercial music, voice-over, broadcast or copyrighted audio assets

These files are downloaded or created locally by the user and are excluded through `.gitignore`.

## Upstream projects and packages

The app can use the following third-party projects. Each dependency remains under its own upstream license and terms.

### Piper TTS

- Project: Piper text-to-speech
- Main project: https://github.com/rhasspy/piper
- Voice models: https://huggingface.co/rhasspy/piper-voices
- Use in this app: fast local TTS with fixed voices
- Notes: selected ONNX voice files are downloaded locally only when requested by the user.

### Chatterbox TTS

- Project/package: Chatterbox TTS
- Python package: `chatterbox-tts`
- Project source should be checked from the package metadata installed by pip.
- Use in this app: higher-quality generation and reference voice cloning.
- Notes: native Chatterbox generation may not provide deterministic male/female voice selection. For stable voice identity, use reference voice cloning with an allowed recording.

### FastAPI

- Project: https://github.com/fastapi/fastapi
- Use in this app: local HTTP backend and API.

### Uvicorn

- Project: https://github.com/encode/uvicorn
- Use in this app: local ASGI server.

### Python audio / numeric packages

- `numpy`
- `scipy`
- `soundfile`
- `pydub`
- `psutil`
- `onnxruntime`
- `torchaudio`

These packages are installed from PyPI by the local installer and remain under their upstream licenses.

## Voice cloning usage

Voice cloning must be used only with audio that the user owns, has licensed, or has permission to process. Do not commit private reference voices to this repository.

Recommended reference clip guidance:

- 5 to 15 seconds of clean speech
- one speaker only
- no background music
- no copyrighted broadcast audio unless you have rights for that use
- WAV or MP3 format

## Output ownership

Generated outputs are created locally in the `outputs/` folder. They are not committed to GitHub. The legal status of generated audio depends on the input text, selected model, reference voice rights and local jurisdiction.

## Repository hygiene

Keep these folders out of Git:

```text
_runtime/
models/
outputs/
data/*.json
data/logs/
samples/*.wav
samples/*.mp3
voices/*.wav
voices/*.mp3
```

Do not upload model files such as `.onnx`, `.pt`, `.pth`, `.safetensors` or `.ckpt` unless the license explicitly allows redistribution and the project has been reviewed for that purpose.
