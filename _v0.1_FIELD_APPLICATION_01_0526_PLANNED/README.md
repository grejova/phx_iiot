# PHX IIoT Field Pilot

## Read-Only Brownfield Observability Brief

**Target Area:** Automotive components manufacturing  
**Platform:** Ignition  
**Pilot Type:** Read-only observability and runtime foundation discovery  
**Status:** Pre-field preparation

---

## Purpose

This pilot evaluates whether PHX IIoT can discover, structure, and generate a repeatable read-only Ignition runtime foundation for a brownfield manufacturing environment.

The first goal is not to replace existing systems or directly optimize production. The goal is to understand what field data, asset hierarchy, signal mapping, and topology foundation are required before practical efficiency visibility can be built from real field data.

---

## Non-Goals

This pilot does not include:

- PLC write operations
- Control logic changes
- Production decision automation
- Live process control
- SCADA / MES / alarm / quality system replacement

PHX IIoT will operate only as a read-only observability layer.

---

## Scope

The pilot includes:

- Asset, machine, line, cell, and station discovery
- PLC / SCADA / OPC-UA data source mapping
- Read-only tag and signal discovery
- ISA-95-like topology manifest creation
- Canonical asset-signal mapping
- Read-only Ignition runtime foundation preparation
- Basic dashboard, status, trend, and asset-view preparation
- Gap and limitation documentation

---

## Access Prerequisites

Preferred inputs:

- Read-only OPC-UA access, if available
- Existing tag list or namespace visibility
- Basic asset / machine / line structure
- Sample signal list or tag export
- Historian or trend access, if available
- Plant-side contact for naming and semantics validation

---

## Pilot Stages

### Stage 0.0 — PHX Deploy API Server and Runtime UI Context Preparation

**Status:** Current — 11 May 2026  
**Phase Type:** Pre-field platform preparation

Stage 0.0 prepares the external PHX Deploy API Server and the reusable Ignition Runtime UI Context foundation before any measured field execution begins.

The original PHX IIoT structure was built as a monolithic lab PoC. For the field pilot, the platform will be separated into:

- Local Ignition runtime
- PHX Runtime UI context
- External PHX Deploy API Server
- Controlled deployment, validation, and runtime-generation logic

The PHX Deploy API Server is intended to keep deployment logic, validation routines, runtime generation methods, and controlled backend operations outside the local Ignition project as much as possible. It should expose only predefined operations to known clients, with validated inputs and expected response structures.

Stage 0.0 also prepares a Runtime UI Context rehydration path for new Ignition Perspective environments. The goal is to start from a blank Ignition Perspective project/canvas and recreate the standard PHX Runtime UI context through a controlled Script Library package instead of manually rebuilding the same view foundation for each environment.

Planned Script Library context:

- `PHX_Deploy_API_Client`
- `PHX_Runtime_Context`
- `PHX_Runtime_Context_1`
- `PHX_Runtime_Context_Components`
- `PHX_Runtime_Context_Ignite`
- `PHX_Runtime_Context_Plant_Overview`
- `PHX_Runtime_Context_System_Health`
- `PHX_Runtime_Context_Trend_Tracking`
- `_ConPar`

Expected output:

- PHX Deploy API Server skeleton
- Controlled API interface for deployment and validation operations
- Separation between local UI, runtime, and backend orchestration logic
- Baseline deploy / redeploy test path
- Deployment log and result reporting structure
- Blank Ignition Perspective rehydration path
- Script Library based PHX Runtime UI Context recreation
- Verification of expected PHX runtime context modules

---

### Stage 0.1 — Field Library and Standard Setup Preparation

**Phase Type:** Pre-field library preparation

Stage 0.1 prepares the reusable field-side setup package required before entering a real plant discovery phase.

This includes simulated manufacturing assets, sample OPC-UA structures, topology templates, dashboard/view templates, reusable setup scripts, and a field discovery checklist. The reusable library also carries the PHX Runtime UI Context rehydration package prepared during Stage 0.0.

Expected output:

- Simulated manufacturing asset model
- Example topology manifest
- Sample OPC-UA signal map
- Reusable topology and signal-mapping templates
- Initial dashboard/view templates
- Field discovery checklist
- Baseline reusable setup library
- PHX Runtime UI Context rehydration package
- Prepared standard setup package for Stage 1

---

### Stage 1 — Field Discovery

**Phase Type:** Start of actual PHX IIoT field pilot

Understand the real plant structure and available read-only data sources.

Expected output:

- Field asset hierarchy
- Machine / line / cell / station map
- Read-only signal inventory
- Available PLC / SCADA / OPC-UA endpoint notes
- Canonical asset-signal map
- Initial topology manifest
- Gap and limitation notes

---

### Stage 2 — Read-Only Runtime Foundation Generation

Generate the read-only Ignition runtime foundation from the field-derived topology manifest.

Expected output:

- Generated read-only Ignition runtime foundation
- Runtime structure based on the field-derived topology manifest
- Read-only tag and signal structure
- Basic runtime verification
- Deployment log and generation result
- Initial consistency check between manifest and generated runtime

---

### Stage 3 — Observability and Efficiency Tracing

Evaluate which basic status, trend, and efficiency-related views can be created from available field data.

Expected output:

- Basic asset status views
- Basic trend views
- Initial efficiency-related signal visibility
- Available / missing signal classification
- Practical observability limits
- Gap report for later instrumentation or integration

---

## Field Pilot Timing Clarification

Stage 0.0 and Stage 0.1 are pre-field preparation stages. They prepare the API server, reusable field library, runtime UI context, setup templates, simulated assets, and deployment structure before a realistic brownfield pilot begins.

The actual PHX IIoT field pilot starts at:

**Stage 1 — Field Discovery**

Measured field setup time should start only after Stage 0.1 is completed.

---

## Final Deliverables

- Read-only field asset hierarchy
- Signal and endpoint inventory
- Initial topology manifest
- Canonical asset-signal map
- Initial read-only Ignition foundation
- Basic dashboard / trend view set
- Gap and limitation report
- Recommendation note for the next pilot phase

---

## Measurement Outputs

| Measurement | Result |
|---|---|
| Pre-field preparation excluded from measured setup time | |
| PHX Deploy API Server prepared before field pilot | |
| Reusable field library prepared before Stage 1 | |
| Runtime UI Context rehydration package prepared | |
| Actual field pilot start stage | Stage 1 |
| Number of mapped assets | |
| Number of mapped machines | |
| Number of mapped lines | |
| Number of mapped cells / stations | |
| Number of discovered read-only signals | |
| Number of connected OPC-UA tags | |
| Available efficiency-related signals | |
| Missing efficiency-related signals | |
| Field data gaps requiring later instrumentation | |
| Time to create topology manifest | |
| Time to generate runtime foundation | |
| Runtime deploy duration | |
| Re-deploy result consistency | |
| Runtime mismatch / drift detected | |
| Historian / trend continuity established | |
| Basic dashboard views generated | |
| Main technical limitation observed | |
| Next improvement target | |

---

## Core Statement

PHX IIoT is being tested as a read-only, repeatable, topology-driven observability foundation for brownfield manufacturing environments.

The goal is to understand what kind of digital foundation is required before practical efficiency visibility can be built from real field data. Stage 0.0 and Stage 0.1 prepare the PHX Deploy API Server, reusable field library, Runtime UI Context, and standard setup foundation. The actual field pilot begins at Stage 1.
