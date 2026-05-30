# Notes: Building with the Claude API

This repository contains personal notes, exercises, and Jupyter notebooks compiled during the **Building with the Claude API** course. The contents focus on understanding, integrating, and leveraging Anthropic's Claude models programmatically using the official Python SDK.

## Folder Contents

The repository is organized into six distinct Jupyter notebooks, each addressing a core concept of the Claude API:

### 1. Basic Requests (`requests.ipynb`)
* **Objective**: Establish the foundation for interacting with the Anthropic API.
* **Topics Covered**:
  * Installing dependencies (`anthropic`, `python-dotenv`).
  * Initializing the `Anthropic` client.
  * Configuring the API client and targeting specific models (e.g., `kiro/claude-sonnet-4.5`).
  * Creating a simple message history structure and executing consecutive multi-turn queries.

### 2. System Prompts (`sys_prompt.ipynb`)
* **Objective**: Leverage system-level instructions to control response characteristics.
* **Topics Covered**:
  * Injecting system prompts into API parameters.
  * Steering the tone, persona, and target audience formatting of responses (e.g., styling explanations in an *Explain Like I'm 5* (ELI5) format).
  * Structuring stateful message transitions with custom system constraints.

### 3. Response Brevity and Constraints (`concise.ipynb`)
* **Objective**: Optimize output length, efficiency, and token usage.
* **Topics Covered**:
  * Using advanced system prompts to strictly enforce code-level conciseness.
  * Prompting techniques designed to minimize token consumption while maintaining technical precision and completeness.

### 4. Interactive Chatbot (`chatbot.ipynb`)
* **Objective**: Build a persistent conversation agent.
* **Topics Covered**:
  * Structuring a terminal-based, loop-driven interactive chatbot.
  * Dynamically managing state by continuously tracking and appending user and assistant messages in a sequential message log.

### 5. Controlling Outputs (`controlling_out.ipynb`)
* **Objective**: Manage response determinism, stream completions, and programmatically handle outputs.
* **Topics Covered**:
  * Utilizing stop sequences (e.g., stopping at `"```"`) to cleanly truncate code blocks.
  * Implementing client-side streaming using `client.messages.stream` to extract and print text content incrementally.
  * Controlling generation determinism by adjusting the `temperature` parameter.
  * Correctly parsing and cleaning API message structures for downstream applications.

### 6. Prefilling Responses (`prefill.ipynb`)
* **Objective**: Guide the starting point of Claude's response to steer output style and formatting.
* **Topics Covered**:
  * Injecting prefilled assistant messages (e.g., starting the assistant's turn with `"```json"`) to programmatically lock in specific formats.
  * Directing code-generation workflows using deterministic and high-temperature brainstorming contexts.

---

## Setup & Installation

Follow these instructions to configure the environment and run the notebooks:

### 1. Clone the repository and navigate to the project directory:
```bash
cd "/home/ir192m2/Desktop/Blockchain/MERN stack/Claude"
```

### 2. Set up a virtual environment (optional but recommended):
```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install the required dependencies:
```bash
pip install anthropic python-dotenv ipykernel
```

### 4. Configure Environment Variables:
Create a `.env` file in the root directory and add your Anthropic API key:
```env
ANTHROPIC_API_KEY=your_actual_api_key_here
```

---

## Core Technical Concepts Demonstrated

* **Client Initialization**: Safe loading of credentials from `.env` and instantiation of the `Anthropic` client class.
* **Structured Message Formats**: Managing conversations via list structures where each item represents a Turn Object containing a `role` (`"user"` or `"assistant"`) and the accompanying `content`.
* **System Parameter Integration**: Utilizing the top-level `system` parameter in the `client.messages.create` method to establish absolute rules before user interaction begins.
* **Real-time Completions**: Programmatic setup of response streams (`text_stream`) and correct access of final `Message` objects via `.content[0].text`.
