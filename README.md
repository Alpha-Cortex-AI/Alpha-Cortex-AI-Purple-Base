# Finance Purple Agent (Baseline Example)

A simple A2A-compatible purple agent that serves as a baseline for the Finance Green Agent benchmark.

## Overview

This is a **baseline example** purple agent for the [AgentBeats](https://agentbeats.org) Phase 1 competition. It demonstrates how a purple agent should respond to the evaluation tasks from the Finance Green Agent.

## Features

- ✅ Fully A2A-protocol compatible
- ✅ Responds to all three evaluation tasks:
  - Risk Classification (Task 1)
  - Business Summary (Task 2)
  - Consistency Check (Task 3)
- ✅ Uses LLM (DeepSeek/OpenAI) for intelligent responses
- ✅ Lightweight and easy to run

## Quick Start

### Prerequisites

- Python 3.11+
- Virtual environment (venv or uv)
- OpenRouter API key

### Installation with venv

```bash
# Create virtual environment
python3 -m venv .venv

# Activate virtual environment
source .venv/bin/activate  # macOS/Linux

# Install dependencies
pip install -e .

# Configure API key
cp .env.example .env
# Edit .env and add your OPENROUTER_API_KEY
```

### Installation with uv (Alternative)

```bash
# Install dependencies
uv sync

# Configure API key
cp .env.example .env
# Edit .env and add your OPENROUTER_API_KEY
```

### Running

```bash
# With venv
.venv/bin/python src/analyst.py --port 9020

# With uv
uv run python src/analyst.py --port 9020
```

## Testing with Green Agent

```bash
# Terminal 1: Start green agent
cd ../finance-green-agent
.venv/bin/python src/server.py --port 9009

# Terminal 2: Start purple agent
cd ../finance-purple-agent
.venv/bin/python src/analyst.py --port 9020

# Terminal 3: Run evaluation
cd ../finance-green-agent
# Use scenario.toml to run evaluation
```

## Response Format

### Task 1: Risk Classification
```json
{
  "task": "risk_classification",
  "risk_classification": ["Market Risk", "Operational Risk", ...]
}
```

### Task 2: Business Summary
```json
{
  "task": "business_summary",
  "business_summary": {
    "industry": "...",
    "products": "...",
    "geography": "..."
  }
}
```

### Task 3: Consistency Check
```json
{
  "task": "consistency_check",
  "consistency_check": ["risk1", "risk2", ...]
}
```

## Project Structure

```
finance-purple-agent/
├── src/
│   └── analyst.py      # Main agent implementation
├── .env.example        # Environment template
├── pyproject.toml      # Dependencies
└── README.md           # This file
```

## License

MIT License