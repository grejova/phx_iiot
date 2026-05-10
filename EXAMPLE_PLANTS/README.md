# Example Plants

This folder contains safe public topology manifest examples used to demonstrate PHX IIoT source-defined runtime provisioning behavior.

These files are synthetic demo inputs. They are not customer exports, production plant data, or Ignition gateway exports.

The examples are intended to show:

- ISA-95-aligned hierarchy modeling
- topology-driven runtime generation
- manifest variation and diff behavior
- deterministic source input structure
- controlled reconciliation test cases

Key example groups:

- `1-*` Datacenter-style topology and drift/reconciliation variants
- `2-*` Small-to-large synthetic plant scale examples
- `3-*` ABS / water-process style multi-PLC examples
- `5-*` Motor list generation example

See `manifest_schema.md` for the public schema overview.
