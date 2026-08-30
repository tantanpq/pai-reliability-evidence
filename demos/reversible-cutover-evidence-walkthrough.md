# Demo Outline: From Candidate to Verified Cutover

A short evidence-first walkthrough suitable for a technical portfolio demo.

## 1. Start with the claim boundary

Show the candidate as “QA-passed,” not “live-proven.” Explain that build/test evidence and live-effect evidence are different.

## 2. Show the rollback contract

Explain that only the affected component needs a preserved known-good rollback state. Avoid the comforting but dangerous ritual of restoring an unrelated whole-system snapshot.

## 3. Show byte readback

Demonstrate the principle: compare the promoted runtime bytes with the frozen candidate. A successful API response is not equivalent to a verified deployment.

## 4. Show bounded restart and canary

Restart only the affected service, verify health, then run a canary designed to detect unintended execution or routing.

## 5. Show terminal and post-terminal truth

Record terminal completion, then check the system again. The useful proof is that ownership, active-work state, and basic execution readiness remain coherent after the task is terminal.

## Demo claim

“This run demonstrated a reversible, evidence-backed cutover sequence with independent QA, exact byte readback, bounded restart, canary verification, terminal completion, and post-terminal readback.”

Do not expand that sentence into claims of certification, zero defects, or universal production readiness.
