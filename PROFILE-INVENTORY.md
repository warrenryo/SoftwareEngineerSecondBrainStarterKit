# Current Codex profile inventory

**Checked:** 2026-11-23. This is a point-in-time inventory of the current local Codex setup, not a portable machine configuration. Names and counts were checked from the Codex CLI, `~/.codex/config.toml` key names, the installed skill and agent directories, plugin cache metadata, and the existing vault's profile snapshot. Secret values and machine-specific command paths are intentionally omitted.

## Versions and verification notes

- Codex CLI: `0.169.1` (`codex --version`).
- GSD Core: `1.16.0` (`~/.codex/gsd-core/VERSION`).
- ECC plugin cache: `2.2.3`; enabled selector is `ecc@ecc`.
- Graphify portability manifest: `graphifyy` `0.9.106`. The `graphify` command was not found on the current shell `PATH`, and the existing vault's Graphify Python marker points to a Windows interpreter unavailable on this host. Treat the package version as a saved pin; verify/install the CLI before building a graph here.
- The existing vault's `Codex Setup/profile-manifest.json` was snapshotted on 2026-11-12. The live enabled plugin selectors below were checked on 2026-11-23 and should take precedence over that older list.

## Skills

### Shared user skills (`~/.agents/skills`): 73

These 72 GSD Core skills and one additional skill are currently present:

`gsd-add-tests`, `gsd-ai-integration-phase`, `gsd-audit-fix`, `gsd-audit-milestone`, `gsd-audit-uat`, `gsd-autonomous`, `gsd-capture`, `gsd-cleanup`, `gsd-code-review`, `gsd-complete-milestone`, `gsd-config`, `gsd-debug`, `gsd-discuss-phase`, `gsd-docs-update`, `gsd-eval-review`, `gsd-execute-phase`, `gsd-explore`, `gsd-extract-learnings`, `gsd-fast`, `gsd-forensics`, `gsd-graphify`, `gsd-health`, `gsd-help`, `gsd-import`, `gsd-inbox`, `gsd-ingest-docs`, `gsd-manager`, `gsd-map-codebase`, `gsd-mempalace-capture`, `gsd-mempalace-recall`, `gsd-milestone-summary`, `gsd-mvp-phase`, `gsd-new-milestone`, `gsd-new-project`, `gsd-next`, `gsd-ns-context`, `gsd-ns-ideate`, `gsd-ns-manage`, `gsd-ns-project`, `gsd-ns-review`, `gsd-ns-workflow`, `gsd-onboard`, `gsd-pause-work`, `gsd-phase`, `gsd-plan-phase`, `gsd-plan-review-convergence`, `gsd-pr-branch`, `gsd-profile-user`, `gsd-progress`, `gsd-quick`, `gsd-quick-batch`, `gsd-resume-work`, `gsd-review`, `gsd-review-backlog`, `gsd-secure-phase`, `gsd-settings`, `gsd-ship`, `gsd-sketch`, `gsd-spec-phase`, `gsd-spike`, `gsd-stats`, `gsd-surface`, `gsd-thread`, `gsd-ui-phase`, `gsd-ui-review`, `gsd-ultraplan-phase`, `gsd-undo`, `gsd-update`, `gsd-validate-phase`, `gsd-verify-work`, `gsd-workspace`, `gsd-workstreams`, and `optimizing-ef-core-queries`.

Install GSD Core from [open-gsd/gsd-core](https://github.com/open-gsd/gsd-core) using the pinned command in [[AGENTS]]. `optimizing-ef-core-queries` has no verified public source URL; its preserved user copy is in the sibling vault's `Codex Setup/Profile/skills/agents-home/` folder when available.

### Codex user skills (`~/.codex/skills`): 6

`check-repo`, `developer-task-creator`, `git-log`, `pull-request-summary`, `repo-period-summary`, and `solution-summary`.

These are user-specific skill copies; no public GitHub origin is recorded. Their preserved copies are in the sibling vault's `Codex Setup/Profile/skills/codex-home/` folder when available.

### Codex system skills: 5

`imagegen`, `openai-docs`, `review-agent`, `skill-creator`, and `skill-installer`. These ship with the current Codex installation.

### Project skill in this starter kit

`graphify` is bundled under `.agents/skills/graphify/`. Its source is the [Graphify repository](https://github.com/Graphify-Labs/graphify); Graphify v0.9.106 is the saved pin in the existing vault's portable manifest.

The enabled ECC plugin also supplies skills from [affaan-m/ECC](https://github.com/affaan-m/ECC). They are loaded through the plugin cache, not copied into this inventory.

## Custom Codex agents

There are **35 unique GSD agent definitions** in the current global profile (99 files across full, compact, and TOML forms):

`gsd-advisor-researcher`, `gsd-ai-researcher`, `gsd-assumptions-analyzer`, `gsd-code-fixer`, `gsd-code-reviewer`, `gsd-codebase-mapper`, `gsd-debug-session-manager`, `gsd-debugger`, `gsd-doc-classifier`, `gsd-doc-synthesizer`, `gsd-doc-verifier`, `gsd-doc-writer`, `gsd-dom-verifier`, `gsd-domain-researcher`, `gsd-eval-auditor`, `gsd-eval-planner`, `gsd-executor`, `gsd-framework-selector`, `gsd-integration-checker`, `gsd-intel-updater`, `gsd-mempalace-curator`, `gsd-nyquist-auditor`, `gsd-pattern-mapper`, `gsd-phase-researcher`, `gsd-plan-checker`, `gsd-planner`, `gsd-project-researcher`, `gsd-research-synthesizer`, `gsd-roadmapper`, `gsd-security-auditor`, `gsd-ui-auditor`, `gsd-ui-checker`, `gsd-ui-researcher`, `gsd-user-profiler`, and `gsd-verifier`.

These are installed by GSD Core. The current profile's user-specific agent copies are preserved under the sibling vault's `Codex Setup/Profile/agents/` folder when available. The current agent definitions are also available through the [GSD Core repository](https://github.com/open-gsd/gsd-core).

## GSD slash commands

There are **72** commands under the current global GSD runtime:

`/add-tests`, `/ai-integration-phase`, `/audit-fix`, `/audit-milestone`, `/audit-uat`, `/autonomous`, `/capture`, `/cleanup`, `/code-review`, `/complete-milestone`, `/config`, `/debug`, `/discuss-phase`, `/docs-update`, `/eval-review`, `/execute-phase`, `/explore`, `/extract-learnings`, `/fast`, `/forensics`, `/graphify`, `/health`, `/help`, `/import`, `/inbox`, `/ingest-docs`, `/manager`, `/map-codebase`, `/mempalace-capture`, `/mempalace-recall`, `/milestone-summary`, `/mvp-phase`, `/new-milestone`, `/new-project`, `/next`, `/ns-context`, `/ns-ideate`, `/ns-manage`, `/ns-project`, `/ns-review`, `/ns-workflow`, `/onboard`, `/pause-work`, `/phase`, `/plan-phase`, `/plan-review-convergence`, `/pr-branch`, `/profile-user`, `/progress`, `/quick-batch`, `/quick`, `/resume-work`, `/review-backlog`, `/review`, `/secure-phase`, `/settings`, `/ship`, `/sketch`, `/spec-phase`, `/spike`, `/stats`, `/surface`, `/thread`, `/ui-phase`, `/ui-review`, `/ultraplan-phase`, `/undo`, `/update`, `/validate-phase`, `/verify-work`, `/workspace`, and `/workstreams`.

## Enabled plugins

The live user configuration has these 10 enabled selectors:

- `browser@openai-bundled`
- `codex-app-tools@openai-bundled`
- `documents@openai-primary-runtime`
- `ecc@ecc`
- `pdf@openai-primary-runtime`
- `presentations@openai-primary-runtime`
- `spreadsheets@openai-primary-runtime`
- `template-creator@openai-primary-runtime`
- `unified-computer-use@openai-bundled`
- `visualize@openai-bundled`

ECC's plugin cache reports version 2.2.3. The other listed selectors are provided by the Codex bundled or primary runtime catalogs and can change with the host app. Install/enable third-party plugins from a trusted marketplace; do not copy a plugin cache as a setup method.

## MCP servers

`codex mcp list` reported:

- `chrome-devtools` — provided by ECC's plugin configuration.
- `codex_app` — Codex app runtime.
- `cua_repl` — computer-use runtime.
- `node_repl` — the only explicit stdio MCP server in the local user configuration.

Do not copy the local `node_repl` executable path or any MCP environment values. Re-check with `codex mcp list` on the target machine. The [OpenAI Docs MCP](https://developers.openai.com/learn/docs-mcp) is a public, read-only option, but it is not in the current explicit MCP configuration.

## Obsidian plugins

The existing vault's `.obsidian/` folder has core plugin settings but no community plugin registry file was found. This starter kit requires no Obsidian community plugins; use core Templates and standard Markdown features.
