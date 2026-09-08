# Changelog

## 0.7.1 — 2026-09-09

- Fix Shape ending the turn immediately after an asynchronous question acknowledgement. Keep pending questions active with host waiting, and provide a complete text fallback when the form is unavailable instead of referring to hidden options.

## 0.7.0 — 2026-09-09

- Add structured manual/interactive review selection before shaping an existing draft. Manual review opens the record and waits; interactive review asks only material clarification questions and preserves the final approval boundary.
- With no target, Shape displays the complete default change list and offers two grounded next-change suggestions plus native manual name entry. Handle fewer candidates and unavailable question tools without guessing selections or starting implementation.

## 0.6.0 — 2026-09-08

- Add `list` to show unfinished changes and their recorded statuses with links. Exclude completed/canceled work by default, expose missing or unknown statuses, and support explicit filters without creating an index or reviewing implementation.

## 0.5.1 — 2026-09-08

- Require Shape and Apply to reconcile a brief with relevant project decisions, implementation, and related changes before requesting initial or renewed approval. Surface unresolved material conflicts and intentional departures without adding a separate stage, report, full-history review, or repeat approval of an unchanged agreed brief.

## 0.5.0 — 2026-09-08

- **Breaking:** automatically archive standard file-based changes at `done` under `nanospec/changes/archive/` with a UTC close-out timestamp prefix. Preserve links and identity without a separate archive command or duplicate record.
- Keep work awaiting acceptance active; handle repeated closure and explicit reopening, and include archived records in focused history research. Existing history is not bulk-migrated.

## 0.4.2 — 2026-09-08

- In Codex, rename Apply tasks to `implemented <change_name>` after implementation and verification, and `finished <change_name>` after human acceptance. Restore `applying <change_name>` when work resumes or the brief returns to draft.

## 0.4.1 — 2026-09-07

- Clarify the existing approval boundary: an implementation request approves what it and agreed references determine, not material product decisions the agent subsequently introduces. Routine technical choices within the agreed scope remain autonomous; task size alone adds no approval stage.
- Align Apply, Shape, and Check with this boundary and add focused evaluation scenarios.

## 0.4.0 — 2026-09-07

- **Breaking:** shorten skill names and directories to `apply`, `shape`, `explore`, and `check`; Codex plugin invocations become `nano-spec:<action>`. Update existing invocation references and direct skill paths; no duplicate compatibility skills are shipped.

- Remove the marketplace plugin-source ref and default installation pin; follow the repository default branch. Keep SemVer release identifiers and tags.

## 0.3.0 — 2026-09-07

- **Breaking:** define one change `status` with six values: `draft`, `approved`, `in_progress`, `ready_for_acceptance`, `done`, and `canceled`.
- Any edit to an approved brief, including wording-only edits, invalidates approval and returns it to `draft`. Status, progress, and evidence-only updates preserve approval when the brief remains unchanged.
- Keep useful execution plans in the change with three step markers: `[ ]` not started, `[-]` started but unfinished, and `[x]` completed. Save concise resume context during work and reconcile interrupted steps with actual implementation in a new session.
- Require human approval of the current brief before implementation and human acceptance of the verified result before `done`. Agent verification ends at `ready_for_acceptance`; acceptance fixes return to implementation, and brief revisions require renewed approval.
- Update all four skills and the evaluation plan. Pin the marketplace to v0.3.0; existing installations require an explicit update.
- Migration: do not bulk-convert legacy `ready` or completed records. For active work, establish actual approval and verification before assigning a new status; preserve unrelated metadata and historical evidence without inventing human acceptance.

## 0.2.0 — 2026-09-07

- Package the canonical skills as Agent Plugins, with Codex compatibility metadata and a Git marketplace pinned to the release tag. Add installation instructions; live installation and cross-agent behavior still need verification.
- **Breaking:** remove the maintained specification library and the requirement to synchronize changes into durable contracts. The change record is the only core artifact.
- Define completion through acceptance criteria and recorded verification evidence; distinguish completion from cancellation and supersession. Earlier evidence does not guarantee present behavior after later changes.
- Retain costly discoveries where useful, without requiring a shared knowledge file or documentation index.
- Record known behavior changes as scoped references inside the newer change, without a separate relationship registry or edits to earlier records.
- Add `nanospec-explore` to reconstruct relevant intent and behavior from linked changes and reconcile the result with the current implementation. Extend the evaluation plan for partial changes, missing links, proposals, reverts, and history-only access; behavioral runs are pending.
- Add Shape's on-demand change-presentation reference, using Codex Desktop file preview when available and links or inline text as a fallback.
- Add Codex task titles for skill invocations: `explore <summary>`, `shape <summary>`, and `applying <change_name>`. Host UI capabilities remain optional and do not introduce approval gates.
- Start evaluation through real project changes, short evidence-based agent reflection, and user feedback. Reserve focused comparisons for demonstrated problems.
- Migration: stop creating NanoSpec specification files and synchronizing completed changes. Existing project documents remain available under their own conventions; do not automatically delete them. Historical change records need no rewrite.

## 0.1.1 — 2026-09-07

- Translate all NanoSpec documentation, skill instructions, descriptions, and examples into English.
- Clarify that skills follow the user's language and the target project's documentation conventions, accept localized briefs and headings, and preserve exact identifiers and interface text.
- Extend the evaluation plan with language coverage. Behavioral evaluation is still pending.

## 0.1.0 — 2026-09-07

- First experimental NanoSpec philosophy: sufficient briefs, context selected for the task, working records, and durable commitments.
- Self-contained `nanospec-shape`, `nanospec-apply`, and `nanospec-check` skills.
- Declare the package's public contract and SemVer 2.0.0 versioning policy.
- Prepare the practical evaluation plan. Effectiveness on real tasks is not yet confirmed.
