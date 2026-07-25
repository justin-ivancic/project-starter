# Unified Systems

This is the steward-facing map of systems that are already unified, intentionally shared, or intentionally kept separate behind a stable boundary. Before implementing a feature, interface, workflow, service, or controller that overlaps one of these systems, reuse or extend the existing system first.

This file is not a replacement for code, tests, product documentation, or the Decision Map. It is a compact routing table that prevents the same behavior from being recreated in multiple places.

The map is intentionally empty when a project begins. Add a row only after a system has a real owner, active consumers, a durable reuse or separation rule, and meaningful proof.

## How To Use This

1. Identify the job of the new work.
2. Check the table for the closest existing system.
3. Inspect the named sources, nearby unchanged examples, and verification contracts before editing.
4. Reuse or extend the system when its semantics, ownership, lifecycle, and boundary match.
5. Keep a separate implementation when those properties genuinely differ, and record that boundary explicitly.
6. Verify the system-level behavior, not only the new local case.
7. Update this map in the same task when durable shared ownership or an intentional separation changes.

## Current Systems Map

| System | Use When | Source Of Truth / Owners | Reuse Rule | Proof / Contracts |
| --- | --- | --- | --- | --- |

<!--
Add one row per durable system:

| Clear system name | Jobs and surfaces that should route here | Canonical code, docs, and owner | What must be reused, and what must remain separate | Tests, checks, or observable proof |
-->

## Steward Rule

If a task touches a known system, the completion report should say which system was reused or extended.

If the closest system is intentionally not reused, the report should explain why, identify the boundary that keeps the exception safe, and name the proof that shows it did not create drift.

A duplicated system, unexplained one-off state, or unclassified shared behavior is a completion issue unless the separation is intentional and documented.
