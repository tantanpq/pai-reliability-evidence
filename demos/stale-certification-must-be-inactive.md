# Demo Outline: A Stale Certification Must Become Inactive

1. Create one benign candidate with a fixed version, test fixture, rollback note, target environment, and narrow scope.
2. Have a separate synthetic evaluator certify the exact frozen candidate.
3. Replay the same candidate as its own evaluator and show self-certification fail.
4. Remove the rollback or required fixture evidence and show certification fail.
5. Advance the clock beyond the certification expiry and show the old certification become inactive.
6. Change the runtime release while keeping the candidate unchanged and show the old certification remain inactive.
7. Repeat with environment and scope drift and confirm the same fail-closed behavior.
8. Add explicit counterevidence and show it blocks active selection.
9. End by showing that a valid certification records evidence but grants no repair or deployment authority.

Public-demo hygiene:
- synthetic fixtures only;
- no credentials, private hosts, internal paths, or production logs;
- no proprietary source code;
- no real customer or personal data;
- no exploit instructions;
- no claim beyond the verified component scope.
