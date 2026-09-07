---
name: nanospec-shape
description: Prepare or clarify a NanoSpec task brief before implementation, defining behavior, constraints, and verification. A request to prepare a brief alone does not authorize implementation.
---

# NanoSpec Shape

Prepare the minimum information needed to complete the task correctly. Each piece should prevent a mistake, preserve a material decision, or help verify the result.

Use the user's requested language for communication and follow the target project's conventions for documentation, unless the user directs otherwise. Accept briefs in any natural language; English headings or keywords are not required. Preserve identifiers, paths, commands, and exact interface text unless changing them is part of the task. Do not create translations solely to use this skill.

At the start of this workflow in Codex, when `mcp__codex_app__set_thread_title` is available, rename the current task to `shape <summary>` by passing `title` and omitting `threadId`. Summarize the invocation's requested change in a few words, using the user's language and the literal prefix `shape`. Use the triggering request if no explicit argument was supplied. Rename once per invocation; if the tool is unavailable or fails, continue preparation without blocking or claiming success. Do not create a new task.

Read the request, applicable project instructions, and any existing brief. Find relevant existing documentation, code, tests, and past changes through the affected behavior; follow material dependencies without loading the whole project archive. A past completed change provides intent and evidence at completion, not a guarantee about today's implementation.

Establish the intended outcome and reason, observable acceptance criteria, material constraints, and verification method. Use examples where they resolve ambiguity. Prefer references to precise existing sources over retelling them. State concrete boundaries when their absence could expand the task.

If an unknown changes behavior, compatibility, data, or scope, ask a specific question. Continue independent investigation while waiting, but do not call the dependent part ready. Leave reversible implementation details to the implementer. Distinguish proposals and assumptions from the user's requirements.

Keep the brief where it is already maintained. If durable context is needed and no location exists, create one record at `nanospec/changes/<name>.md` in the target project. A response is enough for a small, unambiguous task in the current session; before a handoff, preserve context unavailable to the next implementer. Do not duplicate a complete issue or create empty directories.

Choose structure to suit the content. Outcome and reason, behavior/constraints, and verification usually suffice. Add a technical decision with rationale only for a material choice; add a plan for dependencies or continuation. Do not require separate proposal, design, and tasks files, a fixed scenario count, or headings for their own sake.

Keep intent and costly discoveries in the change record. Do not create a separate specification library, reconstruct historical changes, or require a documentation index. Record non-obvious findings with their reason or evidence when rediscovering them would be costly; skip code summaries and easily repeated searches. Mark planned behavior as intent and resolve conflicts with existing project requirements using the user's decisions and project rules.

When research identifies earlier changes whose behavior this task modifies, reference them in this change using an existing filename, identifier, or issue URL. Explain the exact behavior affected and preserve the scope of a partial modification. The relationship is planned until verified. Do not require exhaustive historical research, a separate relationship registry, new numbering, or edits to earlier records.

When presenting a prepared change for required approval, read and follow [Present a change](references/present-change.md). Load that reference only when needed.

Finish briefly: where the brief lives, whether it is sufficient for implementation, and any remaining material question. Do not request permission again for already authorized work; preserve required project approvals. A preparation-only request ends with preparation.
