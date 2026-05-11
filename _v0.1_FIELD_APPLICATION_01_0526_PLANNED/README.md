# PHX IIoT Field Pilot

## Read-Only Brownfield Observability Brief

**Target Area:** Automotive components manufacturing  
**Platform:** Ignition  
**Pilot Type:** Read-only observability and runtime foundation discovery  
**Status:** Pre-field preparation  

---

## Purpose

This pilot evaluates whether PHX IIoT can help discover, structure, and generate a read-only Ignition runtime foundation for a brownfield manufacturing environment.

The first goal is not to replace existing systems or directly optimize production.

The goal is to understand what field data, asset hierarchy, signal mapping, and topology foundation are required before practical efficiency visibility can be built from real field data.

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

### Stage 0.0 — PHX Deploy API Preparation  
**Status:** Current — 10 May 2026  
**Phase Type:** Pre-field platform preparation

The original PHX IIoT structure was built as a monolithic PoC for lab validation.

For the field pilot, the platform will be reorganized around a cleaner separation between the local Ignition runtime, deployment logic, and external orchestration services.

In this stage, an external **PHX Deploy API** system will be prepared outside the plant environment. Its purpose is to keep deployment logic, runtime generation methods, validation routines, and controlled backend operations outside the local Ignition project as much as possible.

The initial external API interface is defined as:

- **System Name:** PHX Deploy API
- **Version:** 1.0.0
- **Specification:** OAS 3.1
- **OpenAPI Schema Endpoint:** `/openapi.json`
- **Interface Role:** API-key-protected secure external interface for controlled PHX deployment operations

The PHX Deploy API is expected to expose only controlled and predefined methods. Access will be limited through known API keys, known method names, validated method inputs, and expected response structures.

In practical terms, the PHX Deploy API acts as a secure external-world interface between the local PHX runtime environment and the controlled deployment/orchestration logic. It is not intended to expose unrestricted plant data or uncontrolled runtime operations.

This stage is not part of the measured field pilot execution time. It is a platform hardening and preparation step required before PHX IIoT can be tested in a more realistic brownfield setting.

### Stage 0.0 Addition — Runtime UI Context Rehydration Preparation

As part of Stage 0.0, PHX IIoT will also prepare a controlled Runtime UI Context rehydration process for new Ignition Perspective environments.

The purpose of this step is to start from an empty Ignition Perspective canvas and recreate the required PHX Runtime UI context structures through a predefined Script Library package. Instead of manually rebuilding the same Perspective view foundation for every new environment, the PHX field-side library will be used to recreate the standard runtime UI context consistently.

The current planned Script Library context includes:

  * `PHX_Deploy_API_Client`
  * `PHX_Runtime_Context`
  * `PHX_Runtime_Context_1`
  * `PHX_Runtime_Context_Components`
  * `PHX_Runtime_Context_Ignite`
  * `PHX_Runtime_Context_Plant_Overview`
  * `PHX_Runtime_Context_System_Health`
  * `PHX_Runtime_Context_Trend_Tracking`
  * `_ConPar`

These libraries are intended to support the repeatable creation of PHX runtime surfaces such as deploy interaction context, plant overview context, system health context, trend tracking context, ignition/runtime initialization context, shared component helpers, and common parameter/context helpers.

In practical terms, this means that a new Ignition Perspective environment should not require manual recreation of the PHX runtime UI foundation. The target behavior is:

  * start from a blank Ignition Perspective project/canvas
  * load the controlled PHX Script Library package
  * recreate the PHX Runtime UI context structure
  * verify that the expected Perspective runtime views and supporting context modules exist
  * prepare the environment for later topology-driven runtime generation

This does not mean that plant-specific dashboards are fully complete before field discovery. The goal of this step is to prepare the reusable PHX runtime UI foundation so that later field-derived topology, signal mapping, and observability views can be attached to a known Perspective structure.

Expected output:

- External PHX Deploy API preparation
- PHX Deploy API versioned as 1.0.0
- OAS 3.1-compatible OpenAPI schema exposed through `/openapi.json`
- API-key-protected secure external interface
- Cleaner separation between UI actions, backend logic, and runtime generation
- API-key-based controlled access model
- Predefined deployment and validation methods
- Input validation and expected output structure
- Safer pre-field platform structure
- Baseline deploy/redeploy test
- Deployment log and result reporting structure

---

### Stage 0.1 — Field Library and Standard Setup Preparation  
**Phase Type:** Pre-field library preparation

This stage prepares the reusable field-side library required for a standard PHX IIoT setup.

The reusable field-side library will also include the PHX Runtime UI Context rehydration package prepared during Stage 0.0. This allows a new Ignition Perspective environment to start from a blank project state and receive the standard PHX runtime UI context before plant-specific topology and signal mapping are applied.

The purpose is to create the minimum reusable foundation before entering the real plant discovery phase: simulated manufacturing assets, sample OPC-UA structures, topology templates, dashboard templates, reusable setup scripts, and a field discovery checklist.

Expected output:

- Simulated manufacturing asset model
- Example topology manifest
- Sample OPC-UA signal map
- Reusable topology and signal-mapping templates
- Initial dashboard/view templates
- Field discovery checklist
- Baseline reusable setup library
- Prepared standard setup package for Stage 1

The measured duration of a standard PHX IIoT setup should start only after this stage is completed.

In other words, Stage 0.0 and Stage 0.1 prepare the platform and reusable library. The actual PHX IIoT field pilot begins at **Stage 1 — Field Discovery**.

---

### Stage 1 — Field Discovery  
**Phase Type:** Start of actual PHX IIoT field pilot

Understand the real plant structure and available read-only data sources.

This is the first stage where the PHX IIoT pilot should be considered as practically starting in the field.

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

Details will be added based on Stage 0 and Stage 1 findings.

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

Details will be added based on field discovery results.

Expected output:

- Basic asset status views
- Basic trend views
- Initial efficiency-related signal visibility
- Available / missing signal classification
- Practical observability limits
- Gap report for later instrumentation or integration

---

## PHX Deploy API Initial Definition

The PHX Deploy API is the controlled external interface prepared for PHX IIoT deployment and runtime foundation operations.

It is designed as an API-key-protected external-world interface, exposing only predefined deployment, validation, and runtime-generation methods.

Initial API definition:

| Item | Value |
|---|---|
| API Name | PHX Deploy API |
| Version | 1.0.0 |
| API Specification | OAS 3.1 |
| OpenAPI Schema | `/openapi.json` |
| Security Model | API-Key protected |
| Interface Purpose | Secure external interface for controlled PHX deployment operations |

The API is expected to support only known methods, known inputs, validated request structures, and expected response formats.

The goal is to keep sensitive deployment logic and backend orchestration outside the local Ignition UI layer while minimizing unnecessary data exposure.

---

## Field Pilot Timing Clarification

Stage 0.0 and Stage 0.1 are pre-field preparation stages.

They are required to prepare the PHX Deploy API, reusable field library, setup templates, simulated assets, and deployment structure before a realistic brownfield pilot can begin.

The measured duration of a standard PHX IIoT field setup should start only after Stage 0.1 is completed.

Therefore, the actual PHX IIoT field pilot starts at:

**Stage 1 — Field Discovery**

This distinction is important because Stage 0.0 and Stage 0.1 represent platform preparation and reusable library development, not the actual field execution time.

---

## Final Deliverables

- Read-only field asset hierarchy
- Signal and endpoint inventory
- Initial topology manifest
- Canonical asset-signal map
- Initial read-only Ignition foundation
- Basic dashboard/trend view set
- Gap and limitation report
- Recommendation note for the next pilot phase

---

## Measurement Outputs

| Measurement | Result |
|---|---|
| Pre-field preparation excluded from measured setup time |  |
| PHX Deploy API prepared before field pilot |  |
| PHX Deploy API version | 1.0.0 |
| PHX Deploy API specification | OAS 3.1 |
| PHX Deploy API schema endpoint | `/openapi.json` |
| PHX Deploy API security model | API-Key protected |
| Reusable field library prepared before Stage 1 |  |
| Actual field pilot start stage | Stage 1 |
| Number of mapped assets |  |
| Number of mapped machines |  |
| Number of mapped lines |  |
| Number of mapped cells / stations |  |
| Number of discovered read-only signals |  |
| Number of connected OPC-UA tags |  |
| Available efficiency-related signals |  |
| Missing efficiency-related signals |  |
| Field data gaps requiring later instrumentation |  |
| Time to create topology manifest |  |
| Time to generate runtime foundation |  |
| Runtime deploy duration |  |
| Re-deploy result consistency |  |
| Runtime mismatch / drift detected |  |
| Historian / trend continuity established |  |
| Basic dashboard views generated |  |
| Main technical limitation observed |  |
| Next improvement target |  |

---

## Core Statement

PHX IIoT is being tested as a read-only, repeatable, topology-driven observability foundation for brownfield manufacturing environments.

The goal is to understand what kind of digital foundation is required before practical efficiency visibility can be built from real field data.

The actual field pilot begins at Stage 1. Stage 0.0 and Stage 0.1 are preparation stages for the external PHX Deploy API, reusable field library, and standard setup foundation.
