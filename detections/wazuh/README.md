# Wazuh detections (MVP)

This directory contains detection rules, tuning notes, and references used in the lab.

## Structure (planned)
- `rules/` — custom rules
- `decoders/` — custom decoders (if needed)
- `notes/` — tuning notes and false-positive handling

## Conventions
Each detection should document:
- data source
- rule logic (high level)
- test method
- known false positives + mitigations
