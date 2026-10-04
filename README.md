# Awesome-Applied-AI-APIS

# Awesome-Applied-AI-APIS



**Curated List of SaaS Products & Open-Source GitHub Projects**

*Focused on Pre-Trained AI APIs, Multimodal Inference & Self-Hosted Alternatives*

**Last updated: October 2026**



This repository tracks notable **commercial AI API platforms** and **open-source projects** that provide pre-trained models for vision, speech, language, and document intelligence. These tools help developers add AI capabilities without training models from scratch.



**Examples** include Microsoft Cognitive Services, Google Cloud AI APIs, AWS AI Services, IBM Watson APIs, Clarifai, Replicate, Hugging Face Inference API, Deepgram, AssemblyAI, and Rev AI (the category leaders).



**Open-source emphasis**: The open-source ecosystem for applied AI is **mature at the model and serving layers**. **vLLM** and **Text Generation Inference (TGI)** are the two dominant LLM serving frameworks—vLLM leads in high-concurrency throughput by 30-40%, while TGI excels in low-concurrency latency and Hugging Face ecosystem integration . **Faster-Whisper** provides production-grade speech recognition with 3.12% WER and low memory usage, while **WhisperX** adds speaker diarization for complex audio scenarios . **Kokoro-82M** delivers local text-to-speech via an MCP server requiring no API keys . **Real-ESRGAN** and **GFPGAN** power image restoration and face enhancement through projects like **ai-image-restorer** and **restore-lab** . This section documents these production-grade solutions.



Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.



## Table of Contents



- [SaaS/Hosted Platforms](#saas-hosted-platforms)

- [Open-Source GitHub Projects](#open-source-github-projects)

- [How to Contribute](#how-to-contribute)

- [Disclaimer](#disclaimer)



## SaaS/Hosted Platforms



- **[Microsoft Cognitive Services](https://azure.microsoft.com/en-us/products/cognitive-services/)**

  Microsoft's suite of pre-trained AI APIs for vision, speech, language, and decision-making. Includes Computer Vision, Face API, Speech Services, Language Understanding, and Translator.



- **[Google Cloud AI APIs](https://cloud.google.com/products/ai)**

  Google's pre-trained ML APIs including Vision AI, Video Intelligence, Natural Language, Speech-to-Text, Text-to-Speech, and Translation.



- **[AWS AI Services](https://aws.amazon.com/machine-learning/ai-services/)**

  AWS's pre-trained AI services including Rekognition (vision), Comprehend (NLP), Transcribe (speech-to-text), Polly (text-to-speech), and Translate.



- **[IBM Watson APIs](https://www.ibm.com/watson)**

  IBM's AI APIs including Watson Assistant (chatbots), Watson Discovery (document understanding), Watson Natural Language Understanding, and Watson Speech to Text.



- **[Clarifai](https://www.clarifai.com/)**

  Computer vision and multimodal AI platform. Provides pre-trained models for image recognition, video analysis, and custom model training.



- **[Replicate](https://replicate.com/)**

  Platform for running open-source models via API. Hosts thousands of community models for image generation, video, audio, and language tasks.



- **[Hugging Face Inference API](https://huggingface.co/inference-api)**

  Serverless inference for models hosted on Hugging Face Hub. Provides API access to thousands of open-source models without infrastructure management.



- **[Deepgram](https://deepgram.com/)**

  Speech recognition API optimized for real-time and batch transcription. Provides speaker diarization, summarization, and multilingual support.



- **[AssemblyAI](https://www.assemblyai.com/)**

  Speech AI API for transcription, speaker diarization, sentiment analysis, and audio intelligence.



- **[Rev AI](https://www.rev.ai/)**

  Speech-to-text API with human-in-the-loop options. Provides transcription, captions, and sentiment analysis.



## Open-Source GitHub Projects



### Large Language Model Serving



- **[vLLM](https://github.com/vllm-project/vllm)**

  **The leading open-source LLM serving engine for high-throughput production deployments.** **Apache-2.0 licensed**. **Key features**: **PagedAttention** for efficient KV cache memory management; **continuous batching** for increased total throughput; **tensor parallelism** for multi-GPU inference; **OpenAI-compatible API**; **AWQ, GPTQ, FP8 quantization** support; **multi-LoRA serving** natively . **Performance**: At 100 concurrent requests, vLLM outperforms TGI by **30-40% in total throughput** due to superior memory utilization . **Tradeoffs**: Higher memory overhead than TGI at low concurrency; setup complexity medium (pip install) . **Best for**: High-traffic production deployments, C-end chat systems, and teams wanting maximum hardware ROI .



- **[Text Generation Inference (TGI)](https://github.com/huggingface/text-generation-inference)**

  **Hugging Face's production-grade LLM serving toolkit.** **Apache-2.0 licensed**, **10,798 GitHub stars** . **Key features**: **Continuous batching** and **Paged Attention**; **token streaming** via SSE; **tensor parallelism**; **bitsandbytes and GPT-Q quantization**; **Flash Attention** optimized transformers code; **distributed tracing** with OpenTelemetry; **Prometheus metrics** . **Performance**: Excellent TTFT at low concurrency (<10 requests) due to Rust-based scheduling . **Note**: **TGI is now in maintenance mode**—Hugging Face recommends downstream engines including **vLLM**, **SGLang**, and **llama.cpp** for new deployments . **Best for**: Teams standardized on Hugging Face ecosystem, low-concurrency latency-sensitive workloads, and those needing Hugging Face model validation tooling .



- **[Ollama](https://github.com/ollama/ollama)**

  **The simplest way to run open-source LLMs locally.** **MIT licensed**, written in Go. **Key features**: **Single binary** with no dependencies; **GGUF model support** with built-in quantization; **OpenAI-compatible API**; **model management** (pull, list, delete); **RAG support** via Open WebUI integration . **Setup complexity**: **Low** (single binary) . **Limitations**: **No continuous batching**, **no PagedAttention**, **limited multi-GPU support** . **Best for**: Development, prototyping, and local RAG applications .



### Speech Recognition & Synthesis



- **[Faster-Whisper](https://github.com/SYSTRAN/faster-whisper)**

  **Production-standard speech recognition with CTranslate2 backend.** **MIT licensed**. **Key features**: **Quantization support** (8-bit) via CTranslate2 for reduced model size; **word-level timestamps**; **multi-language support**; **seamless API integration** . **Performance**: **3.12% Word Error Rate (WER)**, **3,965 MB memory usage**—balanced profile compared to WhisperX . **Deployment**: Works on CPU and GPU; developer-friendly integration . **Best for**: Scalable cloud deployments, production transcription services, and teams needing reliability and integration .



- **[WhisperX](https://github.com/m-bain/whisperX)**

  **High-precision speech recognition with speaker diarization.** **MIT licensed**. **Key features**: **Word-level timestamps** for subtitle generation; **speaker diarization** (exclusive feature)—multi-speaker identification and separation; **cross-language transcription** . **Performance**: **Highest precision with 2.37% WER**, but **4,858 MB memory usage** and **4.83s load time** . **Tradeoffs**: Moderate integration complexity; heavy resource footprint . **Best for**: Offline academic archiving, research workflows, and complex audio scenarios requiring speaker differentiation .



- **[Whisper.cpp](https://github.com/ggerganov/whisper.cpp)**

  **Optimized C/C++ implementation of Whisper for edge devices.** **MIT licensed**. **Key features**: **Unparalleled speed** on modest hardware; **GGML pipeline**; **cross-platform** (macOS, Linux, Windows, mobile) . **Tradeoffs**: **Lacks word-level timestamps**; **no speaker diarization**; **accuracy degradation** with current quantization—unsuitable for complex academic content . **Best for**: Edge devices, real-time streaming on constrained hardware, and macOS Metal acceleration .



- **[Kokoro-82M](https://huggingface.co/hexgrad/Kokoro-82M)**

  **Lightweight, high-quality text-to-speech model.** **Apache-2.0 licensed**. **Key features**: **82M parameters** (extremely small); **local synthesis** with no API keys; **multiple voices** (af_heart, af_sarah, am_michael, etc.); **MCP server integration** for AI assistants . **Deployment**: `uvx mcp-kokoro-tts` for MCP clients; **pykokoro** library for Python integration with **SSMD pause control** and **voice blending** . **Platforms**: macOS, Linux, Windows . **Best for**: Local TTS in AI agents, privacy-conscious applications, and developers wanting voice synthesis without cloud dependencies .



- **[VoxCPM2](https://github.com/OpenBMB/VoxCPM)**

  **Open-source multilingual TTS with voice design and cloning.** **Apache-2.0 licensed**. **Key features**: **30 languages + 9 Chinese dialects**; **voice design** from natural language description (e.g., "a young woman, gentle and sweet voice"); **controllable cloning** from short reference clips; **48kHz studio-quality output**; **1.68% average WER** across 30 languages . **Installation**: `pip install voxcpm`. **Best for**: Multilingual speech generation, voice cloning research, and creative voice design .



- **[Coqui TTS (Idiap Fork)](https://github.com/idiap/coqui-ai-TTS)**

  **Community-maintained fork of Coqui TTS.** **MPL-2.0 licensed**. **Note**: Original Coqui AI shut down December 2025; fork is community-maintained with quarterly releases . **XTTS-v2** mid-tier in 2026 (~910 ELO vs 1,160+ for modern APIs); no inline emotion markup; PyTorch 2.6 compatibility fragile . **Best for**: Legacy voice cloning projects; **new deployments should consider VoxCPM2 or Kokoro** .



### Image Restoration & Enhancement



- **[ai-image-restorer](https://github.com/Motasaith/ai-image-restorer)**

  **Production-grade AI image restoration engine.** **Key features**: **4× super resolution** via Real-ESRGAN; **face enhancement** via GFPGAN; **denoising and deblurring**; **batch processing** with async polling queue; **dual-port architecture** (API: 8001, Dashboard: 8091); **Docker-ready** for VPS deployment . **Quality metrics**: **>0.9 SSIM** consistently; PSNR 31.84 on 4× upscaling . **Best for**: Restoring old photos, enhancing low-resolution images, and production image processing pipelines .



- **[restore-lab](https://github.com/Anishrkhadka/restore-lab)**

  **GPU-accelerated restoration workbench for images and video.** **Key features**: **Spatial upscaling** with 6 Real-ESRGAN/RealESRNet models; **temporal 4× video upscaling** with BasicVSR++; **GFPGAN face restoration**; **RetinexFormer low-light enhancement**; **NVENC output encoding**; **persistent FIFO queue** and **restart-safe job history** . **Deployment**: Docker Compose with NVIDIA runtime. **Best for**: Video restoration, anime upscaling, and comprehensive media processing workflows .



### LLM Application Frameworks



- **[Open WebUI](https://github.com/open-webui/open-webui)**

  **Feature-rich, self-hosted web interface for LLMs.** **MIT licensed**. **Key features**: **RAG support** with document upload; **multi-model support** (Ollama, OpenAI-compatible APIs); **user management** with RBAC; **offline capable**; **plugin ecosystem** . **Best for**: Teams wanting a ChatGPT-like interface for local models with RAG capabilities .



- **[Ollama MCP Servers](https://github.com/ollama/ollama)**

  **Ecosystem of MCP servers for Ollama integration.** Includes **mcp-kokoro-tts** for local TTS, **Ollama Fortress** security proxy, and numerous community integrations for RAG, bots, and productivity apps . **Best for**: AI agents needing local model access with structured tool integration .



### Additional Strong Open-Source Options



- **LLM Serving**: **vLLM** (high-throughput production), **TGI** (Hugging Face ecosystem, maintenance mode), **Ollama** (local development), **SGLang** (emerging alternative), **llama.cpp** (edge/CPU inference) .

- **Speech Recognition**: **Faster-Whisper** (production standard), **WhisperX** (high-precision with diarization), **Whisper.cpp** (edge devices), **Speechmatics** (containerized ASR with 30+ languages) .

- **Speech Synthesis**: **Kokoro-82M** (lightweight local TTS), **VoxCPM2** (multilingual cloning), **Coqui TTS fork** (legacy) .

- **Image Restoration**: **ai-image-restorer** (API + Dashboard), **restore-lab** (video + image workbench) .

- **LLM Applications**: **Open WebUI** (RAG interface), **MCP servers** (tool integration) .



**Frameworks for building custom systems**: Combine **vLLM** for high-throughput LLM serving with OpenAI-compatible API, **Faster-Whisper** for production speech recognition, **Kokoro-82M** or **VoxCPM2** for local TTS, **ai-image-restorer** or **restore-lab** for image/video enhancement, and **Open WebUI** for RAG-enabled chat interfaces. Add **PostgreSQL** for persistence and **Docker** for deployment.



## How to Contribute



1. Fork the repo.

2. Add/edit entries in `README.md` (follow existing format).

3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.

4. Submit PR with a short explanation.



Star the repo if you find it useful!



## Disclaimer



- This is a **community-curated** list — not exhaustive and not an endorsement.

- Applied AI APIs handle potentially sensitive data including images, audio, and text; ensure compliance with privacy regulations and review data handling practices before deployment.

- **Open-source reality**: The open-source ecosystem for applied AI is **mature at the LLM serving layer** (**vLLM**, **TGI**, **Ollama**) and **production-proven at the speech and image layers** (**Faster-Whisper**, **WhisperX**, **Real-ESRGAN**, **GFPGAN**). **vLLM** leads in high-concurrency throughput by 30-40% over TGI . **TGI is now in maintenance mode**—new deployments should consider vLLM, SGLang, or llama.cpp . **Faster-Whisper** provides the best balance of accuracy (3.12% WER) and memory usage for production ASR . **Kokoro-82M** and **VoxCPM2** deliver high-quality local TTS without API keys . However, **commercial platforms** (Microsoft Cognitive Services, Google Cloud AI, AWS AI Services) provide **managed infrastructure, broader model catalogs, and enterprise SLAs** that open-source alternatives require additional operational investment to match. The open-source path is **genuinely viable** for teams with strong ML engineering capacity seeking full data sovereignty and cost control.



---



**Made for AI engineers, ML practitioners, application developers, and technology leaders.**

Let's make applied AI more open, accessible, and self-hostable.
