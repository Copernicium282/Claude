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
- **Thinking/Reasoning**: Chain-of-thought prompting with `</think>` blocks
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

## Handwritten Notes
Personal handwritten notes from the course are available at:
- `/home/ir192m2/Documents/Claude/Building with the Claude API.pdf`

## Course Overview
This comprehensive video course teaches developers how to integrate Claude AI into applications using the Anthropic API. The curriculum covers fundamental API operations, advanced prompting techniques, tool integration, and architectural patterns for building AI-powered systems. Through hands-on exercises and practical examples, participants will learn to implement conversational AI, retrieval-augmented generation, automated workflows, and leverage Claude's multimodal capabilities for processing text, images, and documents.

## What You'll Learn
- Set up and authenticate with the Anthropic API (API key management, request configuration)
- Implement single and multi-turn conversations with proper message formatting
- Configure system prompts and control model behavior (temperature, streaming, structured formats)
- Design evaluation workflows with test dataset generation and automated grading
- Apply prompt engineering (XML tags, examples, clear directives)
- Integrate tool use capabilities (custom tools, batch operations, web search)
- Build RAG systems (chunking, embeddings, BM25, contextual retrieval)
- Utilize extended features (thinking mode, image/PDF processing, citations)
- Implement prompt caching strategies
- Develop MCP servers and clients
- Deploy Anthropic Apps (Claude Code, Computer Use)
- Architect agent-based systems (parallelization, chaining, routing)

## Prerequisites
- Proficiency in Python programming
- Basic knowledge of handling JSON data

## Who This Course Is For
- Backend developers building AI-powered APIs and services
- Full-stack engineers integrating conversational AI into web applications
- Data engineers implementing document processing and knowledge retrieval systems
- DevOps professionals automating workflows with AI assistance
- Technical architects designing scalable AI-integrated systems
- Software engineers transitioning to AI/ML application development
- Developers working on chatbots, virtual assistants, or content generation tools

## Key Concepts from Course

### Claude Models
Three model families optimized for different priorities:

| Model | Purpose | Trade-offs |
|-------|---------|------------|
| **Opus** | Highest intelligence, complex multi-step tasks | Higher cost, more latency |
| **Sonnet** | Balanced intelligence/speed/cost | Best for most practical use cases |
| **Haiku** | Fastest, optimized for speed/cost | No reasoning capabilities |

### API Access Flow
5-step process: User input → Developer server → Anthropic API → Token processing (tokenization → embedding → contextualization → generation) → Response return

### Prompt Engineering Techniques
- **Clear and Direct**: Action verbs in first line, specific task description
- **Being Specific**: Type A (attributes) and Type B (steps) guidelines
- **XML Tags**: Structured content organization for better AI comprehension
- **Examples**: One-shot/multi-shot prompting for corner cases and formatting
- **Structured Data**: Using pre-fill + stop sequences for clean JSON/code output

### Tool Integration
- **Tool Functions**: Python functions called when Claude needs external data
- **Tool Schemas**: JSON schemas describing tool availability and parameters
- **Multi-Turn Tool Conversations**: Continuous Claude calls until no more tool requests
- **Batch Tool**: Parallel tool execution within single request
- **Text Edit Tool**: Built-in file system operations
- **Web Search Tool**: Real-time web access for current information

### RAG Pipeline
1. **Text Chunking**: Size-based, structure-based, or semantic-based strategies
2. **Embeddings**: Numerical representation of text meaning
3. **Vector Database**: Storage and similarity search
4. **Query Processing**: Convert user question to embedding
5. **Similarity Search**: Find relevant chunks using cosine similarity
6. **Prompt Assembly**: Combine question with retrieved context

### Extended Features
- **Extended Thinking**: Reasoning time before final response (costs extra tokens)
- **Image Support**: Up to 100 images per request with token-based pricing
- **PDF Support**: Direct PDF reading with citation generation
- **Citations**: Source references with page/location metadata
- **Prompt Caching**: Reuse computational work for identical content (1-hour cache, 1024 token minimum)

### Tool-Based Grading
Automated validation for LLM outputs:
- **validate_json()**: JSON parsing check (10 if valid, 0 if error)
- **validate_python()**: AST parsing check (10 if valid, 0 if error)
- **validate_regex()**: Regex compilation check (10 if valid, 0 if error)

Score = (model_score + syntax_score) / 2

### MCP Architecture
- **Server**: Exposes tools/resources/prompts
- **Client**: Connects and retrieves definitions
- **Resources**: Proactive data exposure (vs tools' reactive execution)
- **Prompts**: Pre-defined templates for specialized tasks

### Claude Code
Terminal-based coding assistant:
- Run `claude` command to launch
- `init` command scans codebase, creates `claude.md`
- Supports Git worktrees for parallel instances
- Can consume MCP servers for extended capabilities

### Agents & Workflows
- **Workflows**: Pre-defined steps for known tasks (higher reliability)
- **Agents**: Flexible tool combination for unknown tasks
- **Parallel Workflows**: Decompose tasks for simultaneous execution
- **Chaining Workflows**: Sequential steps for complex multi-part tasks
- **Routing Workflows**: Categorize input to select appropriate pipeline

## Core Technical Notes

### Token Processing
Text generation process has 4 stages:
1. **Tokenization**: Breaking input into tokens (words/word parts/symbols/spaces)
2. **Embedding**: Converting tokens to numerical representations of word meanings
3. **Contextualization**: Adjusting embeddings based on neighboring tokens
4. **Generation**: Output layer produces probabilities for next word selection

**Key parameters**: `max_tokens` (generation length limit), `stop_reason` (why model stopped)

### Prompt Engineering Fundamentals
- **Clear and Direct**: Action verbs in first line with specific task description
- **Being Specific**: Type A (output attributes) + Type B (reasoning steps) guidelines
- **XML Tags**: Structure content with tags like `<sales_records>` for better comprehension
- **Examples**: One-shot/multi-shot prompting for corner cases and formatting
- **Structured Data**: Use assistant pre-fill + stop sequences for clean JSON/code output

### Evaluation Workflow
6-step iterative process:
1. Write initial prompt draft
2. Create evaluation dataset (3+ examples or thousands)
3. Generate prompt variations with test inputs
4. Get LLM responses for each variation
5. Grade responses (1-10 scale)
6. Iterate and compare versions

### Chunking Strategies for RAG
- **Size-Based**: Equal-length strings (most common, may cut words)
- **Structure-Based**: Split on document structure (headers, paragraphs)
- **Semantic-Based**: Group sentences by meaning similarity

### Prompt Caching Rules
- Cache duration: 1 hour maximum
- Minimum threshold: 1024 tokens required
- Cache invalidation: Any change before breakpoint invalidates entire cache
- Best for: Repeated system prompts, tool schemas, static message prefixes