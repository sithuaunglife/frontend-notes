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
- Before getting into Agentic Coding, learn and practice normal manual coding first.
- When AI only generates code from your instructions, it's AI-assisted coding. Agentic Development gives the AI an environment where it can inspect the codebase, use tools, execute commands, modify files, test changes, and iterate toward a goal with a certain degree of autonomy.
- Context Pollution: Context becomes filled with irrelevant information. Old prompts, failed attempts, logs, and unnecessary code can interfere with the current task. More context ≠ better context.
- No Boundaries: The agent has too much freedom or unclear scope. Define what the agent can access, modify, execute, and change. Use clear instructions, project structure, permissions, and constraints.
- Prompt Spiral: Repeatedly adding prompts to fix previous prompts or AI mistakes. Example: "Do this." → "Actually, don't do that." → "Fix what you changed." → "Revert that." → "Now fix the original issue.". The conversation becomes increasingly complicated instead of converging on the goal. Often indicates that the environment, instructions, or task boundaries need improvement.
- When Agentic Development goes wrong, don't immediately blame the model. The problem may be the workflow, not the model.
- Evolution of AI Agentic Coding: 1. Manual Coding -> 2. AI-Assisted Coding -> 3. AI Coding Assistants -> 4. Agentic Coding -> 5. Agentic Development.
- Agentic Development is the practice of designing a development workflow and environment in which AI agents can reliably work toward software-development goals. It involves designing: Environment — where the agent operates · Context — what information the agent receives · Boundaries — what the agent is allowed to do · Tools — what actions the agent can perform · Instructions — how the agent should operate · Feedback Loops — how the agent observes results and iterates · Verification — how the developer validates the agent's work. Agentic Development = Designing the system around the AI agent, not simply prompting AI to write code.
- In traditional coding, developers often review the implementation line by line. In Agentic Coding, the developer does not need to review every line of code. Instead, the developer focuses on the evidence that the agent's work is correct. Developer → Goal → Agent → Implementation → Evidence → Verification. Evidence can include: Tests passing, Build succeeding, Type checking passing, Linter passing, Screenshots or visual verification, Relevant command output, Diff / changed files, Expected behavior working correctly. Agentic Coding = Review the evidence, not every line. The developer's role shifts from inspecting every implementation detail to verifying that the agent achieved the intended outcome reliably.
- Agentic Coding is similar to human productivity: The better the environment, the better the AI agent can perform.
- Agentic Coding Lifestyle: SPEC → MAP → BUILD → PROVE → LEARN → REPEAT. SPEC — Define what needs to be built and the expected outcome. MAP — Understand the codebase, environment, constraints, tools, and approach. BUILD — Let the agent implement the solution within the defined boundaries. PROVE — Verify the result through evidence such as tests, builds, type checks, diffs, and actual behavior. LEARN — Analyze the result, improve the workflow, update the environment, and carry the lessons into the next task. Agentic Coding is not just AI writing code. It is a continuous development loop: SPEC → MAP → BUILD → PROVE → LEARN.
- In Agentic Coding, treat tokens as a budget. Every piece of context consumes part of that budget, so the goal is not to give the agent as much context as possible, but to give it the right context.
- Changing a specification is cheap. Changing 25 files after building in the wrong direction is expensive. Cheap changes happen early. Expensive changes happen after implementation.
- Product brief structure for Agentic Development. It prevents the agent from jumping straight into implementation before understanding the product intent. WHO → WHY → WHAT → RULES → NON-GOALS → DONE. WHO — Who is this for? Who is the user? WHY — What problem are we solving? Why does it matter? WHAT — What are we actually building? RULES — What constraints, requirements, or principles must be followed? NON-GOALS — What are we explicitly not building? DONE — What evidence tells us the work is complete? The NON-GOALS part is especially valuable for agents because it establishes a boundary: "Don't expand the task beyond this scope.". And DONE naturally connects to your PROVE stage: DONE = observable acceptance criteria, not "the code looks finished".
- Context boundary is a very important part of the workflow. It defines what information the agent should know for the current task—and what it should not carry in.
- `AGENTS.md` is like persistent project memory/instructions for the agent. Instead of repeatedly putting the same rules into your prompt, you put them in the repository where the agent can discover and follow them.
- Plan before implementation: Spending time planning a 5-line change can be far more cost-efficient than discovering a bad direction after a 25-file refactor.
- Backend tends to be contract-driven; Frontend tends to be perception-driven. Backend proves correctness with contracts. Frontend proves correctness with contracts + browser evidence. Backend context: API contracts · Data models · Validation · Business rules · Error handling · Database behavior · Service boundaries. Frontend context: User flows · UI states · Visual hierarchy · Interaction behavior · Accessibility · Responsive behavior · Loading / error / empty states. So when an agent works on each side, the relevant context isn't identical.
- Build passes ≠ UI correct. For frontend Agentic Coding, browser smoke tests and visual verification are important evidence alongside build and typecheck.
- Harnessed self-correction — The workflow provides feedback mechanisms that allow the agent to detect and fix its own mistakes. Humans don't need to manually find every AI-generated bug. Instead, automated evidence such as tests, typechecks, builds, browser checks, and runtime feedback can trigger the agent's correction loop.
- Harnessed self-correction is a major part of the PROVE stage, where the testing and verification harness provides feedback that allows the agent to detect, correct, and re-test its own mistakes.
- Ask for evidence, not confidence. In Agentic Coding, the goal is not to make the agent sound confident. The goal is to make the workflow produce objective evidence that the work is correct.
- Recover from Prompt Spiral: If the direction is wrong, don't fix the implementation — fix the context. Wrong direction → Stop → Fix the context/spec → Re-map → Build again. When an agent enters a prompt spiral, repeatedly correcting its output can make the workflow increasingly expensive and confusing.
- AFK Workflow — Let the agent work autonomously through predefined steps while you’re away. It handles routine failures and verification automatically, stopping only when human judgment is required.
- MCP = live tools + controlled actions for AI agents. It lets agents interact with external tools, services, and data through defined capabilities. Think of MCP as a plug connector between the agent and those external capabilities. Examples: GitHub, databases, filesystem, browser, APIs, Figma.
- Agent Capability Levels:
 - L1 — Prompt / Tell it once: Give instructions for a single task.
 - L2 — AGENTS.md / Teach the project: Give it persistent project context and rules.
 - L3 — Skills / Teach a workflow: Give it reusable, repeatable processes.
 - L4 — MCP / Give it tools: Connect it to real-world tools and data through live, controlled actions.
 - L5 — Subagents / Let it delegate: Allow it to delegate bounded tasks to specialized agents.
 - Learn the levels progressively, but skip around freely when building real projects. Make one agent reliable before introducing multi-agent delegation.
- You can give the agent a source `.txt` file and ask it to read, understand, and generate the appropriate project documentation from it.
- Ask the coding agent to analyze the requirements and create an implementation plan without implementing the changes.
- `AGENTS.md` — the agent's context and controller; it directs the agent on how to work and tells it which project files/docs to read for the context it needs.
- `HANDOFF.md`: Context checkpoint for AI agents when switching models or running out of context/tokens. Records current progress, decisions, important context, and next steps so another agent can continue without starting over.

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
- This creates an agent-friendly full-stack repository where both humans and agents can understand how the project should be developed.


**Overall Agentic Coding Workflow**
```txt 
PRODUCT BRIEF
WHO → WHY → WHAT → RULES → NON-GOALS → DONE
↓  
SPEC → MAP → BUILD → PROVE → LEARN
```
- Product Brief — Define the product goal, scope, constraints, boundaries, and definition of done.
- SPEC — Turn the brief into clear implementation requirements.
- MAP — Understand the codebase, architecture, files, dependencies, tools, and affected areas.
- BUILD — Let the agent implement the solution within the defined boundaries.
- PROVE — Verify the implementation using evidence such as tests, typecheck, builds, and browser smoke tests.
- LEARN — Capture what worked, what failed, and what should improve in the next iteration.


**Simple Agent Harness**
```txt 
project/
│
├── README.md
│   # Project understanding
│   # What the project is and how to use it
│
├── AGENTS.md
│   # Agent behavior
│   # How the agent should work in this project
│
├── ARCHITECTURE.md
│   # Where/how to build it
│   # Project structure and architectural decisions
│
└── docs/
    │
    ├── PRODUCT.md
    │   # What to build
    │   # Product requirements and expected behavior
    │
    ├── DEVELOPMENT.md
    │   # How to work on it
    │   # Development setup, workflow, and conventions
    │
    └── TESTING.md
        # How to prove it
        # Testing strategy, commands, and verification
```
- A lightweight, simple, minimalist, single-project documentation structure for agent-assisted development.
- Monolithic structure: frontend + backend live together in one project/repository.
- Keeps project context, agent instructions, product requirements, architecture, development workflow, and testing organized without introducing unnecessary complexity.


**Full-Blown Agent Harness**
```txt 
my-project/
│
├── README.md
├── AGENTS.md                 # Agent entry point / project map
├── ARCHITECTURE.md           # System boundaries + dependency rules
├── CONTRIBUTING.md            # Human contribution rules
├── CHANGELOG.md               # Project history
│
├── docs/
│   ├── PRODUCT.md             # Why / who / product principles
│   ├── DEVELOPMENT.md         # Local development workflow
│   ├── TESTING.md             # Testing strategy
│   ├── SECURITY.md            # Security rules / threat boundaries
│   ├── API.md                 # API contracts / conventions
│   │
│   ├── decisions/             # Architecture Decision Records
│   │   └── README.md
│   │
│   ├── plans/                 # Implementation plans
│   │   ├── active/
│   │   └── completed/         # Historical plans
│   │
│   └── specs/                 # Feature specifications
│       └── issue-filtering.md
│
├── .agents/
│   └── skills/                # Reusable agent workflows
│       ├── implement-feature/
│       └── investigate-bug/
│
├── scripts/
│   ├── setup.sh               # Reproducible environment
│   ├── dev.sh                 # Start development environment
│   ├── test.sh                # Run tests
│   ├── lint.sh                # Run static analysis
│   └── verify.sh              # Prove the change
│
├── frontend/
│   ├── AGENTS.md              # Frontend-specific instructions
│   ├── src/
│   └── tests/
│
├── backend/
│   ├── AGENTS.md              # Backend-specific instructions
│   ├── src/
│   └── tests/
│
├── tests/
│   ├── integration/
│   └── e2e/                   # Full user-journey verification
│
└── .github/
    └── workflows/
        └── ci.yml             # External verification gate
```
- A comprehensive, full-blown agent harness for agent-assisted development in a single project.
- Monolithic structure: frontend + backend live together in one project/repository.
- Provides structured project context, agent instructions, product requirements, architecture, reusable skills, implementation plans, development workflows, security rules, and verification.
- Designed to give the agent everything it needs to understand, plan, build, test, and verify the project reliably.

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
- Caveman - Open-source token-saving tool for coding agents** that compresses agent communication to reduce unnecessary output tokens. Helps make long-running agentic workflows more token-efficient while preserving useful technical information.
- Self-hosted Agent: Run your coding agent, harness, MCP servers, memory, and workflows on your own VPS while connecting to cloud-hosted LLMs through APIs. Useful for persistent/AFK workflows, since the agent can keep running even when your PC is offline. The VPS doesn't need a powerful GPU in this setup because the cloud provider does the model inference.
- Figma MCP: Comes with official `SKILL.md` guidance that teaches the agent how to use Figma's MCP capabilities effectively. When setting up Figma MCP, its official skill files can be added to the agent's skills so it knows how to use those capabilities.

## My Confusion & Understanding

-Confusion:Example note

Understanding:Example note

-Confusion:Example note

Understanding:Example note