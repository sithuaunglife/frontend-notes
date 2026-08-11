# Agentic Development

## Facts
- The Model (GPT-4o, Claude, DeepSeek, Ollama) provides the brain: deciding what code to write. The Agent (Codex, Roo Code, Cline) provides the hands: reading files, running terminal commands, and writing diffs. The Tools / MCP (FileSystem, Terminal Shell, Git, DB Drivers) provide the senses & limbs: giving the agent access to external APIs, databases, and system utilities. The Environment (VS Code Workspace, Local Repo, Docker Container, Cloud Sandbox) provides the ground: the physical workspace where code actually executes, builds, and runs tests. When these 4 layers work together, they transform plain text generation into autonomous Agentic Coding—allowing AI to write, run, test, and fix real code directly inside your workspace.
- Extension Agents (Cline, Roo Code): Act as separate "orchestration frameworks" inside standard VS Code; they bring the agentic tools (file editing, terminal execution, MCP, approval gates) while you supply the AI model "brain" via your own API keys. Built-in AI Editors (Cursor, Windsurf): Bundle the agent engine, editor surface, and model infrastructure directly out of the box into a single, pre-configured product. Key Tradeoff: Cline/Roo Code: Maximum control, open-source execution, and raw pay-per-token model routing. Cursor: Zero setup friction, turnkey developer environment, and integrated predictive tab completion.
- CLI Agents (Codex CLI, Claude Code): Autonomous, terminal-native workers that operate directly inside your shell to inspect code, edit files, and execute terminal commands.
- CLI Agent Role: Niche tool for batch file migrations, background scripting, or CI pipeline automation.
- Standard Frontend Workflow: Cursor or VS Code + Roo Code is 90% of what you need. Real-time visual feedback, CSS/Tailwind previewing, and component diffs require an IDE surface.
- Pay-As-You-Go API Key is a meter-based access key provided by AI providers (OpenAI, Anthropic, OpenRouter). Instead of paying a flat $20/month subscription, you pay strictly for the exact input and output tokens consumed per request.
- Vibe coding and Agentic coding both use the same tools, the same underlying AI engines, and IDE tools (e.g., Cursor, Roo Code, Claude, OpenRouter), but their mental models, intents, and execution processes are not the same.
- There are two different things: FIM (Fill-in-the-Middle) and Tab Autocomplete. They are not the same.
- FIM (Fill-in-the-Middle). FIM is a model capability. The model is given: the code before your cursor (prefix), the code after your cursor (suffix), and it predicts the code that belongs in the middle. Many code models (like StarCoder, Codestral, Qwen Coder, DeepSeek Coder, etc.) are trained specifically for FIM. To use FIM, you typically need access to a model that supports it through its API.
- Tab Autocomplete is an editor feature, not a model capability. It displays inline code suggestions that you can accept by pressing Tab. The suggestion can come from different sources, including a FIM model or another completion model. Examples include Cursor and Windsurf.
- Model-Dependent Quotas: Overall request and token limits on gateways (like OpenCode Go/Zen or Kilo Gateway) are heavily model-dependent. Heavy frontier models consume allotments much faster, whereas lighter flash or open-weight models give you vastly more requests.
- Isolated Quotas (BYOK): If you plug in your own API key (like a direct Google AI Studio Gemini key), that specific quota is entirely independent and bound solely to that single model provider's rules.
- There are two different AI coding workflows: Pair Programming and Agentic Coding. They are not the same.
- Pair Programming is where the AI works alongside you as a coding partner. It answers questions, suggests code, explains errors, and completes functions, but you remain in control of every step. (Examples: GitHub Copilot, traditional AI chat assistants.)
- Agentic Coding is where the AI acts as an autonomous coding agent. It can understand a high-level goal, search the codebase, plan changes, edit multiple files, run terminal commands (with your approval), and continue working until the task is complete. (Examples: Codex, OpenCode, Kilo Code, Cursor Agent.)
- Kilo Code is an IDE-first AI coding assistant that emphasizes an interactive pair programming workflow. You work alongside the AI, asking for edits, explanations, and code generation as you build features together, similar to Cursor.
- OpenCode is a CLI-first agent harness that emphasizes agentic programming. Instead of coding step by step with you, it autonomously plans, edits, tests, and completes larger coding tasks from a single prompt, similar to Codex CLI.
- Kilo Code is designed for an interactive pair-programming workflow inside an IDE, so it frequently sends conversation history, editor context, open files, workspace structure, diagnostics, recent edits, and user instructions with each request. This rich surrounding context helps the AI provide better real-time assistance but results in larger prompts and higher token usage. OpenCode, being a CLI-first agent harness, is optimized for agentic task execution by keeping prompts lean and including only the context needed to complete the assigned task. As a result, Kilo Code generally consumes more tokens per interaction, while OpenCode is more token-efficient for larger autonomous coding tasks.
- Agent Initialization: Agentic coding tools (e.g., OpenCode, Aider, and Pi) typically begin by scanning your project, reading important files, and building an understanding of the codebase before performing any tasks. This initialization process can consume a significant portion of the model's context window (e.g., around 8,000 tokens or more, depending on the project size and agent configuration). Once the initial context is loaded, the agent uses that information to perform coding tasks more effectively, and subsequent interactions generally focus on the relevant parts of the project rather than reloading everything from scratch.
- Agent Session Memory: AI agents only remember information within the current session. As long as you remain in the same session, the agent retains the conversation history and previously gathered context. Starting a new session resets the conversation memory, so the agent no longer remembers previous discussions or decisions. However, it can re-scan or re-index your project to rebuild its understanding of the codebase, even though the previous conversation is not retained.
- Configuring Local Models: To use a local LLM or a third-party API gateway with an AI coding agent, you must configure the agent's settings (e.g., OpenCode or Aider) to point to the appropriate API endpoint, specify the model name, and provide any required API key (if applicable). For local inference, this typically means pointing the agent to your local llama.cpp or Ollama server (e.g., `http://localhost:8080/v1` or another configured endpoint). Once configured, the agent sends requests to the specified endpoint instead of using a cloud-hosted model.

## Syntax
**AGENTS.md Hierarchy**
```txt
devboard/
├── AGENTS.md                 # Project rules
├── PRODUCT.md                # Users, flows, constraints
├── frontend/
│   ├── AGENTS.md             # UI conventions
│   └── src/
│       └── features/...
├── backend/
│   ├── AGENTS.md             # API/service conventions
│   └── app/...
└── tests/
    └── e2e/...               # Browser checks
```
- `/AGENTS.md` — Rules for the entire repository.
- `/frontend/AGENTS.md` — UI and frontend conventions.
- `/backend/AGENTS.md` — API and service conventions.
- `/tests/` — End-to-end and browser checks.


**Heading 2**
```js 
 <!-- code here -->
```
- Description

## Terminal Commands
### OpenCode commands

**OpenCode Fix: 479-byte opencode.exe**
```bash
npm install -g --allow-scripts=opencode-ai opencode-ai
```
- Reinstalls OpenCode while allowing the package's install script to run. This installs the correct native executable and fixes the 479-byte opencode.exe error (The specified executable is not a valid application for this OS platform).


**Heading 2**
```bash
 <!-- code here -->
```
- Description


### Terminal tool name 2

**Heading 1**
```bash
 <!-- code here -->
```
- Description


**Heading 2**
```bash
 <!-- code here -->
```
- Description

## Tools
- OpenRouter is an API aggregator that acts as a unified gateway and wallet for hundreds of AI models. Single API Key: Access models from OpenAI, Anthropic, Google, Meta, and DeepSeek using one key. OpenAI-Compatible: Fits directly into VS Code extensions (Cline, Roo Code, Continue), terminal tools, and AI IDEs. No Regional Blocks: Requests route through OpenRouter’s gateway, bypassing local region restrictions.
- GitHub Models is a multi-model developer playground and API access hub integrated into the GitHub and Azure ecosystem. Curated Selection: Provides access to a selected catalog of industry models from OpenAI, Meta, Microsoft, and Mistral. Free Prototyping Quota: Offers free daily rate-limited usage tier out of the box using your standard GitHub personal access token. Azure Billing: Transitions to paid production usage by linking directly to a post-paid Azure subscription or GitHub invoice rather than a prepaid wallet. Ecosystem Integrated: Built primarily for prototyping in the GitHub playground, testing via GitHub Actions, and deploying with Azure AI Inference SDKs.
- GitHub Models free tier limits reset daily and minutely, not monthly. How GitHub Models Limits Work: Requests Per Minute (RPM): Limits how fast you can send requests (usually 10–15 requests/min). Requests Per Day (RPD): Resets every 24 hours. Smaller models (Llama 3, Phi-3): ~150 requests per day. Heavy models (GPT-4o, reasoning models): ~50 requests per day. Note: If you hit a rate limit error (HTTP 429), you just need to wait a few minutes or until the daily 24-hour counter resets.
- GitHub Copilot is a direct end-user subscription product. GitHub Copilot Key Differences Subscription Model: Paid per month/year (e.g., $10/mo for Copilot Pro, $39/mo for Pro+). Each tier gives you monthly included AI Credits to use across models. No API Keys: You do not manage or paste API keys into tool configs. You log in directly with your GitHub Account inside VS Code, JetBrains, or the terminal. Multi-Model Access Included: Includes access to multiple models (GPT-4o, Claude 3.5/3.7, Gemini) under one subscription, managed automatically through the Copilot extension. Built for IDE Workflows: Features built-in autocomplete, inline chat, file context indexing, and agentic workspace tools directly inside your editor.
- Both GitHub Copilot and Cursor act as middleman brokers: your subscription fee funds an internal credit balance on their platform, and they handle paying model providers (Anthropic, OpenAI, Google) on the backend. You do NOT need separate API keys or individual subscriptions to model providers—everything is billed directly through your Cursor or GitHub account. When you select models like Claude Sonnet or GPT-4o inside these tools, tokens are deducted straight from your built-in monthly credit pool.
- GitHub Copilot and Cursor (free or paid) both reset included monthly credits on a fixed billing cycle; unused credits do NOT roll over to the next month. You CANNOT re-purchase the same subscription tier early within the same billing cycle to refresh your base quota. When included credits run out mid-month, neither tool forces you to wait until the next cycle: Both allow immediate mid-cycle tier upgrades (paying the difference to unlock higher usage pools instantly). Both support pay-as-you-go overage billing to continue without interruption. Cursor keeps Auto mode and Tab completion available even after your frontier credit pool reaches $0.
- ChatGPT (Free/Plus/Team/Pro) and Gemini (Free/Advanced/Business) both operate on rolling usage limits (e.g., messages per 3 hours) and monthly renewal dates for workspace quotas; unused messages or API-based web credits do NOT roll over. You CANNOT re-purchase the same subscription tier mid-month to instantly reset your rate limits or monthly usage caps. When you hit usage limits during a heavy session, neither tool strictly forces you to stop working: Both allow immediate mid-cycle upgrades to higher subscription tiers (e.g., Plus to Team/Pro, or Gemini Advanced to Business/Enterprise) to instantly increase rate limits and context windows. Both offer web platform access alongside API options (OpenAI Platform / Google AI Studio) where you can pay per token via pay-as-you-go billing if you hit consumer chat caps. Both drop down to faster, lighter fallback models (e.g., ChatGPT switching to 4o-mini, Gemini switching to 1.5 Flash) so you can keep chatting even after hitting limits on frontier models.
- Copilot & Cursor: Treat AI primarily like metered utility credits. You start with a $10–$20 pool every month, and complex model calls deduct from that pool until it hits $0. ChatGPT & Gemini: Treat AI like bandwidth speed caps. You pay for a flat subscription, and the platform throttles your request frequency across 3-hour or daily rolling windows to manage server traffic.
- Regional Access Restrictions (Myanmar). Claude (Anthropic): Direct web access (`claude.ai`) and direct API endpoints (`api.anthropic.com`) are geo-blocked. Requires routing traffic through a third-party gateway (e.g., `OpenRouter`) or using Cursor's built-in servers. Google AI Studio (Developer Tools): Geo-blocked at the API gateway level (`generativelanguage.googleapis.com`). Yields User location is not supported when attempting to pass raw Google API keys locally. Consumer Gemini (gemini.google.com): Works normally via standard web frontends without the API-level region block.
- You need Roo Code or Cline when you want to use OpenRouter keys, custom provider API keys, or open-weight/local models.
- Codex Extension is Self-Contained: It includes built-in agentic orchestration (reading workspace context, writing multi-file edits, and running terminal commands). Roo Code / Cline are Redundant when using the official Codex extension with an OpenAI account or API key.
- Account-Wide Providers (OpenRouter & Mistral). On platforms like OpenRouter and Mistral AI, the free daily allowance (RPD) is tied to your Account / User ID. OpenRouter: If you exhaust your 50 requests/day free allowance on openrouter/free, OpenRouter blocks your API key. Switching your model config to qwen:free or llama:free will not work because the gateway itself locks your account for 24 hours. Mistral: If you exhaust your free trial evaluation pool on codestral-latest, switching to mistral-small using the same key will still throw an HTTP 429 error.
- Per-Model Bucket Providers (Groq & Cerebras). This is where Groq and Cerebras are different. Their rate limits are calculated per model:  How Groq Works: Groq gives you separate quotas for different model sizes:  llama-3.1-8b-instant -> 14,400 Requests/Day. llama-3.3-70b-versatile -> 1,000 Requests/Day. qwen3-32b -> 1,000 Requests/Day. What this means for you: If you exhaust your 1,000 daily requests on llama-3.3-70b-versatile on Groq, you CAN keep using Groq! Simply switch your tool setting to llama-3.1-8b-instant or qwen3-32b, and you get an entirely fresh daily request bucket.
- Platform like OpenRouter, Groq, Cerebras, Mistral / Codestral are API aggregator that hold API keys and they have Daily Limit (RPD), Per-Minute Limit (RPM) that different from AI model limit. If you use up the Daily Limit you can no longer use that provider even you switch to different AI model.
- You can point Kilo's autocomplete setting to a fast local model like qwen2.5-coder:1.5b via Ollama for zero-cost, offline tab completions.
- Cursor says: "Let's build this together." You and the AI collaborate in real time. It searches the codebase, proposes edits, asks for approval, and continues iterating with you throughout the task.
- Codex says: "Here's the ticket. I'll go implement it and report back." You give it a high-level goal, and it works more independently, carrying out the task before returning with the results for you to review.
- GitHub Copilot says: "I'll suggest code while you type." You write the code, and it helps by completing lines, generating snippets, and answering questions. You stay in control of every step.
- Kilo Code says: "I'll handle this step, then check with you before moving on." You give it a task, and it works through it incrementally, asking for your approval before taking important actions and keeping you involved.
- OpenCode says: "Here's my plan. I'll work through it while keeping you informed." You give it a goal, and it carries out the task in an agentic way while periodically updating you and requesting approval for important actions.
- Aider says: "Tell me what to change. I'll edit the repository directly." You describe the changes, and it modifies your project through a Git-first, terminal-based workflow while keeping the edits organized and reviewable.
- Aider is centered around Git and a terminal-first workflow. While it can handle frontend development, it is generally less optimized for a visual, IDE-centric frontend workflow than tools like Cursor, OpenCode, or Kilo Code.
- When using Kilo Code Auto/Free, the usage limit is based on Kilo Code's request quota, not the individual model's token limit. Each agent step consumes requests from the shared Kilo Code Auto/Free quota. Kilo automatically selects and routes requests to supported free models behind the scenes, so your limit is determined by Kilo's request allowance rather than the token quota of any specific model.
- Kilo Code Auto/Free provides 200 requests per hour per IP. According to the current documentation, Kilo does not specify how the hourly quota refreshes (e.g., fixed hourly window or rolling 60-minute window), so the exact reset behavior is unknown.
- OpenCode Zen's free tier tracks usage based on token consumption (and compute-equivalent value) rather than simple request counts: Context Volume: When using AI coding agents, sending large context files (entire source files, workspace trees, or lengthy system prompts) consumes thousands of tokens per request. Model Quotas: Each free model (e.g., big-pickle, qwen3.6-plus-free, minimax-m3-free) enforces its own usage ceiling tied to input/output token volume. You will hit the limit much faster on a 100k-token prompt than on a short 1k-token query. However, this is not officially confirmed by OpenCode and is based on community insights rather than official documentation.
- OpenCode uses a rolling 5-hour window across its rate-limiting infrastructure: 5-Hour Rolling Window: In OpenCode's ecosystem (including OpenCode Go and shared model pools), limits are enforced dynamically over a rolling 5-hour period rather than resetting at midnight or on a fixed 24-hour clock. How It Behaves: Once you reach the quota for a specific model or usage bucket, your limit gradually restores over the next 5 hours as old requests fall outside the rolling window. Per-Model Reset: On free Zen models, hitting a limit on one model triggers a cooling period for that specific endpoint (or until its 5-hour window rolls over). You can switch to another free model immediately without waiting for the 5-hour timer on the first model to expire. However, this is not officially confirmed by OpenCode and is based on community insights rather than official documentation.

## My Confusion & Understanding

-Confusion:Example note

Understanding:Example note

-Confusion:Example note

Understanding:Example note