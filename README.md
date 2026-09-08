# NanoSpec

Ultra lightweight SDD framework. The minimum documentation needed to implement correctly, verify the result, and let another agent continue the work.

Current version: **0.7.0**. The philosophy and skills are experimental; their effectiveness still needs to be tested on real tasks.

## Get started

Read the [philosophy](PHILOSOPHY.md), then choose the skill you need:

| Skill | When to use it | Result |
| --- | --- | --- |
| [list](skills/list/SKILL.md) | See unfinished changes and their recorded statuses | A concise linked list; no review or implementation |
| [explore](skills/explore/SKILL.md) | Understand existing behavior and its history | A supported account of current behavior, historical intent, and material unknowns |
| [shape](skills/shape/SKILL.md) | Clarify and prepare a task | A draft for human approval or a specific unresolved question |
| [apply](skills/apply/SKILL.md) | Implement or resume an approved task | Verified implementation awaiting human acceptance; closure after acceptance |
| [check](skills/check/SKILL.md) | Independently assess a brief or its implementation | Material gaps or a supported conclusion with verification limits |

List is available as `nano-spec:list`. It shows active records with their statuses, hides `done` and `canceled` by default, and flags unknown or missing status values without rewriting them.

In Shape, invoking `nano-spec:shape` without a target first displays the full default List result, then asks which change to discuss through the host's question tool: two relevant candidates plus manual name entry. Selecting an existing `draft` asks for manual or interactive review. Manual review opens the record and waits for feedback; interactive review asks focused questions to resolve ambiguities. Selecting a change or review mode does not approve the brief or start implementation.

These are independent actions. Calling every skill is unnecessary: `explore` answers research questions, `apply` includes research and verification needed for its own work, and `check` supports a separate review.

In Codex, when the task-title tool is available, Explore and Shape rename the current task to `explore <summary>` and `shape <summary>`; Apply uses `applying <change_name>`, changes it to `implemented <change_name>` when implementation and checks are complete, and to `finished <change_name>` after human acceptance. Resuming work restores `applying`. When a prepared change requires approval, Shape follows its presentation reference to open the record in Codex Desktop or provide a link in other environments. These conveniences do not add an approval gate or prevent work when host tools are unavailable.

The change record is the only core artifact: user intent, acceptance criteria, status, and evidence of completion. File-based changes use one YAML `status`: `draft`, `approved`, `in_progress`, `ready_for_acceptance`, `done`, or `canceled`. Any edit to an approved brief returns it to `draft` for renewed human approval; progress and evidence-only updates do not. Agent verification reaches `ready_for_acceptance`; human acceptance is required for `done`. See the [status rules](PHILOSOPHY.md#change-status).

After `done`, standard file-based changes automatically move to `nanospec/changes/archive/<timestamp>_<name>.md`. The UTC prefix uses `YYYY-MM-DDTHH-mm-ss.SSSZ` and sorts by close-out time; work awaiting acceptance stays active. Archiving is part of Apply, with no separate command.

NanoSpec has no maintained specification library or mandatory documentation index. A completed change records what was verified and accepted at that point; later work can change that behavior. Keep additional notes only when they save costly research.

Record known relationships to earlier changes inside the newer change, explaining the specific behavior modified. Explore uses targeted searches, these references, and current implementation evidence to answer a question without reading the entire history. No separate relationship registry or mandatory exploration report is needed.

## Install in Codex

With Codex CLI available, register the repository marketplace and install the plugin:

```sh
codex plugin marketplace add dmitrii-dremin/nano-spec
codex plugin add nano-spec@nano-spec
```

Then start a new task in your project. Restart Codex Desktop if the plugin is not visible. Select the installed NanoSpec skill in the skill picker, or ask the agent to use `nano-spec:shape`, `nano-spec:apply`, `nano-spec:explore`, `nano-spec:check`, or `nano-spec:list` explicitly. Versions through 0.3.0 used `nano-spec:nanospec-<action>`; update existing invocations to the shorter names.

The marketplace and plugin source follow the repository's default branch (`master`), without a pinned Git ref. Refresh the catalog and reinstall to pick up updates; SemVer versions and release tags identify releases without locking installation to them. These commands are supported by the locally checked Codex CLI 0.153.4. See the [Codex plugin documentation](https://developers.openai.com/plugins/build/plugins) for marketplace management. Installation and live skill behavior should be confirmed in the first run; schema validation alone does not prove either.

To update a Git marketplace that tracks the repository's default branch, refresh its catalog and reinstall the plugin:

```sh
codex plugin marketplace upgrade nano-spec
codex plugin add nano-spec@nano-spec
```

If an earlier installation used `--ref`, remove that old pin once by re-registering the marketplace without it, then reinstall:

```sh
codex plugin marketplace remove nano-spec
codex plugin marketplace add dmitrii-dremin/nano-spec
codex plugin add nano-spec@nano-spec
```

Start a new task after updating so it loads the new skill instructions.

There is no `init` skill in 0.7.0. Begin with a real task; records are created only when needed.

The folders in `skills/` are the package sources. Each skill is self-contained. To try a skill directly without installing the plugin, give the agent its path:

```text
Read C:/Programming/nano-spec/skills/shape/SKILL.md
and use it to prepare this task: ...
Target repository: ...
```

For implementation, provide `skills/apply/SKILL.md`, the task brief, and the target repository. These paths refer to this local checkout; substitute your NanoSpec path in another environment.

For another agent that supports Agent Plugins, install this repository's package using that agent's installation mechanism. Alternatively, install the desired skill folders in the agent's skill directory. Keeping the sources in this repository does not install them in other projects. The skills require no NanoSpec CLI, MCP server, or runtime dependencies. Cross-agent installation has not yet been tested.

Next: [practical evaluation](TESTING.md).

## Distribution

Agent Plugins is the selected package format for NanoSpec. Keep the portable skills in `skills/` as the canonical source so packaging does not create separate workflow implementations for different agents. This choice provides a plugin installation path while preserving direct use of individual skills.

The root `plugin.json` declares the portable Agent Plugins package. `.codex-plugin/plugin.json` provides Codex compatibility metadata and points at the same skills. `.agents/plugins/marketplace.json` exposes the repository Git source to Codex without a `ref`. Keep both manifest versions aligned with `VERSION`; keep installation commands and the catalog free of version pins unless the user explicitly requests a fixed version. Project initialization behavior is still being designed.

## Language

NanoSpec's own documentation, skill instructions, descriptions, and examples are maintained in English. The skills support tasks and project artifacts in any natural language: follow the user's requested language and the target project's documentation conventions. English instructions do not require English output. Preserve existing identifiers, commands, paths, and exact interface text unless changing them is part of the task.

## Versions and compatibility

Versioning follows [Semantic Versioning 2.0.0](https://semver.org/spec/v2.0.0.html). `VERSION` identifies the whole package: philosophy and skills are released together.

NanoSpec's public contract consists of skill names, their purposes and action boundaries, the meaning of a sufficient brief and completed work, and the philosophy's rules for selecting context and retaining knowledge. Markdown wording and optional section titles are not a machine API. This version has no record parser.

The `0.y.z` series is experimental. Our convention before 1.0.0:

- `PATCH`: fixes and clarifications that preserve the contract.
- `MINOR`: new capabilities or contract changes; document incompatibilities and migration steps in the changelog.
- `1.0.0`: establishes a stable contract. After that, incompatible changes increment `MAJOR`, compatible capabilities increment `MINOR`, and compatible fixes increment `PATCH`.

Published versions are immutable: a correction receives a new version. Incrementing a higher component resets lower components to zero. Individual project records do not need their own copy of the package version.

Release history: [CHANGELOG.md](CHANGELOG.md).
