---
name: nanospec-explore
description: Investigate how an existing system capability works and why, using relevant NanoSpec changes, their relationships, current code, and evidence. Use for research and explanations before planning or implementation; do not turn exploration into a mandatory workflow stage.
---

# NanoSpec Explore

Build a supported picture of the requested capability, including current behavior, its historical intent, and material uncertainty. Return the answer in the conversation by default; exploration does not authorize implementation or a new maintained specification.

Use the user's requested language for communication and follow the target project's conventions for documentation, unless the user directs otherwise. Accept records and relationship descriptions in any natural language. Preserve identifiers, paths, commands, and exact interface text.

At the start of this workflow in Codex, when `mcp__codex_app__set_thread_title` is available, rename the current task to `explore <summary>` by passing `title` and omitting `threadId`. Summarize the invocation's research question in a few words, using the user's language and the literal prefix `explore`. Use the triggering request if no explicit argument was supplied. Rename once per invocation; if the tool is unavailable or fails, continue the research without blocking or claiming success. Do not create a new task.

Establish the capability and target state from the request. Unless specified otherwise, inspect the current checkout, including relevant local changes, and identify that scope in the answer. Do not infer deployed behavior from a repository alone. Read applicable project instructions and locate existing documentation and change records without requiring NanoSpec directories to exist.

Start with focused searches for the capability, its user-facing terms, entry points, and relevant tests. Search change titles and content for those terms and discovered identifiers; read the relevant records rather than the entire history. Expand through dependencies that could materially affect the answer.

Follow a relevant change's references to earlier changes, and search for references back to its identifier, filename, or issue URL to find subsequent modifications. Relationships live inside the newer change and explain the affected behavior; they may be ordinary prose, not standardized keywords. Missing links do not prove unchanged behavior. Use targeted code or Git history when records leave a material gap; do not require a complete lineage or a central registry.

Interpret each record by its outcome and evidence. Current statuses are `draft` (unapproved), `approved` (current brief approved by a human), `in_progress` (implementation or checks incomplete), `ready_for_acceptance` (agent work verified, human acceptance pending), `done` (verified result accepted by a human), and `canceled` (abandoned or replaced). Approved intent alone does not prove implementation; `ready_for_acceptance` can provide implementation evidence but not human acceptance. Any edit to an approved brief requires renewed approval and a return to `draft`; status/progress/evidence-only updates do not change the brief. Historical records may follow older conventions: do not infer human acceptance from legacy `ready` or completion labels or rewrite them to fit the new workflow.

A later modification can replace only part of earlier behavior; preserve unaffected criteria in the historical account. A superseding proposal alone does not prove that its replacement shipped. Resolve order or applicability through available revisions and implementation evidence, not numeric IDs or dates alone; account for relevant reverts and work on other branches. Even `done` describes an accepted historical result, not a perpetual guarantee about the target state.

Reconcile the historical account with current code, configuration, and tests. Distinguish user intent, behavior inferred from code, existing test assertions, and checks actually run. Use focused checks that do not alter product state when needed and available; do not treat passing tests as proof beyond their coverage. If code and accepted intent disagree, report the discrepancy without silently redefining either. With history-only access, label the result as a historical reconstruction and name the missing verification.

Stop when the question is answered with sufficient evidence or a concrete access gap prevents further conclusions. Do not traverse unrelated history to claim completeness. Report the relevant behavior and boundaries, the few historical decisions that explain it, supporting source locations, and material unknowns. Include the most useful starting points for follow-up work without producing a file inventory.

Do not edit code, close changes, backfill old records, or generate an index by default. If the user requests persistent research or the work needs a handoff, put only costly discoveries and relevant references in the existing task record or requested artifact. Do not create a duplicate specification library. A separate shape or apply invocation is not required to explain the findings.
