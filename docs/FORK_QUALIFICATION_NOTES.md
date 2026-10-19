# Fork qualification notes — Pocket TTS as a bounded voice component

**Scope:** public source fork and voice-system interoperability qualification.

```mermaid
flowchart LR
  I["Authorized text input"] --> N["Normalization + language policy"]
  N --> T["Pocket TTS CPU synthesis"]
  T --> W["Audio format/sample-rate checks"]
  W --> A["Optional UI / speech playback"]
  A --> V["Latency, underrun and output acceptance"]
```

Pocket TTS is a small CPU-friendly synthesis component. It can be compared with Kokoro and other voice backends using **separate tests and versioned observations**, not assumed interchangeable by interface name. Track model/voice identity, sample rate, chunking, buffering, cache behavior, input policy, CPU utilization, initialization latency and output quality.

Runtime integration requires independently verifying which service process is running, which caller is wired and which user device actually hears the generated audio. A Python package import, completed CPU test or HTTP 200 is not user acceptance.

Preserve upstream license and attribution; published examples must not embed personal voice recordings, accounts, model-store paths, internal endpoints, tokens or private transcripts.
