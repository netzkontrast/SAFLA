# LLM-Oriented Guide to the SAFLA Repository

This document provides a comprehensive overview of the SAFLA repository, tailored for Large Language Models (LLMs) and AI agents. Its purpose is to enable an AI to understand the project's goals, architecture, and core functionalities, and to facilitate its use in new project prototypes.

## 1. Project Overview

**SAFLA (Self-Aware Feedback Loop Algorithm)** is a custom-built neural network designed specifically for AI agents and autonomous coding systems. It enhances AI agents with:

*   **Persistent Memory:** Remembers context across sessions.
*   **Self-Learning Capabilities:** Improves performance over time based on feedback.
*   **Adaptive Reasoning:** Adapts strategies for different tasks.

SAFLA is intended for use in autonomous development, research agents, and intelligent automation. It is production-ready and can be deployed in enterprise environments.

## 2. Core Components

SAFLA can be interacted with in three primary ways:

### a. Python SDK
The repository includes a comprehensive Python SDK for custom application development, research, and enterprise integration. The core logic is located in the `safla/` directory.

**Key Classes:**
*   `safla.core.HybridMemoryArchitecture`: Manages the hybrid neural memory system.
*   `safla.core.MetaCognitiveEngine`: Handles self-learning and adaptive reasoning.

### b. Command Line Interface (CLI)
A powerful CLI is provided for system administration, automation, and DevOps. The main entry point for the CLI is `safla/cli_main.py`.

**Key Commands:**
*   `safla system start`: Starts the SAFLA system.
*   `safla memory search <query>`: Searches the memory.
*   `safla optimize performance`: Runs performance optimization tasks.

### c. Model Context Protocol (MCP) Integration
SAFLA is designed for seamless integration with AI development environments like Claude Code via the Model Context Protocol (MCP). This provides AI agents with access to SAFLA's tools and capabilities. The primary script for this is `safla_mcp_enhanced.py`.

## 3. Key Features

SAFLA's architecture provides several key benefits:

*   **Persistent Memory:** A hybrid neural memory system (Vector, Episodic, Semantic, Working) that allows the AI to remember context and learn from past interactions.
*   **Self-Learning & Improvement:** A feedback loop that allows the system to get smarter over time by analyzing outcomes and adapting its strategies.
*   **Safety & Reliability:** A safety framework with a constraint engine, risk assessment, and rollback capabilities to prevent harmful operations.
*   **High Performance:** Optimized for speed, with capabilities for real-time response and high-throughput batch processing.
*   **Enhanced AI Tools:** A suite of 14 tools for tasks like text analysis, pattern detection, and knowledge graph construction.
*   **Enterprise Ready:** Includes features like JWT authentication, auto-scaling, and cloud deployment support.

## 4. Installation

There are two primary ways to install SAFLA:

### a. Standard Installation (from PyPI)
For most use cases, SAFLA can be installed directly from PyPI.

```bash
pip install safla
```

### b. Development Installation (from source)
To contribute to development or to access the latest, unreleased features, install the package in editable mode from the cloned repository.

```bash
git clone https://github.com/ruvnet/SAFLA.git
cd SAFLA
pip install -e .
```

## 5. Usage Example (Python SDK)

This example demonstrates basic usage of the Python SDK to store and retrieve a memory. This is a simplified version of the examples found in the `examples/` directory.

```python
# main.py
import asyncio
from safla.core.hybrid_memory import HybridMemoryArchitecture
from safla.core.meta_cognitive_engine import MetaCognitiveEngine

async def main():
    # Initialize SAFLA components
    memory = HybridMemoryArchitecture()
    meta_engine = MetaCognitiveEngine()

    # Store a memory
    print("Storing a memory...")
    memory_id = await memory.store_memory(
        "SAFLA is a neural network for AI agents.",
        metadata={"project": "llm-overview"}
    )
    print(f"Memory stored with ID: {memory_id}")

    # Search for a similar memory
    print("Searching for similar memories...")
    similar_memories = await memory.search_similar(
        "What is SAFLA?",
        top_k=1
    )

    if similar_memories:
        print("Found similar memory:")
        print(similar_memories[0])
    else:
        print("No similar memories found.")

if __name__ == "__main__":
    asyncio.run(main())
```

## 6. Project Structure

The repository is organized into the following key directories:

*   `safla/`: Contains the core Python source code for the SAFLA library, including the SDK, CLI, and MCP components.
*   `docs/`: Contains detailed documentation on various aspects of the project, such as the CLI, MCP setup, and deployment.
*   `examples/`: Contains example Python scripts demonstrating how to use the SAFLA SDK for various tasks.
*   `tests/`: Contains a comprehensive suite of tests for the project, covering all major components.
*   `scripts/`: Contains utility scripts for system administration, testing, and development.
*   `README.md`: The main README file for the project, providing a detailed overview.
*   `CLAUDE.md`: A document describing the SPARC development methodology used in the project.
*   `LLM.md`: This file, an LLM-oriented guide to the repository.
