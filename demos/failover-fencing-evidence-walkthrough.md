# Demo: Failover and Fencing Evidence Walkthrough

A short, evidence-first walkthrough for explaining the verified simulation without exposing private implementation details.

## 1. Establish the safety question

Can a standby take over after a failure without creating two mutable owners or letting the old owner resume unsafe writes?

## 2. Show the gates

Walk through the required conditions: explicit owner state, strict lease expiry, provenance/dependency revalidation, no terminal result, deterministic contender ordering, and safe shared-state/clock conditions.

## 3. Show the fencing transition

Explain that takeover creates a newer fencing token and leaves the previous token unable to authorize mutation. The important observable is not merely “another node started”; it is “ownership advanced and stale authority stopped working.”

## 4. Show adversarial cases

Use four examples from the verified matrix:

- heartbeat disappears but lease is still active → no takeover;
- two contenders arrive without established ordering → fail closed;
- prior owner returns with an old token → mutation rejected;
- terminal result already exists → takeover blocked.

## 5. Close with evidence and limits

The captured simulation passed **21/21 scenarios** and produced deterministic evidence on equivalent repeats. Production activation was disabled, so the demo claims simulation-level safety evidence only.

## Audience takeaway

Reliable failover is an authority-transfer problem, not merely a heartbeat-detection problem. The evidence should prove the transfer rules and stale-writer rejection, not just show that a standby process can start.
