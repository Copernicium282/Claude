# Notes: Building with the Claude API

This repository contains my personal notes, exercises, and Jupyter notebooks from the **Building with the Claude API** course. The goal of this course is to learn how to effectively integrate and leverage Anthropic's Claude models inside applications.

## Repository Structure

The project is organized into several hands-on Jupyter notebooks:

*   **[`requests.ipynb`](./requests.ipynb)**: Getting started with the Anthropic Python SDK, managing environment variables, and making initial API calls to Claude.
*   **[`sys_prompt.ipynb`](./sys_prompt.ipynb)**: Exploring the power of **System Prompts** to define roles, style, tone, and format constraints (e.g., explaining complex topics in an *Explain Like I'm 5* (ELI5) style).
*   **[`concise.ipynb`](./concise.ipynb)**: Techniques and prompts for enforcing brevity, extracting key information, and generating concise/constrained outputs from the API.
*   **[`chatbot.ipynb`](./chatbot.ipynb)**: Building a stateful, interactive, terminal-based chatbot that maintains dynamic conversation history across multiple turns.

---

## Setup & Installation

To run these notebooks locally, follow these steps:

### 1. Clone the repository and navigate to it:
```bash
cd "/home/ir192m2/Desktop/Blockchain/MERN stack/Claude"
```

### 2. Set up a virtual environment (optional but recommended):
```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies:
```bash
pip install anthropic python-dotenv ipykernel
```

### 4. Configure Environment Variables:
Create a `.env` file in the root directory and add your Anthropic API key:
```env
ANTHROPIC_API_KEY=your_api_key_here
```

---

## Key Learning Takeaways

*   **SDK Usage**: Initializing `Anthropic()` client, setting target models (like `claude-sonnet-4.5`), and managing `max_tokens`.
*   **Message List Management**: Maintaining conversation history by appending dictionary messages representing `"role": "user"` and `"role": "assistant"` sequence structures.
*   **System Prompts**: Injecting system instructions separately from user content to guide the persona, response constraints, and formatting behaviors.
