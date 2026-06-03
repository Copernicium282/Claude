# Notes: Building with the Claude API

This repository contains personal notes, exercises, and Jupyter notebooks compiled during the **Building with the Claude API** course. The contents focus on understanding, integrating, and leveraging Anthropic's Claude models programmatically using the official Python SDK.

## Folder Structure

| Folder | Description | Key Files |
|--------|-------------|-----------|
| **Accessing Claude with the API** | Core API interaction patterns | `requests.ipynb`, `chatbot.ipynb`, `concise.ipynb`, `sys_prompt.ipynb`, `controlling_out.ipynb`, `prefill.ipynb`, `stream.ipynb`, `temperature.ipynb` |
| **Features Of Claude** | Advanced Claude capabilities | `caching.ipynb`, `citations.ipynb`, `code_execution.ipynb`, `thinking.ipynb`, `images.ipynb` |
| **Tool use with Claude** | Tool integration patterns | `tools.ipynb`, `multitool.ipynb`, `multiturn_tools.ipynb`, `web_search_tool.ipynb`, `text_editor_tool.ipynb`, `tools_multi_conversation.ipynb` |
| **RAG and Agentic Search** | Retrieval-Augmented Generation | `chunking.ipynb`, `embeddings.ipynb`, `vectordb.ipynb`, `bm25.ipynb`, `hybrid.ipynb` |
| **Prompt Engineering** | Prompt design principles | `prompt_engineering.ipynb` |
| **Prompt Evaluation** | Methods for evaluating prompts | `prompt_evaluation.ipynb`, `grader.ipynb`, `improved_evaluator.ipynb`, `code_grader_fns.ipynb` |
| **Anthropic Apps** | Python package with MCP server | `main.py`, `tools/`, `tests/`, `pyproject.toml` |
| **Model Context Protocol** | CLI chat with MCP integration | `main.py`, `mcp_client.py`, `mcp_server.py`, `core/` |

## Detailed Overview

### Accessing Claude with the API
Core API interaction patterns including:
- **Basic Requests**: Installing dependencies, initializing the `Anthropic` client, multi-turn queries
- **System Prompts**: Controlling tone, persona, and response formatting (e.g., ELI5 explanations)
- **Response Brevity**: Optimizing token usage while maintaining precision
- **Interactive Chatbot**: Building terminal-based persistent conversation agents
- **Output Control**: Streaming responses, stop sequences, temperature tuning
- **Prefilling**: Steering response style with deterministic starting points

### Features Of Claude
Advanced capabilities:
- **Caching**: Cost optimization through response caching
- **Citations**: Source references and document grounding
- **Code Execution**: Running code within Claude responses
- **Thinking/Reasoning**: Chain-of-thought prompting with `<think>` blocks
- **Multimodal**: Image and PDF processing support

### Tool use with Claude
Integration patterns for:
- Single tool definition and registration
- Multi-tool workflows with state management
- Tool streaming and incremental output
- Conversation-aware tool usage
- Web search and text editor tools

### RAG and Agentic Search
Retrieval-Augmented Generation techniques:
- **Chunking Strategies**: Document segmentation approaches
- **Embeddings**: Using VoyageAI and other embedding models
- **Vector Databases**: Storage and similarity search
- **BM25**: Lexical search scoring
- **Hybrid Search**: Combining dense and sparse retrieval

### Prompt Engineering
Design principles for:
- Effective prompt construction and iteration
- Persona and tone control
- State management in multi-turn conversations
- Structured output formatting

### Prompt Evaluation
Methods for:
- Automated prompt evaluation with datasets
- Code grading functions for technical prompts
- Grounded evaluation metrics
- Improved evaluator prompts

### Anthropic Apps
A Python package implementing document-related tools exposed via MCP server for AI assistant integration.

**Setup:**
```bash
uv venv && source .venv/bin/activate
uv pip install -e .
```

**Run:**
```bash
uv run main.py
```

**Test:**
```bash
uv run pytest
```

### Model Context Protocol
CLI chat application supporting document retrieval and MCP slash commands.

**Setup:**
```bash
uv venv && source .venv/bin/activate
uv pip install -e .
```

**Run:**
```bash
uv run main.py
```

## Setup & Installation

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

## Core Technical Concepts Demonstrated

- **Client Initialization**: Safe loading of credentials from `.env` and instantiation of the `Anthropic` client class.
- **Structured Message Formats**: Managing conversations via list structures where each item represents a Turn Object containing a `role` (`"user"` or `"assistant"`) and the accompanying `content`.
- **System Parameter Integration**: Utilizing the top-level `system` parameter in `client.messages.create` to establish absolute rules before user interaction begins.
- **Real-time Completions**: Programmatic setup of response streams and correct access of final `Message` objects via `.content[0].text`.