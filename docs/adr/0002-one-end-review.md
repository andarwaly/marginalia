# One end review replaces per-statement confirmation in ingest

Status: accepted

`ingest` asked "what's missing or wrong?" after every statement and rejected a bare "yes". In the first test that became the main activity of the session, and the stock replies ("Fixed.", "Noted.") kept it from feeling two-way. The agent now tracks points silently, checks quotes itself, raises a mismatch as an ordinary remark, and runs one End review at the end.

Consequence: quote fidelity rests on the agent's silent check plus the End review, not on a gate per statement. `ideate` keeps its Statement gate.
