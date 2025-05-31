# SAFLA
Self-Aware Feedback Loop Algorithm (python)


## 🔁 SAFLA: Self-Aware Feedback Loop Algorithm (Agentic Edition)

You are building a state-of-the-art autonomous system that implements **SAFLA** — a fully recursive, self-aware feedback loop rooted in the latest agentic AI research. This build is not theoretical. It is real, test-driven, self-reflecting, and capable of patching its own policy via continual divergence, reward, and error analysis.

---

### ⚙️ Environment Setup

* **Codespace**: Internet access enabled
* **MCP configuration**: `@/.roo/mcp.json`
* **Secrets**: Stored in `.env` (used by `requesty.ai`, `context7`, `perplexityai`)
* **Source control**: Commit after each phase to [https://github.com/ruvnet/SAFLA](https://github.com/ruvnet/SAFLA)
* **Mode roles**: Defined in `.roomodes`
* **Instruction template**: `@/mcp-instructions.md`

---

### 🧠 Step 1 — Guided Deep Research (🔍 `deep-research`)

Use MCPs to perform scoped deep research into:

1. **Using `perplexityai` MCP + Sonar LLM**:

   * Topic: “self-aware feedback loop architectures in autonomous agents”
   * Output: `/research/05_final_report/03_findings.md`

2. **Using `context7` MCP**:

   * Topic: “top libraries for divergence detection, vector memory, delta patching, and loop evaluation”
   * Output: `/research/02_data_collection/02_secondary_findings.md`

---

### 🔄 SAFLA Orchestration (via MCP Protocol)

Define and implement a full **Model-Context Protocol (MCP)** orchestration layer. Each cycle of the loop shares, stores, and updates the following:

```json
{
  "context": {
    "goals": [...],
    "constraints": [...],
    "state_snapshot": {...},
    "memory_refs": [...],
    "prior_rationale": "...",
    "prior_reflection": "...",
    "patches_applied": [...]
  },
  "action_proposal": "...",
  "result_observed": "...",
  "metrics": {
    "reward": 0.92,
    "divergence": 0.14,
    "delta_improvement": 0.07
  },
  "status": "pending | complete | patched",
  "task": "reflection | scoring | implementation | critic"
}
```

MCP payloads must be passed between agents (`reflection`, `scorer`, `prompt-generator`, `code`) via `.roo` message passing or `new_task` invocations. Store all serialized contexts in `/memory-bank/context_logs/`.

---

### 📐 Delta Evaluation and Reflection Reuse Loop

Implement a formal **delta evaluation model** to quantify improvement across iterations:

#### 📊 Delta Metric (Δ-score)

```python
Δ = (rewardᵢ - rewardᵢ₋₁) / tokens_usedᵢ
```

* **If** Δ < ε (e.g. 0.01): trigger `mini-reflection` and policy patch loop
* **If** Δ > τ (e.g. 0.2): promote patch to `core-policy-guidelines.md`

Track all Δ-scores across iterations in:

* `/scores/delta_scores.json`
* `/logs/loop_deltas.md`

#### 🔁 Reflection Reuse

Each `reflection_LS{n}.md` must be scored by the `scorer`:

* If `patch_effectiveness_score ≥ 0.8`, reuse it in future `prompt-generator` calls
* Save reusable patches to:
  `/patches/library/generic-patches.md`

Add `reflection_id` tags in prompt history and memory logs for traceability.

---

### 🧠 Agent Modes (from `.roomodes`)

Use the following roles in your recursive loop:

| Mode                  | Function                                                 |
| --------------------- | -------------------------------------------------------- |
| 🧠 `memory-manager`   | Stores embeddings, computes JSD, and prunes              |
| 💬 `prompt-generator` | Produces next-step action prompts with deltas and memory |
| 🔄 `reflection`       | Writes new patch notes, checks past patch effectiveness  |
| 🧐 `critic`           | Detects logic flaws, offers commentary                   |
| 🎯 `scorer`           | Calculates Δ, JSD, reward change, and patch success      |
| 🧪 `tdd`              | Red-green-refactor + test scaffolding                    |
| 🧠 `code`             | Writes modular implementations (<500 lines)              |
| ♾️ `mcp`              | Handles integrations with requesty, Sonar, context7      |
| 🏁 `final-assembly`   | Merges code, metrics, and results into `/final.md`       |

Each role must call `spawn new_task` and conclude with `attempt_completion`.

---

### 📦 Execution Phases

1. **/memory-bank/**

   * `store.py`: SQLite + JSD pruning
   * `README.md`: define memory layers, delta logic, and storage structure

2. **/cli/**

   * `safla run`: Full loop executor
   * `safla step`: Trigger one mode at a time

3. **/tests/**

   * Test coverage for: JSD, patch success, prompt selection, MCP health

4. **/orchestration/**

   * `run_loop.py`: Recursive mode orchestrator
   * `workflow.json`: DAG or step-graph for mode transitions

---

### ✅ Evaluation Conditions

At each loop, log:

* `Δ-score` vs. previous
* `JSD` vs. previous state
* `token usage`
* `patch applied (y/n)`
* `reflection reused (y/n)`

If no improvement is detected for 3 loops:

* Trigger escalation to `meta-reflection`
* Write `loop_stall_report.md`

---

### 📘 Output Artifacts

* `@/plans/research.md`: From Perplexity + Context7
* `/final.md`: Full output with diagrams and scores
* `/reflection/`: All patches, reused or rejected
* `/memory-bank/`: Snapshot DBs, embedding deltas
* `/scores/`: Delta history, patch effectiveness, loop cost

---

### 🧾 Identity

**Created by rUv**
This is recursive, modular autonomy in motion. A feedback loop that reflects, scores, patches, and evolves — autonomously.
 