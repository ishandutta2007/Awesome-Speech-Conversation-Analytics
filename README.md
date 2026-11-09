# Awesome-Speech-Conversation-Analytics

# Awesome Speech & Conversation Analytics

> A curated list of top Speech and Conversation Analytics platforms — both SaaS/Hosted commercial solutions and open-source alternatives for transcribing, analyzing, and extracting insights from voice conversations, sales calls, and customer interactions.
> 🌟 Star this repo if you find it useful! 🌟

---

## 📋 Table of Contents

- [SaaS / Hosted Platforms](#-saas--hosted-platforms)
  - [Gong](#gong)
  - [Chorus by ZoomInfo](#chorus-by-zoominfo)
  - [Clari Copilot](#clari-copilot)
  - [Invoca](#invoca)
  - [CallMiner](#callminer)
  - [Observe.AI](#observeai)
  - [Verint](#verint)
  - [Tethr](#tethr)
  - [Balto](#balto)
- [Open-Source Software](#-open-source-software)
  - [Percept](#percept)
  - [CallHarness SDK](#callharness-sdk)
  - [CallSense (ML-voice-lead-analysis)](#callsense-ml-voice-lead-analysis)
  - [diarizers](#diarizers)
  - [Debrief](#debrief)
  - [Surivoice](#surivoice)
  - [VoiceSummary](#voicesummary)
  - [WhoSpeaks](#whospeaks)
  - [CohereX](#coherex)
- [Comparison at a Glance](#-comparison-at-a-glance)
- [Contributing](#-contributing)

---

## 🟦 SaaS / Hosted Platforms

Commercial, cloud-hosted Speech and Conversation Analytics platforms. These are not open-source but are included as reference points for feature comparison.

### Gong
**Type:** Revenue intelligence and sales conversation analytics
Gong is the category-defining revenue intelligence platform, analyzing sales calls, emails, and meetings to surface deal risks, coaching opportunities, and revenue insights. It provides call recording, transcription, sentiment analysis, talk-time metrics, and deal progression tracking. An MCP server integration is available for accessing Gong's analytics through AI assistants [citation:8].

### Chorus by ZoomInfo
**Type:** Conversation intelligence for sales teams
Chorus (part of ZoomInfo) provides call recording, transcription, and analysis for sales conversations, with deal risk detection, coaching insights, and integration with CRM data. Positioned as a direct competitor to Gong.

### Clari Copilot
**Type:** Revenue operations with conversation intelligence
Clari Copilot (formerly Wingman) provides call recording, transcription, and real-time coaching for sales teams, integrated into Clari's broader revenue operations platform.

### Invoca
**Type:** Call intelligence for marketing and contact centers
Invoca specializes in analyzing inbound phone calls for marketing attribution, lead qualification, and contact center optimization. It uses AI to extract intent, sentiment, and outcome from voice conversations.

### CallMiner
**Type:** Enterprise speech analytics
CallMiner provides AI-powered speech and text analytics for contact centers, covering compliance, agent performance, and customer experience. It is a long-standing enterprise standard for large-scale conversation analytics.

### Observe.AI
**Type:** Contact center AI with agent assistance
Observe.AI provides conversation intelligence for contact centers, including automated QA, agent coaching, and real-time assistance. Focused on improving agent performance and customer satisfaction at scale.

### Verint
**Type:** Enterprise workforce engagement and speech analytics
Verint provides speech analytics as part of its broader workforce engagement management suite, covering compliance, quality, and customer experience for large contact centers.

### Tethr
**Type:** AI-powered conversation analytics for contact centers
Tethr analyzes customer conversations to surface insights on effort, sentiment, and operational performance. Positioned for enterprises wanting to understand what drives customer loyalty and dissatisfaction from voice interactions.

### Balto
**Type:** Real-time guidance and conversation analytics
Balto provides real-time coaching and guidance for contact center agents during live calls, alongside post-call analytics. Focused on improving agent performance through in-the-moment suggestions.

---

## 🟩 Open-Source Software

Self-hosted, community-driven Speech and Conversation Analytics tools. The open-source ecosystem is **fragmented** across transcription pipelines, diarization libraries, call analytics SDKs, and sales-focused analysis platforms.

### Percept
**Stack:** Python | **License:** Open Source (per PyPI)
Percept is a local-first conversation intelligence pipeline that captures, transcribes, and analyzes spoken conversations, with a web dashboard and MCP server for AI assistant integration [citation:1]. Features include wake-word detection, speaker authorization/revocation, full-text and semantic search across transcripts, entity graph extraction, and a three-tier transcription strategy (Omi on-device, faster-whisper local, or webhook sources). It supports syncing from Granola, Zoom, and ChatGPT Actions. The MCP server exposes tools including `percept_search`, `percept_transcripts`, and `percept_speakers` for Claude Desktop integration [citation:1]. **Note:** Percept is designed for personal/team conversation capture (meetings, voice notes) rather than contact center analytics.

### CallHarness SDK
**Stack:** Python | **License:** Open Source (per PyPI)
CallHarness is an open-source SDK for **voice AI agent call analytics**, sending agent calls to a self-hosted server that runs post-call LLM analysis (summary, sentiment, outcome, why a call transferred or didn't complete) and displays results on a dashboard [citation:2]. It integrates with Pipecat pipelines, capturing per-turn STT/LLM/TTS latency, interruptions, tool calls, and transfers. Transcripts stay on your own infrastructure. **Limitation:** Focused on analyzing AI agent calls, not human-to-human sales conversations.

### CallSense (ML-voice-lead-analysis)
**Stack:** Python / FastAPI / React | **License:** Open Source (per GitHub)
CallSense is a self-hosted, deterministic **sales call lead-scoring engine** that turns recorded call transcripts into explainable lead scores, objection detection, buyer intent signals, and next-best-action recommendations [citation:3][citation:13]. Every score component is traceable to exact transcript quotes — a rep can interrogate why a lead scored 73.9/100. It runs on Python 3.11+ with no GPU, no model download, and no external database. The analysis engine is pure Python (no PyTorch/spaCy), processing a 40-turn call in ~2.4ms [citation:3]. **Trade-off:** Requires transcripts as input (it does not transcribe audio); no real-time analysis; sentiment is lexicon-based by default with an optional transformer upgrade.

### diarizers
**Stack:** Python / PyTorch | **License:** Apache-2.0
diarizers is a unified open-source ASR, speaker diarization, and DiarizationLM post-processing package implementing the algorithms from Google's DiarizationLM papers [citation:4]. It combines Whisper or Qwen ASR, pyannote segmentation, SpeechBrain embeddings, spectral clustering, and LLM-based diarization refinement (via DiarizationLM-Gemma-4-E4B). Supports CPU (llama.cpp GGUF) and GPU (Safetensors) inference. **Focus:** Speaker diarization quality rather than conversation analytics — it produces who-said-what transcripts, not sentiment or outcome analysis.

### Debrief
**Stack:** Electron / React / Python | **License:** Open Source (per GitHub)
Debrief is a privacy-first conversation analysis desktop app that transcribes audio/video locally using faster-whisper, performs speaker diarization with pyannote.audio 3.1, and runs AI analysis via local Ollama or your choice of OpenAI/Anthropic/Groq/Gemini/OpenRouter . Model weights are bundled, so no HuggingFace token is required at runtime. Cross-platform (macOS, Windows, Linux) with FFmpeg bundled. **Trade-off:** Desktop app rather than a server platform; analysis depth depends on the LLM you connect.

### Surivoice
**Stack:** Python / Whisper / pyannote | **License:** Open Source (per PyPI)
Surivoice is a local-first speech transcription tool with speaker diarization, taking video/audio files and outputting structured Markdown transcripts with timestamps [citation:9]. It uses faster-whisper for transcription and pyannote.audio for diarization, with GPU acceleration and CPU fallback. Provides both a GUI and CLI. **Trade-off:** Transcription and diarization only — no sentiment, outcome, or conversation analytics.

### VoiceSummary
**Stack:** Python / FastAPI / Next.js / PostgreSQL | **License:** MIT
VoiceSummary is an open-source AI database for voice agent transcripts, providing call analysis, insights, extraction, and labeling [citation:7]. It offers API endpoints for call records, audio processing, AI data extraction pipelines, and agent comparisons. Use cases include call quality assessment, sentiment analysis, and structured data extraction from transcripts. **Focus:** Voice agent analytics rather than human sales conversation intelligence.

### WhoSpeaks
**Stack:** Python / PyTorch | **License:** Open Source (per PyPI)
WhoSpeaks provides local, GPU-accelerated speaker diarization with a low-latency live preview path and a final high-accuracy transcription path [citation:6]. It is designed for sensitive audio (internal meetings, research interviews, legal/medical workflows) where sending raw conversation audio to another company is not acceptable. Includes a full-screen setup application, speaker library management, and Docker deployment. **Trade-off:** GPU-heavy; diarization accuracy degrades with background noise, crosstalk, and overlapping speech [citation:6].

### CohereX
**Stack:** Python | **License:** Open Source (per PyPI)
CohereX wraps Cohere Transcribe ASR with word-level timestamps and speaker diarization, following the WhisperX pipeline design (VAD → ASR → forced alignment → diarization) [citation:14]. It supports 14 languages and outputs SRT, VTT, TXT, TSV, and JSON. Requires HuggingFace token for pyannote models. **Focus:** High-quality transcription and diarization rather than conversation analytics.

---

## 📊 Comparison at a Glance

| Software | License | Stack | Transcription | Diarization | Analytics | Self-Hosted | Best For |
|----------|---------|-------|---------------|-------------|-----------|-------------|----------|
| **Gong** | Proprietary | Cloud | ✅ | ✅ | ✅ Revenue intel | ❌ | Sales conversation intelligence |
| **CallMiner** | Proprietary | Cloud | ✅ | ✅ | ✅ Enterprise | ❌ | Contact center speech analytics |
| **Observe.AI** | Proprietary | Cloud | ✅ | ✅ | ✅ Agent coaching | ❌ | Contact center QA |
| **Percept** | Open Source | Python | ✅ (Omi/faster-whisper) | ✅ (Speaker auth) | ✅ Search + MCP | ✅ | Personal/team conversation capture |
| **CallHarness** | Open Source | Python | (Agent input) | (Turn-based) | ✅ Post-call LLM | ✅ | Voice AI agent call analytics |
| **CallSense** | Open Source | Python/FastAPI | ❌ (Transcript input) | ❌ | ✅ Lead scoring | ✅ | Explainable sales lead scoring |
| **diarizers** | Apache-2.0 | Python/PyTorch | ✅ (Whisper/Qwen) | ✅ Deep | ❌ | ✅ | High-quality diarization pipeline |
| **Debrief** | Open Source | Electron/Python | ✅ Local Whisper | ✅ pyannote | ✅ LLM choice | ✅ (Desktop) | Privacy-first meeting analysis |
| **VoiceSummary** | MIT | Python/FastAPI | (Agent input) | (Check) | ✅ AI extraction | ✅ | Voice agent transcript database |
| **WhoSpeaks** | Open Source | Python/PyTorch | ✅ Live + final | ✅ Deep | ❌ | ✅ | Sensitive audio diarization |

---

## 🤝 Contributing

Contributions are welcome! If you know of an open-source Speech or Conversation Analytics tool that should be listed here, please open a pull request with:

- Project name and URL
- Brief description (1–2 sentences)
- Stack and license
- Why it stands out

Please ensure the project is actively maintained (releases within the last 12 months) and genuinely open-source. Note that the open-source ecosystem **splits** across several layers: **transcription and diarization pipelines** (diarizers, Surivoice, WhoSpeaks, CohereX) that produce who-said-what transcripts; **conversation capture platforms** (Percept, Debrief) that add search and AI analysis on top; and **sales/agent analytics engines** (CallSense, CallHarness, VoiceSummary) that focus on lead scoring or agent performance. No single open-source project replicates Gong's full breadth of revenue intelligence, CRM integration, and team coaching, but combinations of Percept (capture) + CallSense (sales analysis) cover a meaningful subset of the workflow.

---

## 📄 License

This list is released under CC0 1.0 Universal (Public Domain). The software projects listed retain their respective licenses.

---

⭐ **If this list helped you discover a useful tool, please star the repo!** ⭐
