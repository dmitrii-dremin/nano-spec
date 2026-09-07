# Present a change

Use this reference when presenting a prepared change for approval required by the user or project. Show the current record and briefly state the decision needed. Preserve existing authorization; presenting a record does not introduce an additional approval gate or count as approval.

## Codex Desktop

When `mcp__codex_app__open_in_codex` is available and the change has a local file, resolve its absolute path and call the tool with `target: { type: "file", path: absolutePath }`. Omit `threadId` to open it in the current task. Do this before requesting the required approval, so the user can review the actual record.

Include a clickable file link in the response. If opening is queued, unavailable, or fails, do not claim that the document is already visible; the link remains the fallback. Do not repeatedly retry a UI operation or block delivery on it.

## Other environments and record types

If a documented host preview tool is available, use it to present the record. Otherwise, provide a clickable file or issue link and a concise summary. Do not invent platform commands or install an integration just to open a document. If the brief exists only in the conversation, present it there without creating a file solely for the preview.

When approval is required, wait for the user's decision before dependent implementation. Do not infer acceptance from opening the file, a successful tool call, or elapsed time.
