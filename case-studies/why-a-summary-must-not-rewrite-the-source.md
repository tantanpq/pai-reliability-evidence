# Case Study Draft: The Summary Must Not Rewrite the Source

## Problem
A convenient dashboard can quietly become a second source of truth when summaries are allowed to overwrite or normalize the records they summarize. That makes corrections hard to audit and stale claims easy to preserve accidentally.

## Approach
The verified component kept the Current Picture explicitly derived. It rebuilt the view from governed reads, carried freshness and contradiction states into the display, and preserved access and provenance checks. A correction fixture replaced a source-backed decision, then proved the projection hash and displayed summary changed without writing interpretation back into the source record.

## Verified result
- lifecycle reached RESULT_VERIFIED through QA-verified retry evidence;
- focused projection and reader regressions passed;
- stale, contradicted, unauthorized, and untraceable states failed closed;
- corrections propagated through the projection hash;
- read context stayed read-only and had no canonical-promotion path.

## Why it matters
The pattern makes a compact operational picture useful without giving it authority it should not possess. Users can see a coherent view while retaining the ability to trace, correct, and challenge the underlying evidence.

## Evidence ceiling
The result proves a local governed integration seam and focused regressions. It does not prove immutable-release cutover, a production canary, or authority to mutate canonical records.
