# Ollama

## Facts
- Ollama (The "Docker" of AI Models) What It Is: An open-source local model manager that simplifies running open-weight LLMs (e.g., Llama, Qwen, DeepSeek) directly on your hardware. Why the Docker Analogy Fits: Registry/Pulls: Pulls models with single commands similar to container images (ollama pull qwen2.5-coder). Container-like Abstraction: Packages the model file (GGUF/weights), runtime configurations, system prompts, and memory allocations into a unified CLI runner. Modelfiles: Uses Modelfile (identical to Dockerfile syntax) to configure parameters, system behavior, and context limits.
- Ollama Engine is 100% Free: Ollama itself is a free, open-source local runtime. Downloading it and pulling models costs $0. Open-Weight Models are 100% Free: The AI models hosted in the Ollama library (like `qwen2.5-coder`, `qwen3.6`, `llama3.2`, `gemma`) are open-weight and completely free to download and run. Zero Cloud API Usage: Inferences consume local hardware resources (GPU/RAM) rather than cloud model tokens. There are no per-token charges or monthly platform billing.
- Ollama is generally a bit slower than `llama.cpp` because it adds a management layer on top of the inference engine and exposes fewer low-level performance tuning options.
- Ollama: once the Ollama server is running, you can switch between models freely using `ollama run <model-name>` without restarting the server.
- By installing Ollama from the official website and launching ollama.exe, the Ollama server starts automatically in the background. You do not need to run ollama serve manually because it's already running.

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
### Ollama commands

**Install Ollama**
```bash
irm https://ollama.com/install.ps1 | iex
```
- Downloads and runs the official Ollama installer.
- Installs Ollama on your Windows machine.


**Check Running Models**
```bash
ollama ps
```
- Displays the models currently loaded and running in Ollama.
- Shows information such as the model name, processor usage (CPU/GPU), context size, and how long the model has been loaded.


**Download a Model**
```bash
ollama pull <model-name>
```
- Downloads the specified model from the Ollama model library to your local machine.
- If the model is already installed, Ollama checks for updates and downloads newer layers if available.


**Show a Model**
```bash
ollama show <model-name>
```
- Displays detailed information about an installed model, including its architecture, parameter size, context length, quantization, and license.


**Run the Ollama Server**
```bash
ollama serve
```
- Starts the Ollama server, allowing clients and applications to connect to local models through the Ollama API.
- By default, the server listens on `http://localhost:11434`.

## Tools
- Notes

## My Confusion & Understanding

-Confusion:Example note

Understanding:Example note

-Confusion:Example note

Understanding:Example note