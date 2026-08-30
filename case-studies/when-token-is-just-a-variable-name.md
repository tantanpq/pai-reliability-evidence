# When “Token” Is Just a Variable Name

## Situation

A portable source-safety gate produced a false positive because ordinary implementation code used a property name containing token-like language. The easy shortcut would have been to broadly allow anything containing that word, which would weaken the safety boundary.

## Repair pattern

The verified repair followed a narrower path:

1. close exact source provenance first;
2. reproduce the specific false-positive trigger;
3. narrow only the semantic content classifier;
4. retain independent path/name checks;
5. retain fail-closed handling for tested private-key, explicit-placeholder, and credential-shaped literal classes;
6. preserve byte-fidelity, scope, and carrier checks;
7. replay both positive and negative adversarial fixtures against frozen evidence;
8. require independent QA before any activation decision.

## Verified outcome

The repair reached terminal `DONE`, and independent QA also reached `DONE` with no blocker. QA independently re-read the relevant frozen evidence and passed fixture classes covering sensitive content, benign identifiers/properties, path, scope, carrier, UTF-8, and BOM behavior.

The key result was not “allow token names.” It was more precise:

> classify values and context, not scary substrings alone.

## Why this matters

Over-broad scanning creates two bad incentives at once: safe code can be blocked, while operators become tempted to add sweeping bypasses. A bounded classifier with explicit negative and positive fixtures reduces false positives without turning convenience into a new authority path.

## Limits

This case study does not claim universal secret detection, repository-wide safety, production activation, or external-customer repeatability. The public version contains no private source, real credentials, internal paths, or sensitive logs.
