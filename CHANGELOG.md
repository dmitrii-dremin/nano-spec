# Changelog

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
