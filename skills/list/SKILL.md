---
name: list
description: Show NanoSpec changes and their recorded statuses. Use to list unfinished work or find a change to continue, without reviewing or implementing it.
---

# NanoSpec List

Show a concise list in the conversation, using the user's language and preserving change names and status tokens.

Read applicable project instructions and identify the target project from the request or current workspace. Use `nanospec/changes/` by default, or the project's explicitly configured change location. Enumerate active Markdown change records, excluding `archive/` unless the user requests archived or all changes. Do not search unrelated repositories or reconstruct changes from code or Git history. If the project explicitly keeps changes in an accessible issue source, list that source without creating local copies; disclose unavailable sources.

Read only each record's YAML frontmatter and title initially. Use its top-level `status`, not a status mentioned in an example or quotation. Read additional text only to resolve ambiguous metadata or an explicit user filter. Do not load full briefs, implementation files, test evidence, or related history just to list work.

By default include `draft`, `approved`, `in_progress`, and `ready_for_acceptance`; exclude `done` and `canceled`. Apply explicit user filters instead when supplied. For missing, malformed, or unknown statuses, include the record with a short annotation such as `missing status` or `unknown: ready`; never silently classify it as approved, completed, or absent. Use a legacy mapping only when the project explicitly defines it, and preserve the recorded value in the output. If a record cannot be read, show its path and the access limitation instead of dropping it silently.

Return a compact table with `Change` and `Status`, sorted by change name. Link the change name to its file using an absolute path, or to its issue URL. Add its title only if it materially clarifies the name. State the searched location and number of matching records. If no matches exist, say so; distinguish an absent changes directory from an unreadable source. Do not create a directory or an index. For a large result, avoid silent truncation: show all matches or identify the displayed portion and remaining count.

This is a view of recorded state, not verification that the implementation or approval matches it. Do not change statuses, rename or archive files, start implementation, rename the current Codex task, or request approval merely to show the list.
