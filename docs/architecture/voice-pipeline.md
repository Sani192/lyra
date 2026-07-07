# Voice Pipeline Architecture

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative architectural design, latency budgets, and interface specifications for Lyra's voice processing pipeline.

## Purpose

Define the real-time voice streaming pipeline, specifying audio formats, external speech processing adapters (STT/TTS), Voice Activity Detection (VAD) thresholds, and strict latency budgets required to maintain fluid conversation pacing.

## Voice Pipeline Flow

Real-time audio processing flows asynchronously through a multi-stage translation pipeline:

```
[WebSocket Client] ===(WSS Audio Packets)===> [ WebSocket Adapter ]
                                                     |
                                                     v (Push binary)
[Deepgram / Whisper] <===(Streaming STT)========== [ STT Adapter ]
                                                     |
                                                     v (Text output)
                                              [ NLU/LLM Engine ]
                                                     |
                                                     v (Selected intent)
                                              [ Workflow Engine ]
                                                     |
                                                     v (Invoke capability)
                                              [ Consumer API ]
                                                     |
                                                     v (Return payload)
                                              [ LLM / TTS Agent ]
                                                     |
                                                     v (Dialogue text)
[Google TTS / Cartesia] <==(Synthesize wave)===== [ TTS Adapter ]
                                                     |
                                                     v (Streaming audio)
[WebSocket Client] <===(WSS Audio Packets)==== [ WebSocket Adapter ]
```

### 1. Latency Budgets
To simulate natural human-to-human turn pacing, the total roundtrip turn latency (from the moment the user stops speaking to the first byte of system audio feedback) must not exceed **1,000 milliseconds**.

| Segment | Target Latency | Maximum SLA | Responsibility |
| --- | --- | --- | --- |
| **STT Conversion** | 150ms | 300ms | External STT provider (Deepgram) |
| **NLU / Intent Classifier** | 100ms | 200ms | Internal classifier models |
| **LLM Response Generation** | 450ms | 800ms | OpenAI / Anthropic models |
| **TTS Synthesis** | 150ms | 300ms | External TTS provider (Google / Cartesia) |
| **Orchestration & Network** | 150ms | 250ms | Lyra WebSocket adapter and message broker |
| **Total Roundtrip Turn** | **1,000ms** | **1,850ms** | **Complete Platform SLA** |

### 2. Audio Formats & Streaming Protocols
The WebSocket adapter accepts and emits audio streams conforming to standard telephony and web codecs:
* **Default Web Protocol:** Raw PCM linear 16-bit, 16kHz sample rate, mono (320kbps uncompressed).
* **Telephony Protocol Adapter:** G.711 mu-law (8kHz sample rate, mono, 64kbps) for integration with SIP trunks and VoIP gateways.
* **Ingress transport:** WebSockets (`wss://`) or WebRTC (for direct browser media channels).

### 3. Voice Activity Detection (VAD)
To ensure the system turns taking is accurate and doesn't cut users off prematurely:
* **VAD Engine:** Instantiated locally inside the WebSocket adapter (e.g. Silero VAD) to run sub-10ms chunk evaluations.
* **Silence Threshold:** The system considers the user to have finished speaking when a continuous silence interval of **400ms** is detected after active speech.
* **Interruption Handling:** If the user speaks while Lyra is streaming TTS audio, the WebSocket adapter immediately sends a `STOP` command to the TTS client, halts outgoing audio frames, and initializes a new conversational turn.
