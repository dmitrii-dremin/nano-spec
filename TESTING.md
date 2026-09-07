# Try NanoSpec on real work

Start with useful changes in the user's project. The first goal is to discover whether NanoSpec helps deliver them, not to build a benchmark suite. Behavioral evaluation is pending.

## First run

Install a fixed NanoSpec release and start a fresh task in the target project. Choose a small feature or bug with an observable outcome. No initialization skill is required.

Use Shape when the brief needs preparation; ask for approval explicitly if you want to review it before implementation. Check that Codex gives the task a short `shape ...` title and opens a local change record when presenting it for required approval. Then use Apply: the title should become `applying <change_name>`, and completion should include acceptance evidence. Use Explore for a real research question and Check when a separate review is useful; invoking all skills is not required.

Check the resulting behavior yourself. Record useful feedback in the conversation or the existing change; do not create a separate report for each run.

## Brief reflection after a change

During this evaluation, ask the agent:

```text
Reflect briefly on this change, using concrete actions and artifacts as evidence:
- What did NanoSpec help clarify or prevent?
- What reading, writing, or interaction was unnecessary?
- What information was missing or expensive to rediscover?
Propose at most one improvement, or say that no change is warranted.
Do not edit NanoSpec or produce an additional report.
```

Add the user's experience: did the result meet expectations, and which interaction felt useful or irritating? Agent reflection is a hypothesis to compare with the actual result, rework, and user feedback; it is not an objective score.

Keep the first two or three changes on the same NanoSpec version unless a clear blocker needs fixing. Note the release and any material model or environment differences. Correct demonstrated problems with small changes; do not turn each suggestion into a new universal rule.

## What to watch during normal development

- Briefs and verification preserve important requirements without generating a specification library, index, or activity diary.
- History research answers a concrete question. When a later change modifies part of an earlier one, its local reference explains what changed without rewriting the older record.
- Explore distinguishes current code from historical evidence and unimplemented proposals, including when links are missing or a change was reverted.
- Language follows the user and project. Missing host UI tools fall back gracefully; displaying a record is not approval.
- A fresh task can continue substantive work from the record without the original conversation.

## Focused comparisons only when needed

If an observed problem is recurring or its cause is uncertain, replay that small scenario with and without the relevant instruction, from the same starting state and with comparable settings. Use isolated working copies and do not leak the previous solution into the next run. Compare correctness, rework, context cost, and user intervention. A single run is evidence to investigate, not proof of superiority.

Maintain a benchmark only when it protects against a demonstrated regression and is cheaper than rediscovering it through normal work.
