# SoftwareEngineerBrain agent guide

This folder is the root of a separate, Obsidian-first engineering knowledge vault. Keep it portable: do not put credentials, API keys, private MCP configuration, local machine paths, session databases, or unrelated project notes in the starter kit.

## Start with the right context

1. Read this file and [[CONTEXT]].
2. For engineering work, find the matching folder under `10 - Projects/` and read its `Hub.md` first. Follow only the linked Knowledge notes, Areas, Resources, or Inbox captures needed for the task.
3. If an active project has no folder, create one from [[Templates/Project]] and record its repository, tracker, source of truth, status, next action, and updated date.
4. Treat the repository and issue tracker as authoritative for live code and execution status. Use this vault for durable context, concise routing, and decisions that belong outside the code history.

## Skill-first workflow

Before handling each request, check the user's Codex skill folders (`$CODEX_HOME/skills` or `~/.codex/skills`, plus `~/.agents/skills`), this workspace's `.agents/skills/`, and relevant skills supplied by installed plugins. Read the best match before proceeding. Do not say a skill was used unless its instructions were read and applied.

Use the matching task skill when one is available. The current profile specifically includes `solution-summary`, `repo-period-summary`, `developer-task-creator`, `pull-request-summary`, and `git-log` for those kinds of requests. See [[PROFILE-INVENTORY]] for the dated list and install sources.

## Engineering rules

- Before editing a repository, read its `AGENTS.md` or `CLAUDE.md` and the matching project Hub in this vault.
- Reuse the repository's shared UI components for text inputs, textareas, selects, date pickers, uploads, editors, buttons, dialogs, labels, and validation when they meet the requirement.
- Format frontend code with the repository's Prettier configuration. Keep components, handlers, conditionals, object literals, and JSX readable.
- Ground code plans in inspected files and symbols. Trace the relevant UI/API/controller/service/data layers where they apply. For multi-file plans, use ordered steps with exact files and symbols, verified insertion points, how the layers connect, and a short pseudocode sketch when it clarifies the change. Do not invent paths, line numbers, or architecture.
- When a user choice is required, ask and wait before doing dependent work. Continue independent work while waiting.
- For solution recaps and developer task writeups, include verified client-facing navigation and tester steps for affected workflows, with roles, prerequisites, and observable pass criteria when known. For UI changes in PR summaries, include the same navigation when it helps reviewers. For backend-only work, give the verified API or operational path; mark unavailable navigation as unverified instead of guessing.
- Create or update an ADR through the repository's existing process for a significant technical decision. Update a changelog only if the repository already maintains one. Do not create a new changelog unless the user asks.
- For personal topics that are not represented in this engineering vault, ask for the relevant source instead of assuming this vault contains it.

## Keep project context current

At the end of every coding session, including sessions where code changes are made only in another repository:

1. Update the project Hub's `status`, `next`, and `updated` fields when they change.
2. Create one dated session note directly inside the project folder from [[Templates/Coding Session]]. Include Focus, What was built, Mistakes, Decisions, Wins, context used, files changed, verification (or say not run), and next action.
3. Add a short dated link to that note in the root [[log]].
4. Promote durable findings to one canonical Knowledge note and link it from the project's Knowledge map or domain MOC. Keep detailed code history in the repository or tracker.
5. Do not paste full transcripts or diffs into a session note or `log.md`.

## Make this vault global for Codex

When adopting this starter kit as the active engineering vault, update Codex's user-wide `AGENTS.md` using [[Codex Setup/README]] and the portable template [[Codex Setup/Global AGENTS]]. This is required for tasks launched from other repositories: merge the template into the global file, preserve unrelated rules, and replace `{{VAULT_ROOT}}` with this folder's absolute path. The global instructions must route every software engineering session through this vault and require a dated session note plus root `log.md` link at the end of each coding session. Do not overwrite the current global profile until this starter kit is the intended primary vault.

## Install guide: Codex, skills, agents, plugins, and MCP

The detailed current-machine snapshot is [[PROFILE-INVENTORY]]. It was checked on 2026-11-23 and is not a portable lockfile. The sibling `MySoftwareEngineerVault/Codex Setup/profile-manifest.json` is older (2026-11-12). Verify current versions and selectors before restoring anything.

### Core tools for this vault

- **Obsidian:** install from [obsidian.md/download](https://obsidian.md/download), then open this folder as a vault. Obsidian's [vault guide](https://obsidian.md/help/manage-vaults) documents opening an existing local folder.
- **Codex:** install the Codex app or CLI from the [official Codex docs](https://developers.openai.com/codex). Sign in on each machine. Do not copy `auth.json`, OAuth data, history databases, or a complete machine-specific `config.toml`.
- **Node.js LTS:** install from [nodejs.org](https://nodejs.org/) for `npx` and the GSD installer.
- **Python and uv:** Graphify needs Python; the existing portability bundle uses Python 3.13. Install `uv` from [astral-sh/uv on GitHub](https://github.com/astral-sh/uv), then install Graphify in an isolated tool environment.
- **Graphify:** the existing profile snapshot pins `graphifyy` 0.9.106. Run:

  ```bash
  uv tool install 'graphifyy==0.9.106'
  ```

  This starter kit already includes the project skill at `.agents/skills/graphify/`. To install or refresh the project skill from Graphify instead, run from this folder:

  ```bash
  graphify install --project --platform codex
  ```

  Source and current install options: [Graphify GitHub](https://github.com/Graphify-Labs/graphify). Codex discovers project skills from `.agents/skills/`; invoke this skill as `$graphify`.

### Current local installation snapshot (2026-11-23)

- GSD Core `1.16.0` is installed globally: 73 shared skills (72 GSD skills plus `optimizing-ef-core-queries`), 35 unique GSD agent profiles, and 72 slash commands. The full names are in [[PROFILE-INVENTORY]].
- Six user-specific Codex skills are present: `check-repo`, `developer-task-creator`, `git-log`, `pull-request-summary`, `repo-period-summary`, and `solution-summary`. The five Codex system skills ship with Codex.
- Enabled plugin selectors: `browser@openai-bundled`, `codex-app-tools@openai-bundled`, `documents@openai-primary-runtime`, `ecc@ecc`, `pdf@openai-primary-runtime`, `presentations@openai-primary-runtime`, `spreadsheets@openai-primary-runtime`, `template-creator@openai-primary-runtime`, `unified-computer-use@openai-bundled`, and `visualize@openai-bundled`.
- MCP names reported by the current session: `chrome-devtools`, `codex_app`, `cua_repl`, and `node_repl`. `chrome-devtools` is provided by ECC; `codex_app` and `cua_repl` are runtime-provided; `node_repl` is the only explicit user-configured server.

### Current skill and agent sources

- **GSD Core:** the current local snapshot is `@opengsd/gsd-core` 1.16.0. To reproduce that version and its Codex-global agents, skills, and slash commands:

  ```bash
  npx --yes @opengsd/gsd-core@1.16.0 --codex --global
  ```

  Sources: [GSD Core repository](https://github.com/open-gsd/gsd-core) and [installation guide](https://github.com/open-gsd/docs/blob/main/core/installation.mdx). Update the pinned version only when you intend to change the profile.
- **ECC plugin:** the current local selector is `ecc@ecc` (cached version 2.2.3). Install using the repository marketplace:

  ```bash
  codex plugin marketplace add affaan-m/ECC
  codex plugin add ecc@ecc
  ```

  Source and Codex steps: [ECC repository](https://github.com/affaan-m/ECC) and its [Codex plugin README](https://github.com/affaan-m/ECC/blob/main/.codex-plugin/README.md). ECC supplies its skill bundle and the `chrome-devtools` MCP server.
- **Local user skills:** the six user-authored Codex skills and `optimizing-ef-core-queries` have no verified public GitHub source recorded. Their preserved copies are under `Codex Setup/Profile/skills/` in the sibling `MySoftwareEngineerVault` vault when available. Use those copies; do not guess a public origin.
- **Codex built-in skills and bundled plugins:** these ship with the Codex installation or app runtime. Use Codex's plugin browser or the [plugin documentation](https://developers.openai.com/plugins/concepts/plugins) rather than copying cache directories.

### MCP and plugin rules

- No MCP server is required for Obsidian, ICM routing, or a local Graphify graph.
- The current session listed `chrome-devtools`, `codex_app`, `cua_repl`, and `node_repl`. `node_repl` is the only explicit MCP server in the local Codex config; `chrome-devtools` comes from ECC, and `codex_app`/`cua_repl` are runtime-provided. These may differ on another machine.
- Inspect names with `codex mcp list` and plugins with `codex plugin list --json`. Store tokens, environment values, private URLs, and machine-specific command paths only in the local Codex configuration or approved secret store. Never copy them into this vault.
- The current enabled plugin selectors are recorded in [[PROFILE-INVENTORY]]. The `openai-bundled` and `openai-primary-runtime` selectors are supplied by the Codex runtime. Reinstall third-party plugins from their source marketplace and complete any required sign-in on the target machine.
- An MCP server exposes tools or data; a skill explains when and how to use them. Add an MCP only for a concrete workflow need, and record its public purpose and source without recording private configuration. See the [Codex plugin guide](https://developers.openai.com/plugins/build/plugins) and [OpenAI MCP documentation](https://developers.openai.com/learn/docs-mcp).

## Obsidian, Graphify, and ICM connection rules

### Obsidian

- Open `SoftwareEngineerBrain/` as its own local vault. Do not place it inside another Obsidian vault; Obsidian links are local to a vault.
- Keep the Obsidian `.obsidian/` folder for vault-specific settings. Use core Markdown, Properties, Graph, Backlinks, and Templates features where useful. No community plugin set is required by this starter kit.
- Use wiki-style links such as `[[Note title]]` for relationships between notes in this vault and preserve source URLs in reference notes.

### Graphify

- The scan root is this folder only. Never scan the parent `Documents/` directory or the sibling `MySoftwareEngineerVault/` folder.
- Graphify semantic extraction of Markdown uses a model. The existing approval to use Codex for semantic extraction applies to `MySoftwareEngineerVault`; confirm the model/data flow before the first semantic build of this separate vault.
- Index source Markdown only from `00 - Inbox/`, `10 - Projects/`, `20 - Areas/`, and `30 - Resources/`. `.graphifyignore` excludes Obsidian settings, templates, attachments, archived notes, setup instructions, the skill bundle, and generated output.
- Treat `graphify-out/graph.json`, `graph.html`, reports, caches, and query memory as derived data. Source Markdown remains authoritative. Do not hand-edit generated graph files.
- Graphify can re-ingest Markdown under `graphify-out/memory/` as query memory even though the output folder is ignored. Keep only useful query outcomes there, verify them against source notes, and treat them as graph input.
- Query an existing graph before broad searches. Verify important answers against the linked source Markdown and cite its path. `EXTRACTED` edges reflect explicit source relationships; `INFERRED` edges are hypotheses and must be checked against source notes.
- Obsidian wiki links and explicit Markdown links are the preferred way to make source relationships visible to Graphify. Keep those links truthful; do not create links just to inflate graph connectivity.
- If writing a custom Graphify extractor, use the installed package’s `graphify.ids.make_id` / `normalize_id` behavior and preserve the exact absolute `source_file` paths expected by the extraction spec.
- Build or update only this vault's graph, and follow `.agents/skills/graphify/SKILL.md` for the exact workflow. This starter kit contains no prebuilt graph.

### Lightweight ICM

This vault uses ICM's context-selection principle, not its staged workspace layout. The filesystem routes context directly: `AGENTS.md` holds operating rules; `CONTEXT.md` selects canonical destinations; each project `Hub.md` points to relevant Knowledge notes, Areas, Resources, or captures. Read only the relevant linked notes, keep one canonical explanation per fact, and use links instead of copying it. Do not add numbered processing stages or temporary workspaces.

Reference: [Interpretable Context Methodology](https://github.com/RinDig/Interpretable-Context-Methodology). This vault's lightweight adaptation is summarized in [[CONTEXT]].
