# SAFLA - Self-Aware Feedback Loop Algorithm

A sophisticated AI/ML system implementing autonomous learning and adaptation with comprehensive safety mechanisms, hybrid memory architecture, and meta-cognitive capabilities.

## 🚀 Overview

SAFLA is a production-ready autonomous AI system that combines advanced memory management, meta-cognitive reasoning, distributed orchestration, and safety validation. The system implements a multi-layered architecture for intelligent agents capable of self-awareness, continuous learning, and safe autonomous operation.

### Key Capabilities

- **🧠 Hybrid Memory Architecture**: Multi-layered memory system with vector, episodic, semantic, and working memory
- **🤖 Meta-Cognitive Engine**: Self-awareness, goal management, strategy selection, and adaptive learning
- **🔗 MCP Orchestration**: Distributed agent coordination via Model Context Protocol
- **🛡️ Safety & Validation**: Comprehensive safety constraints, risk assessment, and rollback mechanisms
- **📊 Delta Evaluation**: Formal quantification of system improvements across multiple dimensions

## 🏗️ Architecture

### Core Components

#### 1. Hybrid Memory Architecture (`safla/core/hybrid_memory.py`)
- **Vector Memory**: High-dimensional vector storage with similarity search (cosine, euclidean, dot product, manhattan)
- **Episodic Memory**: Sequential experience storage with temporal indexing and event clustering
- **Semantic Memory**: Knowledge graph implementation with nodes, edges, and relationship mapping
- **Working Memory**: Active context management with attention mechanisms and temporal decay
- **Memory Consolidation**: Automated transfer between memory types with importance weighting

#### 2. Meta-Cognitive Engine (`safla/core/meta_cognitive_engine.py`)
- **Self-Awareness Module**: System state monitoring and introspective capabilities
- **Goal Manager**: Dynamic goal setting, tracking, adaptation, and conflict resolution
- **Strategy Selector**: Context-aware strategy selection and optimization with learning
- **Performance Monitor**: Real-time performance tracking, alerting, and trend analysis
- **Adaptation Engine**: Continuous learning and controlled self-modification

#### 3. MCP Orchestration (`safla/core/mcp_orchestration.py`)
- **Server Management**: Dynamic MCP server discovery, registration, and health monitoring
- **Context Sharing**: Vector embedding-based context propagation between agents
- **Agent Coordination**: Multi-agent orchestration with capability-based task assignment
- **Resource Management**: Load balancing and resource allocation across distributed systems
- **Error Handling**: Robust error recovery with retry, failover, and circuit breaker patterns

#### 4. Safety & Validation Framework (`safla/core/safety_validation.py`)
- **Safety Constraints**: Hard and soft limits with configurable violation actions
- **Validation Pipeline**: Multi-stage validation with timeout and error handling
- **Risk Assessment**: Quantitative risk scoring with weighted factor analysis
- **Rollback Mechanisms**: Safe reversion to previous system states via checkpoints
- **Safety Monitoring**: Real-time monitoring with configurable alert thresholds

#### 5. Delta Evaluation System (`safla/core/delta_evaluation.py`)
- **Performance Delta**: Reward improvements per token with historical tracking
- **Efficiency Delta**: Throughput improvements per resource with multi-resource support
- **Stability Delta**: Divergence-based stability measurement with trend analysis
- **Capability Delta**: New capabilities acquisition tracking relative to total capability space
- **Adaptive Weighting**: Context-aware weight adjustment for different operational priorities

## 🚀 Quick Start

### Installation

```bash
# Clone the repository
git clone https://github.com/ruvnet/SAFLA.git
cd SAFLA

# Install dependencies
pip install -r requirements.txt

# Set up environment variables
cp .env.example .env
# Edit .env with your configuration
```

### Basic Usage

```python
from safla.core.hybrid_memory import HybridMemoryArchitecture
from safla.core.meta_cognitive_engine import MetaCognitiveEngine
from safla.core.safety_validation import SafetyValidationFramework

# Initialize core components
memory = HybridMemoryArchitecture()
meta_engine = MetaCognitiveEngine()
safety_framework = SafetyValidationFramework()

# Start the system
await memory.start()
await meta_engine.start()
await safety_framework.start()

# Store and retrieve memories
memory_id = await memory.store_vector_memory(
    content="Example content",
    embedding=[0.1, 0.2, 0.3, ...],  # 512-dimensional vector
    metadata={"type": "example", "timestamp": time.time()}
)

# Retrieve similar memories
similar_memories = await memory.search_similar_memories(
    query_embedding=[0.1, 0.2, 0.3, ...],
    top_k=5,
    similarity_threshold=0.8
)

# Set goals and monitor performance
goal_id = await meta_engine.goal_manager.add_goal(
    description="Optimize system performance",
    priority=0.8,
    target_metrics={"accuracy": 0.95, "latency": 100}
)

# Validate system modifications
modification_data = {
    "memory_usage": 500000000,  # 500MB
    "cpu_usage": 0.7,
    "new_capabilities": 2,
    "total_capabilities": 10
}

validation_result = await safety_framework.validate_system_modification(modification_data)
if validation_result.is_approved:
    print("Modification approved")
else:
    print(f"Modification rejected: {validation_result.message}")
```

### MCP Integration

```python
from safla.core.mcp_orchestration import MCPOrchestrator

# Initialize MCP orchestrator
orchestrator = MCPOrchestrator()

# Register MCP servers
await orchestrator.server_manager.register_server(
    name="context7",
    connection_config={
        "command": "npx",
        "args": ["-y", "@upstash/context7-mcp"]
    }
)

# Coordinate agents
task_result = await orchestrator.agent_coordinator.assign_task(
    task_type="research",
    requirements=["context7"],
    context={"topic": "machine learning"}
)
```

## 📊 Delta Evaluation

The system implements formal quantification of improvements using:

```
Δ_total = α₁ × Δ_performance + α₂ × Δ_efficiency + α₃ × Δ_stability + α₄ × Δ_capability
```

Where:
- **Δ_performance**: `(current_reward - previous_reward) / tokens_used`
- **Δ_efficiency**: `(current_throughput - previous_throughput) / resource_used`
- **Δ_stability**: `1 - divergence_score` (with trend analysis)
- **Δ_capability**: `new_capabilities / total_capabilities`

```python
from safla.core.delta_evaluation import DeltaEvaluator

evaluator = DeltaEvaluator()

# Evaluate system improvements
result = evaluator.evaluate_delta(
    performance_data={
        'current_reward': 0.92,
        'previous_reward': 0.85,
        'tokens_used': 1000
    },
    efficiency_data={
        'current_throughput': 150,
        'previous_throughput': 120,
        'resource_used': 0.8
    },
    stability_data={
        'divergence_score': 0.15
    },
    capability_data={
        'new_capabilities': 2,
        'total_capabilities': 10
    },
    context="performance_critical"
)

print(f"Total Delta: {result.total_delta}")
print(f"Improvement Detected: {result.is_improvement()}")
```

## 🛡️ Safety Features

### Safety Constraints

```python
from safla.core.safety_validation import SafetyConstraint, ConstraintType

# Define safety constraints
memory_constraint = SafetyConstraint(
    name="memory_limit",
    constraint_type=ConstraintType.HARD,
    description="Maximum memory usage limit",
    rule="memory_usage <= 1000000000",  # 1GB
    threshold=1000000000,
    violation_action="emergency_stop"
)

# Add to safety framework
safety_framework.constraint_engine.add_constraint(memory_constraint)
```

### Risk Assessment

```python
from safla.core.safety_validation import RiskFactor

# Define risk factors
def calculate_memory_risk(data):
    memory_usage = data.get('memory_usage', 0)
    return min(memory_usage / 1000000000, 1.0)  # Normalize to 0-1

memory_risk = RiskFactor(
    name="memory_risk",
    description="Risk based on memory usage",
    weight=0.3,
    calculator=calculate_memory_risk
)

safety_framework.risk_scorer.add_risk_factor(memory_risk)
```

## 🧠 Memory Management

### Vector Memory Operations

```python
# Store vector memories with different embedding dimensions
await memory.vector_memory.store_memory(
    content="Technical documentation",
    embedding_512=[...],  # 512-dimensional
    embedding_768=[...],  # 768-dimensional
    metadata={"type": "documentation", "domain": "technical"}
)

# Search with different similarity metrics
results = await memory.vector_memory.search_memories(
    query_embedding=[...],
    similarity_metric="cosine",  # or "euclidean", "dot_product", "manhattan"
    top_k=10,
    threshold=0.8
)
```

### Episodic Memory

```python
# Store episodic experiences
episode_id = await memory.episodic_memory.store_episode(
    content="User interaction session",
    context={"user_id": "123", "session_type": "support"},
    outcome="resolved",
    metadata={"duration": 300, "satisfaction": 0.9}
)

# Retrieve episodes by time range
episodes = await memory.episodic_memory.get_episodes_by_timerange(
    start_time=start_timestamp,
    end_time=end_timestamp
)
```

### Semantic Memory

```python
# Add knowledge to semantic memory
node_id = await memory.semantic_memory.add_node(
    content="Machine Learning",
    node_type="concept",
    properties={"domain": "AI", "complexity": "high"}
)

# Create relationships
await memory.semantic_memory.add_edge(
    source_id=node_id,
    target_id=other_node_id,
    relationship="is_related_to",
    weight=0.8
)

# Query knowledge graph
related_concepts = await memory.semantic_memory.get_related_nodes(
    node_id=node_id,
    relationship_type="is_related_to",
    max_depth=2
)
```

## 🔧 Configuration

### Environment Variables

```bash
# Memory Configuration
SAFLA_VECTOR_DIMENSIONS=512,768,1024,1536
SAFLA_MAX_MEMORIES=10000
SAFLA_SIMILARITY_THRESHOLD=0.8

# Safety Configuration
SAFLA_MEMORY_LIMIT=1000000000
SAFLA_CPU_LIMIT=0.9
SAFLA_SAFETY_MONITORING_INTERVAL=1.0

# MCP Configuration
SAFLA_MCP_TIMEOUT=30
SAFLA_MCP_MAX_RETRIES=3
SAFLA_MCP_HEALTH_CHECK_INTERVAL=60
```

### MCP Server Configuration

Create `.roo/mcp.json`:

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp"]
    },
    "perplexity": {
      "command": "python",
      "args": ["-m", "mcp_perplexity"]
    }
  }
}
```

## 🧪 Testing

```bash
# Run all tests
python -m pytest tests/

# Run specific test suites
python -m pytest tests/test_hybrid_memory.py
python -m pytest tests/test_meta_cognitive.py
python -m pytest tests/test_safety_validation.py

# Run with coverage
python -m pytest --cov=safla tests/
```

## 📚 API Reference

### Core Classes

- **`HybridMemoryArchitecture`**: Main memory management system
- **`MetaCognitiveEngine`**: Meta-cognitive reasoning and adaptation
- **`MCPOrchestrator`**: Distributed agent coordination
- **`SafetyValidationFramework`**: Safety constraints and validation
- **`DeltaEvaluator`**: System improvement quantification

### Key Methods

#### Memory Operations
- `store_vector_memory(content, embedding, metadata)`: Store vector memory
- `search_similar_memories(query_embedding, top_k, threshold)`: Search similar memories
- `consolidate_memories()`: Transfer memories between layers

#### Meta-Cognitive Operations
- `add_goal(description, priority, target_metrics)`: Add system goal
- `select_strategy(context, available_strategies)`: Select optimal strategy
- `monitor_performance(metrics)`: Monitor system performance

#### Safety Operations
- `validate_system_modification(data)`: Validate proposed changes
- `create_safety_checkpoint(name, description)`: Create system checkpoint
- `emergency_stop(reason)`: Trigger emergency stop

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🧾 Credits

**Created by rUv**

SAFLA represents a comprehensive approach to autonomous AI systems with built-in safety, sophisticated memory management, and meta-cognitive capabilities. The system demonstrates how advanced AI architectures can be implemented with proper safety constraints and validation mechanisms.

---

*This README reflects the actual implementation of SAFLA as a sophisticated AI/ML system, not a conceptual framework.*