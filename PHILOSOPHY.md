# NanoSpec philosophy

NanoSpec helps an agent obtain enough context to complete a task correctly and leave the work understandable to the next implementer.

**Minimum clutter and unnecessary rituals; maximum useful information. Every piece of documentation should prevent a concrete mistake, preserve a material decision, or help verify the result.**

## A sufficient brief

A brief is sufficient when it and its accessible references explain the intended outcome and reason, verifiable behavior, material constraints, and a way to verify completion. No unresolved question should determine whether the current step is correct.

These are content requirements, not mandatory headings. There is no minimum number of lines, scenarios, documents, or stages. A short condition with a precise example can replace a page of description. A complex migration may need more detail.

Record what cannot reliably be recovered from code: intent, product commitments, constraints, and the reasons behind non-obvious decisions. Reference existing interfaces and tests. Code shows the current implementation; it does not by itself prove that it matches the user's intent.

Clarify an unknown when its answer changes behavior, compatibility, data, or scope. Agents can make local, reversible technical decisions independently. Distinguish assumptions from agreed requirements; writing down a risky assumption does not make it acceptable.

NanoSpec's own documentation and skill sources use English. In a target project, follow the user's requested language and established documentation conventions. Briefs, headings, and explanations can use any natural language; English keywords are not required. Preserve identifiers and exact interface text unless the task calls for changing them. Do not create translated copies just to use NanoSpec.

## Documents appear when needed

The change record is NanoSpec's only core artifact. It holds user intent, acceptance criteria, status, and evidence of completion. If an accessible issue or another durable source already describes the task completely, use it. A user message can be enough for a small, unambiguous task within one session. Do not rewrite a brief just to satisfy a format.

Before a handoff, preserve information the next implementer would otherwise lose. If no suitable location exists, use `nanospec/changes/<name>.md`. Create the directory only with its first useful record; continue the existing record for the same task.

Add a technical decision and its rationale when it shapes the approach or avoids repeated investigation. A plan helps with dependencies, long tasks, or handoffs. Separate files are justified by independent use or volume; there is no mandatory proposal/design/tasks bundle.

When work needs a plan or may span sessions, keep a short execution list in the same change record: `[ ]` means not started, `[-]` means started but unfinished, and `[x]` means completed. Maintaining these markers is mandatory whenever the list exists: save `[-]` before the first action on a step; save `[x]` immediately after completing it and its required checks, before starting another step. Do not defer transitions to the end of the session or keep them only in chat or a host's plan UI. If a completed step needs further work, save `[-]` before resuming it. An interrupted or blocked step stays `[-]`; this marker does not imply an agent is still running. Completed steps do not replace human acceptance of the whole change. These are literal text markers, independent of how a Markdown renderer displays them.

Keep a concise resume note beside the list when the unfinished step needs context: where work stopped, relevant files, checks already run, and the next action or blocker. Update it after each meaningful intermediate result or costly discovery, before switching away from unfinished work, and before a planned handoff; replace stale notes instead of accumulating a diary. A new session starts from unfinished steps and reconciles the record with the actual code, diff, and relevant checks, correcting stale markers and notes before continuing. An abrupt interruption may leave unrecorded work; the list guides recovery rather than proving the exact state. Progress-only updates do not invalidate approval.

An example brief for a small task:

```md
---
status: draft
---

# Cancel an export

Why: let the user stop a long export.

Behavior:
- Cancellation stops producing new rows and closes the output stream.
- Delete the incomplete temporary file; preserve a completed export.
- Repeated cancellation is safe.

Verification: cancel during writing, cancel repeatedly, and cancel after
successful completion; check that writing stops and files are handled correctly.
```

This example is not a mandatory template. Resolve material ambiguity in the specific project before dependent implementation.

## Change status

For a file-based change, keep one `status` field in YAML frontmatter and preserve unrelated existing metadata. No `slug`, dependency array, approval ledger, or separate status file is required. For an issue or conversation-based brief, express the same state in its existing location without creating a duplicate record. Status values are fixed English tokens; the surrounding content follows the project's language.

| Status | Meaning |
| --- | --- |
| `draft` | The brief is being prepared or revised and its current contents have not been approved by a human. |
| `approved` | A human approved the current brief; implementation has not started or is awaiting resumption after renewed approval. |
| `in_progress` | Implementation or agent verification is underway. A blocked task stays here with a short explanation. |
| `ready_for_acceptance` | Implementation and required agent checks are complete; human acceptance of this result is pending. |
| `done` | A human accepted the verified result against the current approved brief. |
| `canceled` | The change was abandoned or replaced without being completed; record the reason or replacement when useful. |

Any edit to the approved brief invalidates its approval: return to `draft`, show what changed, and obtain renewed human approval before implementing the revised brief. This applies even to wording-only edits and also when implementation has already started or is awaiting acceptance. Updating status, progress, or verification evidence alone does not revise the brief; changing agreed behavior, constraints, acceptance criteria, or approach does. Keep existing implementation work when approval is invalidated, but do not continue dependent work under stale approval.

Use the human's explicit decision about the current brief to enter `approved`; an earlier decision still applies only while that brief is unchanged. An explicit request to implement that same brief can supply approval. Editing the brief is not itself approval. A generic earlier authorization does not approve subsequent revisions. Do not require a separate command or file write for every intermediate transition.

After agent verification, enter `ready_for_acceptance`, present the result and evidence, and request human acceptance. Passing tests, a favorable agent review, or silence cannot set `done`. If the human requests implementation fixes under the same brief, return to `in_progress`, then repeat verification and acceptance. If the brief changes, return to `draft` instead. A canceled change is not evidence of completed functionality. Preserve old completed records as history; later changes do not trigger retrospective reapproval.

## Context and memory

Start with the current brief and applicable project instructions. Find relevant existing documentation, code, tests, and past changes through affected behavior, modules, and links; expand reading along discovered dependencies. Keeping context small does not justify missing an important constraint. Do not load the entire change history by default.

NanoSpec does not maintain a separate specification library or synchronize completed changes into a description of the current product. Research current behavior from the implementation and appropriate checks. Use past changes to recover intent and earlier evidence; later work may have changed the behavior. Existing project documentation and its own maintenance requirements still apply, without creating a NanoSpec copy.

When research identifies an earlier change whose behavior the current change modifies, record that relationship inside the newer change. Reference the existing filename, identifier, or issue URL and state exactly what behavior changes; a partial modification does not replace the entire earlier change. For example: `Changes CHANGE-7000: failed exports now retry automatically up to three times; manual retry remains available.` The relationship describes intent until implementation is verified.

Do not require a complete lineage, allocate IDs through a new registry, maintain a separate relationship list, or add backlinks to old records. Find later changes by searching references to the earlier record, supplemented by focused searches of behavior and code. Missing relationships are not evidence that behavior is unchanged. Explore follows relevant links and reconciles historical evidence with the target implementation; it does not read all changes or produce a maintained system description.

Keep costly discoveries in the change that needed them: externally imposed constraints, reasons for surprising decisions, or environment facts that code does not reveal. Include the reason or evidence and enough scope to judge relevance. A separate shared note is justified only when reuse has concrete value and the information is difficult to recover; use a suitable existing location. There is no required knowledge file or documentation index. A directory listing, code summary, or easily repeated search does not justify another maintained document.

For unfinished work, retain only what helps continuation: what is done, what was verified, what remains, and the blocking question. At `ready_for_acceptance`, record a short outcome and evidence, including the checked revision or equivalent artifact identity when available. At `done`, retain a brief note of the human's acceptance of that result. Completion is evidence of accepted behavior at that point, not a perpetual guarantee about the latest code. Completed records need no ongoing synchronization or separate archiving ceremony.

## Execution and completion

Preparing a brief does not authorize implementation. Human approval of the current brief authorizes work within that scope, subject to the target project's permissions. A revised brief requires renewed approval, and the implemented result requires separate human acceptance. Preserve any additional project-required approvals.

A change is `done` when its acceptance criteria are met, appropriate checks and project-required deliverables are complete, and a human has accepted that result. Do not rewrite requirements to fit the code. If required verification is unavailable, state exactly what remains unconfirmed and keep `in_progress`; a status label without evidence does not prove readiness.

Evaluate the framework by result correctness, material guesses and rework, handoff success, and context cost. Add a rule in response to an observed, recurring failure when a simpler clarification cannot solve it.
