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

### Stage 0.0 — Pre-Field Platform Readiness (Current : 10 May 2026)

The original PHX IIoT structure was built as a monolithic PoC for lab validation.

For the field pilot, the platform will be prepared with cleaner separation between UI actions, backend logic, and runtime generation flow.

Expected output:

- Safer pre-field platform structure
- Baseline deploy/redeploy test
- Deployment log and result reporting structure

---

### Stage 0.1 — Field Work Preparation

Prepare simulated manufacturing assets, sample OPC-UA structures, topology templates, dashboard templates, and field discovery checklist before the site visit.

Expected output:

- Simulated manufacturing asset model
- Example topology manifest
- Sample OPC-UA signal map
- Initial dashboard/view templates
- Field discovery checklist

---

### Stage 1 — Field Discovery

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

Details will be added based on Stage 0 and Stage 1 findings.

---

### Stage 3 — Observability and Efficiency Tracing

Evaluate which basic status, trend, and efficiency-related views can be created from available field data.

Details will be added based on field discovery results.

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
