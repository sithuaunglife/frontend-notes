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
- Notes

## My Confusion & Understanding

-Confusion:Example note

Understanding:Example note

-Confusion:Example note

Understanding:Example note