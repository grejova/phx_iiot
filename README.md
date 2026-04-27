#PHX IIoT — Runtime Orchestration Layer
Decalarative and Deterministic SCADA/MES Foundation Provisioning
Ignition as Code

PHX IIoT is an experimental rebuild provisioning layer for Inductive Automation Ignition. It serves as an architectural research prototype to test deterministic state generation, topology management, and Infrastructure as Code (IaC) principles within industrial SCADA/MES environments.

"The system is not the truth. The definition is."

The core engineering focus is state-aware deployment semantics. Rather than manually configuring a SCADA environment, this layer deterministically generates the foundation (Tags, UDT instances, Database schemas, and Perspective UI structure) from a single ISA-95-aligned CSV model.

The Engineering Problem

Traditional SCADA deployments often suffer from:

Weakly validated states (false-positive deployment success)
Manual scaffolding preventing repeatable teardown/rebuild cycles
High Time-to-Value (TTV) due to repetitive engineering effort

PHX IIoT explores a state-machine driven deployment model, testing whether SCADA foundations can be treated as reproducible, software-defined infrastructure.

The core rule is:

Same input → same generated runtime

Conceptual Capabilities
1. Deterministic Deployment Lifecycle

Deployments follow a strict state progression for traceability:

Supported execution modes:

Fresh bootstrap deploy
Idempotent no-op redeploy
Drift corrective reconcile
Wipe / reset lifecycle
Restore from deploy journal
CRC-based state detection
Topology diffing
Historian readiness gating
Partial rollback handling
Locking / run ownership control
Throughput checkpoints & metrics
2. Validation & Drift Observation

The system evaluates deployments against structural invariants:

Topology integrity (no orphans, no cycles)
CRC-based source integrity validation
Historian schema consistency
Mapping completeness (runtime ↔ OPC ↔ tags)
3. CRC Modeling & Idempotency

A structural CRC is computed from the manifest.

Fast No-Op Execution:
If manifest_crc == runtime_crc, execution is skipped immediately.

This enables deterministic, idempotent redeployment without rewriting runtime state.

4. Historian-Aware Handshakes

The system models historian behavior as an asynchronous subsystem:

Bootstrap delay handling
Quiet window validation
Deferred commit states
Partial readiness detection
Output Artifacts & Immutable Journaling

All state transitions are stored in an execution log (PHX_DEPLOY_LOG), enabling full replayability and auditability.

Example schema:

run_id	action	machine_count	tag_count	manifest_crc	runtime_crc	execution_mode	status
RUN_437	DEPLOY	10	430	18DB897E	18DB897E	Full Apply	DONE
RUN_551	NO_OP	10	0	18DB897E	18DB897E	No-Op	DEFERRED
Engineering Research Program & Test Phases

This project maps system behavior under increasing OT/IT stress conditions:

DONE — Phoenix Phase
Full topology rebuild
Deterministic idempotency validation
One-click declarative system reconstruction
DONE — Icarus Phase
~30,000+ tag provisioning
~2,700 tags/sec sustained throughput
Historian degradation boundary observation
PLANNED — Connection Storm
OPC-UA subscription saturation testing
Gateway thread exhaustion analysis
PLANNED — Atlas Phase
Database I/O saturation and write choke simulation
PLANNED — Hades Phase
Network instability matrix (packet loss, flapping, timeout cascades)
VISION — Daedalus Phase
Machine-to-financial KPI traceability
VISION — Artemis Phase
Predictive intelligence layer on top of deterministic runtime
VISION — Prometheus Phase
Embedded PLC simulation environment for CI loops
Formal Execution Benchmarks

Environment: Ignition 8.3.2 / JVM constrained runtime (M1 Pro / 2GB heap)

Scale Target	Runtime Size	Deployment Time	Peak Throughput	Observation
Small Matrix	~1,000 tags	18.6 sec	~2,700 tags/sec	Stable
Single Site	~10,000 tags	24.5 sec	~2,700 tags/sec	Stable
Stress Point	~30,000+	28.7 sec	~2,700 tags/sec	GC pressure visible
Limit Point	~100,000+	TBD	TBD	Atomicity threshold under study
