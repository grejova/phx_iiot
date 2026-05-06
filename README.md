# PHX IIoT — Runtime Orchestration Layer
### Declarative and Deterministic SCADA/MES Foundation Provisioning
**Ignition as Code**

PHX IIoT is an experimental rebuild provisioning layer for Inductive Automation Ignition. It serves as an architectural research prototype to test deterministic state generation, topology management, and Infrastructure as Code (IaC) principles within industrial SCADA/MES environments.

> *"The system is not the truth. The definition is."*

The core engineering focus is state-aware deployment semantics. Rather than manually configuring a SCADA environment, this layer deterministically generates the foundation (Tags, UDT instances, Database schemas, and Perspective UI structure) from a single ISA-95-aligned CSV model.

## Concept Videos:

### Full Topology Rebuild - Phoenix Phase
1- Rebuild Provisioning Layer: https://youtu.be/BU7qWBIWs_4

2- Rebuild Provisioning & Reconciliation Layer: https://youtu.be/VquVNYi_Z9U

### Tag Burst Provisioning - Icarus Phase;
+30k Tags Provisioning , in a minute: https://youtu.be/Ci-ngGc4NF8


## The Engineering Problem

Traditional SCADA deployments often suffer from:
*   **Weakly validated states** (false-positive deployment success)
*   **Manual scaffolding** preventing repeatable teardown/rebuild cycles
*   **High Time-to-Value (TTV)** due to repetitive engineering effort

PHX IIoT explores a state-machine driven deployment model, testing whether SCADA foundations can be treated as reproducible, software-defined infrastructure. 

The core rule is:
> **`Same input → same generated runtime`**

---

## Conceptual Capabilities

### 1. Deterministic Deployment Lifecycle
Deployments follow a strict state progression for traceability. Supported capabilities and execution modes include:
*   Fresh bootstrap deploy
*   Idempotent no-op redeploy
*   Drift corrective reconcile
*   Wipe / reset lifecycle
*   Restore from deploy journal
*   CRC-based state detection
*   Topology diffing
*   Historian readiness gating
*   Partial rollback handling
*   Locking / run ownership control
*   Throughput checkpoints & metrics

### 2. Validation & Drift Observation
The system evaluates deployments against structural invariants:
*   **Topology integrity:** No orphans, no circular dependencies.
*   **CRC-based validation:** Source integrity verification.
*   **Historian schema consistency:** Ensuring database state matches expectations.
*   **Mapping completeness:** `runtime` ↔ `OPC` ↔ `tags`

### 3. CRC Modeling & Idempotency
A structural CRC is computed from the manifest. 

*   **Fast No-Op Execution:** If `manifest_crc == runtime_crc`, execution is skipped immediately. This enables deterministic, idempotent redeployment without rewriting or interrupting existing runtime state.

### 4. Historian-Aware Handshakes
The system models historian behavior as an asynchronous subsystem:
*   Bootstrap delay handling
*   Quiet window validation
*   Deferred commit states
*   Partial readiness detection

---

## Output Artifacts & Immutable Journaling

All state transitions are stored in an execution log (`PHX_DEPLOY_LOG`), enabling full replayability and auditability.

*Example Schema:*

| run_id | action | machine_count | tag_count | manifest_crc | runtime_crc | execution_mode | status |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `RUN_437` | `DEPLOY` | 10 | 430 | `18DB897E` | `18DB897E` | Full Apply | `DONE` |
| `RUN_551` | `NO_OP` | 10 | 0 | `18DB897E` | `18DB897E` | No-Op | `DEFERRED` |

---

## Engineering Researchs (Controlled Chaos Experiments)

This project maps system behavior under increasing OT/IT stress conditions:

* **[DONE] Test #1 — Full Topology Rebuild** <br>
  Idempotency proof, one-click rebuild in seconds, hot-patching.  *(Phoenix Phase)*

* **[DONE] Test #2 — Tag Burst Provisioning** <br>
  Historian write degradation confirmed at ~2,700 tags/sec, ~30k tags.  *(Icarus Phase)*

* **[PLANNED] Test #3 — Subscription Storm** <br>
  Gateway memory collapse threshold under mass OPC UA subscriptions.  *(Connection Storm Phase)*

* **[PLANNED] Test #4 — DB Overweight (Max IO Scope)** <br>
  Maximum database writes with simulated disk errors.  *(Atlas Phase)*

* **[PLANNED] Test #5 — Connection Loss Matrix** <br>
  Every failure combination: partial loss, flapping, timeout cascades.  *(Hades Phase)*

* **[PLANNED] Test #6 — Machine to Capital Impact Tracing** <br>
  Data path from machine sensor to financial loss number.  *(Daedalus Phase)*

* **[VISION] Test #7 — Predictive Intelligence Engine** <br>
  ML layer on top of the IaC stack.  *(Artemis Phase)*

* **[VISION] Test #8 — Built-In PLC Simulator & Playground** <br>
  Embedded PLC simulation environment for CI loops.  *(Prometheus Phase)*
  
---

## Formal Execution Benchmarks

*Environment: Ignition 8.3.2 / JVM constrained runtime (M1 Pro / 2GB heap)*

| Scale Target | Runtime Size | Deployment Time | Peak Throughput | Observation |
| :--- | :--- | :--- | :--- | :--- |
| **Small Matrix** | ~1,000 tags | 18.6 sec | ~2,700 tags/sec | Stable |
| **Single Site** | ~10,000 tags | 24.5 sec | ~2,700 tags/sec | Stable |
| **Stress Point** | ~30,000+ tags | 28.7 sec | ~2,700 tags/sec | GC pressure visible (Unsustainable at ~35k+ tags) |
| **Limit Point** | ~100,000+ tags | *TBD* | *TBD* | GC pressure fault (Gateway Restart) |
