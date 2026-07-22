# AI

## Facts
- An AI Model is the broad umbrella category. An LLM (Large Language Model) is a specific kind of AI model focused on language.
- In AI systems, an Agent Harness (often called an Agent Framework or Runner) is the surrounding control code that wraps around a raw LLM to turn it into an autonomous agent. An LLM on its own is completely stateless—it just receives text input and predicts text output. The harness provides the loop, state management, and execution rules that allow the LLM to perform multi-step work.
- LLM-as-a-Judge like a teacher grading a student's exam. Instead of a human reading every single response, you give the grading job to a super-smart AI model (like Claude or GPT-4o) and ask it to review the work of another AI model.
- Agent UX is about designing how smoothly an AI agent guides the customer through a task improving UX. It ensures the customer always knows what to do, what the AI is doing, and how to stay in control. Functions like a UX Design: proactively walking users through flows, asking for clarification, and preventing frustration.
- AI shifts computing from command-driven (how to do it) to intent-driven (what to achieve). The user specifies the goal; the AI handles execution, orchestration, and tool selection.
- Inference in AI is the execution phase where a trained model processes new, unseen inputs to generate predictions, responses, or actions. Training builds the brain; inference uses it.
- Fine-Tuning AI is adjusting the internal weights of a pre-trained base model using a task-specific dataset. It modifies behavior, tone, and output formatting rather than serving as a real-time knowledge base.
- Real-Time HITL (Human-in-the-Loop). This happens live, while the AI is executing a task. `AI Generates Plan -> Triggers Confirmation UI / Text Window -> Human Approves -> AI Executes Action`. Purpose: Risk prevention, preventing hallucinated errors, and ensuring safety for high-stakes actions (e.g., executing a database query, charging a credit card, sending an email). UX Mechanism: Action confirmation cards, dynamic text fields for user corrections, modal dialogs, or inline "Approve / Edit / Deny" triggers. Scope: Happens during active runtime to control a single, real-time transaction.
- AI Evals (Evaluation) is a standardized report card for AI systems to measure accuracy, safety, and task completion instead of relying on subjective "vibe-checks.".
- An AI Tool is a programmatic capability given to an AI agent to perform real-world actions. Without tools, an LLM is purely a text generator (calculating probability of next words). With tools, an LLM becomes an action-taking agent—it decides what tool to use, what inputs to pass, and how to handle the execution output.
- Model means the "brain" or engine of the AI (e.g., GPT-4o, Claude 3.5 Sonnet, Gemini 3.5 Flash). It is the trained neural network that processes inputs and generates outputs.
- Prompt means the text instructions, code, or context you feed to the AI model to direct its behavior and specify what output you want.
- Parameters mean the internal variables (weights and biases) learned by the model during training that dictate its knowledge and capabilities (e.g., 7B, 70B, 405B). Higher parameter counts generally mean a more capable, complex model.
- Context (Context Window) means the short-term memory limit of the model—the maximum total number of tokens (prompt + output response) it can process at one time.
- Token is the basic unit of text that the AI reads and generates. It is not 1-to-1 with a word:Rough conversion: 1 token is 4 characters or 0.75 English words. Code conversion: Code takes more tokens due to special characters (1.5–2 tokens per word).
- The Model (GPT-4o, Claude, DeepSeek, Ollama) provides the brain: deciding what code to write. The Agent (Codex, Roo Code, Cline) provides the hands: reading files, running terminal commands, and writing diffs. The Tools / MCP (FileSystem, Terminal Shell, Git, DB Drivers) provide the senses & limbs: giving the agent access to external APIs, databases, and system utilities. The Environment (VS Code Workspace, Local Repo, Docker Container, Cloud Sandbox) provides the ground: the physical workspace where code actually executes, builds, and runs tests. When these 4 layers work together, they transform plain text generation into autonomous Agentic Coding—allowing AI to write, run, test, and fix real code directly inside your workspace.
- Extension Agents (Cline, Roo Code): Act as separate "orchestration frameworks" inside standard VS Code; they bring the agentic tools (file editing, terminal execution, MCP, approval gates) while you supply the AI model "brain" via your own API keys. Built-in AI Editors (Cursor, Windsurf): Bundle the agent engine, editor surface, and model infrastructure directly out of the box into a single, pre-configured product. Key Tradeoff: Cline/Roo Code: Maximum control, open-source execution, and raw pay-per-token model routing. Cursor: Zero setup friction, turnkey developer environment, and integrated predictive tab completion.
- CLI Agents (Codex CLI, Claude Code): Autonomous, terminal-native workers that operate directly inside your shell to inspect code, edit files, and execute terminal commands.
- CLI Agent Role: Niche tool for batch file migrations, background scripting, or CI pipeline automation.
- Standard Frontend Workflow: Cursor or VS Code + Roo Code is 90% of what you need. Real-time visual feedback, CSS/Tailwind previewing, and component diffs require an IDE surface.
- Pay-As-You-Go API Key is a meter-based access key provided by AI providers (OpenAI, Anthropic, OpenRouter). Instead of paying a flat $20/month subscription, you pay strictly for the exact input and output tokens consumed per request.
- Vibe coding and Agentic coding both use the same tools, the same underlying AI engines, and IDE tools (e.g., Cursor, Roo Code, Claude, OpenRouter), but their mental models, intents, and execution processes are not the same.
- By connecting your frontend project to an AI backend API, you enable the software to execute complex, multi-step tasks autonomously. The client application handles user interaction and real-time UI updates, while the server-side agent runs loops, calls tools, and processes data. This transforms static web software into an active agent that can perform real actions on behalf of the user.

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
### Terminal tool name 1

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
- Both GitHub Copilot and Cursor act as middleman brokers: your subscription fee funds an internal credit balance on their platform, and they handle paying model providers (Anthropic, OpenAI, Google) on the backend. You do NOT need separate API keys or individual subscriptions to model providers—everything is billed directly through your Cursor or GitHub account.
- When you select models like Claude Sonnet or GPT-4o inside these tools, tokens are deducted straight from your built-in monthly credit pool.
- GitHub Copilot and Cursor (free or paid) both reset included monthly credits on a fixed billing cycle; unused credits do NOT roll over to the next month. You CANNOT re-purchase the same subscription tier early within the same billing cycle to refresh your base quota. When included credits run out mid-month, neither tool forces you to wait until the next cycle: Both allow immediate mid-cycle tier upgrades (paying the difference to unlock higher usage pools instantly). Both support pay-as-you-go overage billing to continue without interruption. Cursor keeps Auto mode and Tab completion available even after your frontier credit pool reaches $0.
- ChatGPT (Free/Plus/Team/Pro) and Gemini (Free/Advanced/Business) both operate on rolling usage limits (e.g., messages per 3 hours) and monthly renewal dates for workspace quotas; unused messages or API-based web credits do NOT roll over. You CANNOT re-purchase the same subscription tier mid-month to instantly reset your rate limits or monthly usage caps. When you hit usage limits during a heavy session, neither tool strictly forces you to stop working: Both allow immediate mid-cycle upgrades to higher subscription tiers (e.g., Plus to Team/Pro, or Gemini Advanced to Business/Enterprise) to instantly increase rate limits and context windows. Both offer web platform access alongside API options (OpenAI Platform / Google AI Studio) where you can pay per token via pay-as-you-go billing if you hit consumer chat caps. Both drop down to faster, lighter fallback models (e.g., ChatGPT switching to 4o-mini, Gemini switching to 1.5 Flash) so you can keep chatting even after hitting limits on frontier models.
- Copilot & Cursor: Treat AI primarily like metered utility credits. You start with a $10–$20 pool every month, and complex model calls deduct from that pool until it hits $0. ChatGPT & Gemini: Treat AI like bandwidth speed caps. You pay for a flat subscription, and the platform throttles your request frequency across 3-hour or daily rolling windows to manage server traffic.
- Ollama (The "Docker" of AI Models) What It Is: An open-source local model manager that simplifies running open-weight LLMs (e.g., Llama, Qwen, DeepSeek) directly on your hardware. Why the Docker Analogy Fits: Registry/Pulls: Pulls models with single commands similar to container images (ollama pull qwen2.5-coder). Container-like Abstraction: Packages the model file (GGUF/weights), runtime configurations, system prompts, and memory allocations into a unified CLI runner. Modelfiles: Uses Modelfile (identical to Dockerfile syntax) to configure parameters, system behavior, and context limits.
- Ollama Engine is 100% Free: Ollama itself is a free, open-source local runtime. Downloading it and pulling models costs $0. Open-Weight Models are 100% Free: The AI models hosted in the Ollama library (like `qwen2.5-coder`, `qwen3.6`, `llama3.2`, `gemma`) are open-weight and completely free to download and run. Zero Cloud API Usage: Inferences consume local hardware resources (GPU/RAM) rather than cloud model tokens. There are no per-token charges or monthly platform billing.
- Regional Access Restrictions (Myanmar). Claude (Anthropic): Direct web access (`claude.ai`) and direct API endpoints (`api.anthropic.com`) are geo-blocked. Requires routing traffic through a third-party gateway (e.g., `OpenRouter`) or using Cursor's built-in servers. Google AI Studio (Developer Tools): Geo-blocked at the API gateway level (`generativelanguage.googleapis.com`). Yields User location is not supported when attempting to pass raw Google API keys locally. Consumer Gemini (gemini.google.com): Works normally via standard web frontends without the API-level region block.
- You need Roo Code or Cline when you want to use OpenRouter keys, custom provider API keys, or open-weight/local models.
- Codex Extension is Self-Contained: It includes built-in agentic orchestration (reading workspace context, writing multi-file edits, and running terminal commands). Roo Code / Cline are Redundant when using the official Codex extension with an OpenAI account or API key.

## My Confusion & Understanding

-Confusion:Example note

Understanding:Example note

-Confusion:Example note

Understanding:Example note