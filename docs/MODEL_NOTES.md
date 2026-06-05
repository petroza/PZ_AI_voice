# Model notes

This build uses two modes.

## Piper voice library

Piper uses local ONNX voices. It is the reliable mode for fixed male/female voice selection. Each voice is downloaded once from the public rhasspy/piper-voices Hugging Face repository and cached locally.

## Chatterbox

Chatterbox is kept for premium generation and reference voice cloning. Native Chatterbox mode does not provide a deterministic built-in male/female picker. For a reliable Chatterbox voice, upload a 5-15 second reference WAV/MP3 and use Chatterbox Turbo clone.

## Removed

Kokoro 82M fast and eSpeak setup were removed from this build because they were unstable in the previous Windows package.
