# Integration Guide - Traditional Medicine Reasoning Library (Non-Medical)

Purpose: use extracted traditional medicine logic/theory as a business reasoning engine for:
- troubleshooting
- mindset opening
- behavior change coaching

This integration is non-medical and non-therapeutic.

## 1) Allowed Knowledge Types
- system thinking logic (interdependence, balance, cycles)
- pattern differentiation logic (root vs symptom style reasoning)
- progression/stage reasoning
- adaptation and habit stabilization reasoning

## 2) Forbidden Knowledge Types
- diagnosis guidance for disease
- treatment protocol
- dosage/formulation instructions
- efficacy promises linked to product cure/treatment

## 3) Runtime Flow
1. Ingest source excerpt.
2. Convert to `Reasoning Atom` using `knowledge/REASONING_SCHEMA_VN.md`.
3. Run safety filter from `knowledge/TRAD_MED_REASONING_GUARDRAILS.md`.
4. Map atom to one of 3 output modes:
- `troubleshoot_mode`
- `mindset_opening_mode`
- `behavior_change_mode`
5. If unsafe wording appears, force rewrite via `knowledge/SAFE_REWRITE_TEMPLATES_VN.md`.

## 4) Evidence and Confidence
Each atom must include:
- source reference
- confidence level
- prohibited interpretation notes

Low-confidence atoms cannot be used for persuasive product claims.

## 5) Release Rule
Do not release final campaign copy until:
1. no medical claim intent
2. no guarantee language
3. disclosure line is present
4. human reviewer accepts
