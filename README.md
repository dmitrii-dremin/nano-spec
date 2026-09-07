# NanoSpec

Ultra lightweight SDD framework. The minimum documentation needed to implement correctly, verify the result, and let another agent continue the work.

Current version: **0.2.0**. The philosophy and skills are experimental; their effectiveness still needs to be tested on real tasks.

## Get started

Read the [philosophy](PHILOSOPHY.md), then choose the skill you need:

| Skill | When to use it | Result |
| --- | --- | --- |
| [nanospec-explore](skills/nanospec-explore/SKILL.md) | Understand existing behavior and its history | A supported account of current behavior, historical intent, and material unknowns |
| [nanospec-shape](skills/nanospec-shape/SKILL.md) | Clarify and prepare a task | A sufficient task brief or a specific unresolved question |
| [nanospec-apply](skills/nanospec-apply/SKILL.md) | Implement or resume authorized work | Implementation, verification, and necessary record updates |
| [nanospec-check](skills/nanospec-check/SKILL.md) | Independently assess a brief or its implementation | Material gaps or a supported conclusion with verification limits |

These are independent actions. Calling every skill is unnecessary: `explore` answers research questions, `apply` includes research and verification needed for its own work, and `check` supports a separate review.

In Codex, when the task-title tool is available, Explore and Shape rename the current task to `explore <summary>` and `shape <summary>`; Apply uses `applying <change_name>`. When a prepared change requires approval, Shape follows its presentation reference to open the record in Codex Desktop or provide a link in other environments. These conveniences do not add an approval gate or prevent work when host tools are unavailable.

The change record is the only core artifact: user intent, acceptance criteria, and evidence of completion. NanoSpec has no maintained specification library or mandatory documentation index. A completed change records what was verified at completion; later work can change that behavior. Keep additional notes only when they save costly research.

Record known relationships to earlier changes inside the newer change, explaining the specific behavior modified. Explore uses targeted searches, these references, and current implementation evidence to answer a question without reading the entire history. No separate relationship registry or mandatory exploration report is needed.

## Install in Codex

With Codex CLI available, register the versioned repository marketplace and install the plugin:

```sh
codex plugin marketplace add dmitrii-dremin/nano-spec --ref v0.2.0
codex plugin add nano-spec@nano-spec
```

Then start a new task in your project. Restart Codex Desktop if the plugin is not visible. Select the installed NanoSpec skill in the skill picker, or ask the agent to use `nanospec-shape`, `nanospec-apply`, `nanospec-explore`, or `nanospec-check` explicitly. The host may display the plugin namespace alongside the skill name.

The marketplace and its plugin source both pin `v0.2.0`; installation does not follow the development branch. These commands are supported by the locally checked Codex CLI 0.153.4. See the [Codex plugin documentation](https://developers.openai.com/plugins/build/plugins) for marketplace management. Installation and live skill behavior should be confirmed in the first run; schema validation alone does not prove either.

There is no `nanospec-init` skill in 0.2.0. Begin with a real task; records are created only when needed.

The folders in `skills/` are the package sources. Each skill is self-contained. To try a skill directly without installing the plugin, give the agent its path:

```text
Read C:/Programming/nano-spec/skills/nanospec-shape/SKILL.md
and use it to prepare this task: ...
Target repository: ...
```

For implementation, provide `nanospec-apply/SKILL.md`, the task brief, and the target repository. These paths refer to this local checkout; substitute your NanoSpec path in another environment.

For another agent that supports Agent Plugins, install this repository's versioned package using that agent's installation mechanism. Alternatively, install the desired skill folders in the agent's skill directory. Keeping the sources in this repository does not install them in other projects. The skills require no NanoSpec CLI, MCP server, or runtime dependencies. Cross-agent installation has not yet been tested.

Next: [practical evaluation](TESTING.md).

## Distribution

Agent Plugins is the selected package format for NanoSpec. Keep the portable skills in `skills/` as the canonical source so packaging does not create separate workflow implementations for different agents. This choice provides a plugin installation path while preserving direct use of individual skills.

The root `plugin.json` declares the portable Agent Plugins package. `.codex-plugin/plugin.json` provides Codex compatibility metadata and points at the same skills. `.agents/plugins/marketplace.json` exposes the versioned Git source to Codex. Keep both manifest versions aligned with `VERSION` and the marketplace source aligned with the release tag. Project initialization behavior is still being designed.

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
