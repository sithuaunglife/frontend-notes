# Llama.cpp

## Facts
- `llama.cpp` is an open-source inference engine for running GGUF large language models locally.
- Ollama and LM Studio both use `llama.cpp` (or technology based on it) under the hood to run supported models.
- `llama.cpp` can be used directly as a model host, but you must manually download models, configure settings, and start the server yourself.
- Ollama is essentially a wrapper around `llama.cpp` that simplifies model downloading, management, and serving through a user-friendly CLI and API.
- You can either: Build `llama.cpp` yourself from its GitHub source code or download prebuilt binaries released by the `llama.cpp` project or provided by third parties.
- After starting the server with `llama serve`, click the URL displayed in the terminal to open the built-in web chat interface in your browser.
- `llama.cpp`: each `llama serve` instance serves a single model. To use a different model, you must stop the current server and start a new `llama serve` command with the desired model (or run another server instance on a different port).
- Quantization Models — Definition: Quantization reduces a model's size by storing its weights in lower precision while preserving most of its performance. Original Precision: FP32 (32-bit Floating Point) • BF16 (16-bit Brain Float) • FP16 (16-bit Floating Point). Why Lower Precision? Higher precision requires more storage and memory. Quantized Formats: Q8_0 (Highest quality, largest size) • Q6_K (Excellent quality) • Q5_K_M (Great balance) • Q4_K_M (Most popular) • Q3_K_M (Smaller with noticeable quality loss) • IQ4_XS / IQ3_M (Newer intelligent quantizations). Example (Qwen3.5-4B): BF16 (~8.7 GB) • Q8_0 (~4.6 GB) • Q6_K (~3.8 GB) • Q5_K_M (~3.4 GB) • Q4_K_M (~2.9 GB). Performance: Q4_K_M typically retains ~90–95%+ of the original model's capabilities while using only a fraction of the storage. Why Quantization Works: Neural networks tolerate small numerical approximations, allowing lower-precision weights with minimal impact on model quality. GGUF Quantization: Most GGUF models on Hugging Face are already quantized (Q4_K_M • Q5_K_M • Q6_K • Q8_0 • IQ4_XS • IQ3_M), so no additional quantization is needed for llama.cpp. Benefits: Smaller download size • Lower RAM/VRAM usage • Faster inference • Runs on consumer hardware • Retains most of the original model's performance.
- llama.cpp Backends: llama.cpp supports multiple hardware acceleration backends depending on your system: CUDA (NVIDIA GPUs) • Vulkan (Cross-platform API supporting NVIDIA, AMD, and Intel GPUs) • ROCm/HIP (AMD GPUs on Linux) • Metal (Apple Silicon & Macs) • SYCL (Intel GPUs and oneAPI) • OpenCL (Older cross-platform GPU support) • CPU (No GPU acceleration; works on any system). The backend determines which hardware performs model inference for better speed and efficiency.
- Installing llama.cpp: You can build llama.cpp from source with your preferred backend (e.g., CUDA using the CUDA Toolkit, Vulkan using the Vulkan SDK, ROCm/HIP for AMD GPUs, Metal for Apple Silicon, or SYCL for Intel GPUs). If you don't want to compile it yourself, you can download the precompiled binaries from the llama.cpp GitHub releases, extract them to a folder on your computer (e.g., `C:\llama.cpp`), and add that folder to your Windows PATH environment variable so the `llama` command is available from any terminal.
- Precompiled CUDA Binaries: You do not need to install the full CUDA Toolkit to use the CUDA-enabled precompiled builds of llama.cpp. The GitHub release typically includes the required CUDA runtime `.dll` files. Simply download the CUDA precompiled binaries, extract them, and keep the bundled `.dll` files in the same directory as the `llama.exe` executable. This allows the CUDA backend to run without installing the complete CUDA Toolkit, provided you already have a compatible NVIDIA graphics driver installed.
- CUDA Compatibility: Some older NVIDIA GPUs (e.g., GeForce MX250) are not compatible with CUDA 13 builds. They are limited to CUDA 12 builds instead. Before downloading precompiled llama.cpp binaries, verify your GPU's CUDA compatibility and choose the appropriate CUDA version; otherwise, the executable may fail to run or load the required CUDA libraries.
- Building llama.cpp with CUDA: If you want to compile llama.cpp with CUDA support, enable the CUDA backend during the build process using `-DGGML_CUDA=ON`. You can also enable CUDA Graphs using `-DGGML_CUDA_GRAPHS=ON` to potentially reduce kernel launch overhead and improve inference performance on supported NVIDIA GPUs. These options produce a CUDA-enabled binary optimized for NVIDIA hardware.
- GPU Memory (VRAM) & Offloading: Large language models primarily benefit from GPU VRAM during inference. If the model (or the number of GPU-offloaded layers) exceeds the available VRAM, the remaining layers are automatically kept in system RAM and executed by the CPU, which is significantly slower. GPU backends such as CUDA, Vulkan, ROCm/HIP, and Metal allow llama.cpp to offload model layers to the GPU. The `-ngl` (`--gpu-layers`) option controls how many layers are offloaded to VRAM—higher values generally improve performance if sufficient VRAM is available, while lower values reduce VRAM usage by leaving more work to the CPU.
- Choosing a Model Based on VRAM: Select a model that matches your available GPU VRAM for the best balance of speed and quality. As a general guideline, 2 GB VRAM is best suited for 2B models, which provide faster inference and allow more layers to be offloaded to the GPU. You can still run larger models such as 4B, but more layers will remain on the CPU due to VRAM limitations, resulting in slower response times. Larger models generally produce higher-quality outputs but require more memory and computation. If a model does not fully fit in VRAM, llama.cpp automatically offloads the remaining layers to the CPU using system RAM.
- Model Parameters (B): The "B" in a model name stands for billions of parameters (e.g., 2B = 2 billion, 4B = 4 billion, 8B = 8 billion). In general, models with more parameters are more capable—they tend to produce higher-quality responses, follow instructions better, reason more effectively, and possess broader knowledge. This also benefits local AI agents (e.g., OpenCode, Aider, Pi), as they rely on the underlying model's capabilities to perform coding, reasoning, and other tasks. However, larger models require more RAM/VRAM, run more slowly, and consume more computational resources during inference.

## Syntax
**Heading 1**
```js 
 <!-- code here -->
```
- Description


**Heading 2**
```js 
 <!-- code here -->
```
- Description

## Terminal Commands
### llama.cpp commands

**Running Model**
```bash
llama serve `
  -hf bartowski/Qwen_Qwen3.5-4B-GGUF:IQ4_XS `
  -ngl 18 `
  -t 8 `
  -np 1 `
  -c 19000
```
- `serve` Starts the OpenAI-compatible HTTP server.
- `-hf bartowski/Qwen_Qwen3.5-4B-GGUF:IQ4_XS` downloads (if needed) and runs the `Qwen3.5-4B` GGUF model from Hugging Face using the `IQ4_XS` quantization.
- `-ngl 18` offloads the first 18 layers of the model to the GPU. Use `0` for CPU only or `999` to offload as many layers as possible (if VRAM allows).
- `-t 8` — uses 8 CPU threads for inference. A good starting point is the number of your CPU's physical or logical cores, depending on your workload.
- `-np 1` — allows 1 parallel request (slot) to be processed at a time. Increase this if you expect multiple clients to use the server simultaneously. Higher values consume more memory and can reduce performance for each individual request.
- `-c 19000` sets the context window to 19000 tokens.
- The model is downloaded automatically the first time you run the command.
- After the server starts, it exposes an OpenAI-compatible API (typically at `http://localhost:8080` unless configured otherwise).
- Increase `-ngl` if you have more GPU VRAM for better performance.
- Larger context sizes (`-c`) require more RAM and may reduce inference speed.


**Benchmark a Model**
```bash
llama bench `
  -hf unsloth/Qwen3.5-4B-GGUF:Q4_K_M `
  -ngl 5
```
- `bench` — benchmarks the model to measure inference performance.
- The benchmark reports metrics such as prompt processing speed (tokens/second), text generation speed (tokens/second), and memory usage (depending on the build and options).
- Use the results to compare different models, quantizations (e.g., `Q4_K_M` vs. `Q8_0`), `-ngl` values, and CPU-only vs. GPU-accelerated inference.


**Running a Model in the Terminal**
```bash
llama-cli `
  -m "C:\Users\Admin\.cache\huggingface\hub\models--bartowski--Qwen_Qwen3.5-4B-GGUF\snapshots\4168f45a16a1290d65a4ec0fa312ae917a4c15d6\Qwen_Qwen3.5-4B-IQ4_XS.gguf" `
  -ngl 18 `
  -t 8 `
  -c 19000
```
- `-m` Loads a local GGUF model from the specified file path.
- `e87f176479d0855a907a41277aca2f8ee7a09523` is the Hugging Face snapshot ID. It is version-specific and may change when the model is updated or re-downloaded.


- `llama serve --help` — Displays the help message and all available options for the `llama serve` command.
- `llama-cli --version` — Shows the version of the installed `llama.cpp` CLI.
- `pi install git:github.com/huggingface/pi-llama` — installs the `Pi Llama` coding agent.
- `pi` — launches Pi and automatically discovers your local `llama.cpp` model. No configuration or API keys are required.

## Tools
- Visit `https://llama.app/` and follow the installation instructions to automatically set up `llama.cpp` on your device. This is the easiest option if you don't want to build or configure it manually.
- Visit `https://github.com/ggml-org/llama.cpp` if you want to build and set up `llama.cpp` manually from the source code.
- llama.cpp Releases: Visit the llama.cpp GitHub Releases page to download the latest precompiled binaries: `https://github.com/ggml-org/llama.cpp/releases`. Download the archive for your desired backend (e.g., CUDA, Vulkan, HIP/ROCm, Metal, or SYCL). Extract the ZIP file and copy its contents into your `llama.cpp` folder. If you've already downloaded the base binaries, simply copy the backend-specific files (such as the CUDA package) into the same folder to enable that backend.
- Coding Models: For local AI coding agents, the Qwen family of models is widely regarded as one of the strongest choices for programming tasks. Models such as Qwen2.5-Coder and Qwen3.5 generally excel at code generation, debugging, code explanation, and following programming instructions. The best model still depends on your hardware, but if your primary use case is coding, the Qwen family is often an excellent starting point for local inference.


