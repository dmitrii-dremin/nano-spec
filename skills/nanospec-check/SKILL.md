---
name: nanospec-check
description: Assess whether a NanoSpec brief is sufficient or its implementation meets the requirements. Use for separate reviews and readiness checks; report findings without changing code or requirements by default.
---

# NanoSpec Check

Assess whether the brief enables correct work or whether the result satisfies it. Check meaning and evidence; file, heading, and checkbox counts are not criteria.

Use the user's requested language for communication and follow the target project's conventions for documentation, unless the user directs otherwise. Accept briefs in any natural language; English headings or keywords are not required. Preserve identifiers, paths, commands, and exact interface text unless changing them is part of the task. Do not require translations solely for this review.

Infer the review target from the request: brief, implementation, or both. Read applicable project instructions, the task, and relevant existing documentation and past changes. For implementation, inspect the actual diff, affected code, and checks. Expand context through material dependencies; do not read the whole archive by default.

When reviewing a brief, determine:

- Do the text and accessible references explain the outcome and reason, behavior, material constraints, and verification method?
- Could an unknown or contradiction lead the implementer to a materially different result?
- Could duplication or stale instructions cause an error? A specification library, shared knowledge file, or documentation index is not required.

Where a change references earlier behavior, check that it explains the affected part and does not imply that unrelated criteria were replaced. Check material references against available evidence. Do not demand a complete relationship graph or flag absent links alone as a defect; planned relationships do not prove completed implementation.

When reviewing implementation, match acceptance criteria to observable results. Run appropriate checks in the authorized environment when needed. Distinguish checks performed now, previous reports, and conclusions from reading code. Account for significant edge cases and existing project requirements. For a change marked completed, check its recorded outcome and evidence; distinguish cancellation or supersession. Earlier completion proves only what was verified at that point; evaluate present behavior against the current implementation. Do not require synchronization into a separate specification library or updates to historical records merely because later changes exist.

Do not edit code, the brief, or completion markers by default. If the user also authorized fixes, correct findings within that scope and recheck affected results. Do not resolve a mismatch by weakening a requirement without an agreed task change.

Give a short conclusion: ready for implementation, or implementation confirmed within the reviewed scope. For each material finding, provide the location, concrete problem, consequence, and necessary clarification or correction. Identify failed or unavailable checks. If there are no findings, say so along with the review scope; no discovered problems does not prove what was not checked.
