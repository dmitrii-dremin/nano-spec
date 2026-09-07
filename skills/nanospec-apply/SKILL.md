---
name: nanospec-apply
description: Implement or resume an authorized NanoSpec change, verify the result, and preserve necessary context. Use for implementation requests; a separate nanospec-shape invocation is not required.
---

# NanoSpec Apply

Implement the authorized task from a sufficient brief and retain only information useful for verification and continuation.

Use the user's requested language for communication and follow the target project's conventions for documentation, unless the user directs otherwise. Accept briefs in any natural language; English headings or keywords are not required. Preserve identifiers, paths, commands, and exact interface text unless changing them is part of the task. Do not create translations solely to use this skill.

Read the request, applicable project instructions, the brief, and relevant existing documentation. Find code, tests, dependencies, and past changes through affected behavior. When resuming, inspect the actual state of work: a past completed change records earlier intent and verification, not a guarantee about the latest code. The full archive is unnecessary without a concrete reason.

Early in this workflow in Codex, once the target change is identified and `mcp__codex_app__set_thread_title` is available, rename the current task to `applying <change_name>` by passing `title` and omitting `threadId`. Preserve the existing change name or identifier; for a file record use its filename without the `.md` extension. If no name exists, derive a short name from the accepted brief without creating a record just for the title. Use the literal prefix `applying`. Rename once per invocation; if the tool is unavailable or fails, continue the work without blocking or claiming success. Do not create a new task.

Check that the outcome, behavior, constraints, and verification method are clear. Use an existing issue, document, or sufficient user message; do not require a new spec file or another skill invocation. If a gap changes correctness, data, compatibility, or scope, clarify it and pause only dependent work. Make reversible technical decisions independently.

Work within the agreed scope. Add a plan only for useful dependencies or long tasks. Record material decisions with their rationale; do not keep a step-by-step activity diary. A new requirement discovered during implementation is not automatically agreed. Preserve necessary project approvals and the user's existing authorization.

If research identifies earlier changes whose behavior this task modifies, record the references and exact affected behavior in the current change, using existing filenames, identifiers, or issue URLs. Keep those descriptions consistent with the agreed scope and actual outcome; planned links alone do not prove implementation. A partial modification does not replace the entire earlier change. Do not require exhaustive lineage research, a separate registry, or backlinks in old records.

Verify observable results against the brief, including significant errors and compatibility. Use suitable tests, commands, or manual checks; inspecting a diff may suffice for a simple edit. Perform required project checks. Record actual results, not just an intention to run checks. Do not weaken criteria to pass tests or change the task's goal to justify the implementation.

Do not create or synchronize a separate specification library. Meet the target project's existing documentation requirements without duplicating them for NanoSpec. Keep discoveries that are costly to recover in the current change with their reason or evidence. Add a shared note only for concrete reuse of information difficult to recover, using a suitable existing location; no knowledge file or documentation index is required.

If a working record exists, close it as completed only when its acceptance criteria are met and verified. Record a short outcome and evidence, identifying the checked revision or equivalent artifact when available. Keep cancellation and supersession distinct from completion. For continuation, retain completed work, remaining work, check results, and the blocker. When a handoff needs a record and no location exists, use `nanospec/changes/<name>.md` in the target project. Do not create a retrospective record solely for reporting. Completed records need no ongoing synchronization or separate archive invocation.

Report what changed and what supports it. Completion requires meeting the acceptance criteria, appropriate verification, and any project-required deliverables. If a material check is unavailable or work is blocked, identify unconfirmed and remaining items explicitly; do not mark the change completed.
