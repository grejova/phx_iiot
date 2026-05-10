# Manifest Schema Overview

PHX uses a flat CSV-style source definition to describe plant/runtime topology.

The public examples are simplified, synthetic manifests. They are intended to make the input model reviewable without exposing customer-specific plant data or private deployment logic.

## Conceptual Model

A manifest row represents an asset or equipment node that can be materialized into an Ignition runtime foundation.

Typical semantics include:

- enterprise / site / area / line / cell / asset hierarchy
- explicit parent-child relationships
- UDT or asset type selection
- PLC / OPC server reference
- OPC index or addressing reference
- stable source identity for repeatable provisioning
- topology variation for drift and reconciliation testing

## Diff Examples

Some files intentionally represent changed topology states:

- `diff_topology` files show topology changes
- `diff_reconcile` files support governed reconciliation tests
- `diff_chaos` files are stress or disorder examples for validation

## Public Boundary

These examples are not production plant exports.

They are safe public source-definition examples used to demonstrate the PHX provisioning and reconciliation model.
