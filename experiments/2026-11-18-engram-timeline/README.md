# Complete Engram GPU wait records

Base deployment c0e4124f76f627ed973e788fc0517d1eb0eb1a56, vLLM patch head c0097f3ece9bdbd1da856c4466d5fd37856e9e57. One change: debug timeline completeness. The previous single-slot sampling lost steps under early prefetch. A per-sequence GPU ring retains 64-bit waits until export, which joins the same step and defers unfinished records. Overflow raises. Model arithmetic and row scheduling are preserved.

Acceptance requires delayed/early/burst/final-step regression, ring-slot wrap and 64-bit duration export, live four-rank health, and exact full coverage of every prefill step in repeated uncached 32768-token requests. Measurements retain fresh cache salts, traffic counters and all raw records. Storage-caused TTFT attribution must distinguish observed local GPU waits, cross-rank communication propagation, and any unmatched counterfactual.
