# Global Codex repository guidance

## Skill-first request workflow

Before handling each user request, check the user-level Codex skill roots (`%USERPROFILE%\.codex\skills` or `$CODEX_HOME\skills`) and the shared skill root (`%USERPROFILE%\.agents\skills`) for an applicable `SKILL.md` and read the best match before proceeding. Give particular attention to these skills when the request matches:

- Solution recaps: `solution-summary`
- Repository period summaries: `repo-period-summary`
- Developer task or issue creation: `developer-task-creator`
- Git pull request summaries, titles, or descriptions: `pull-request-summary`; use `git-log` as well when the request needs a merge-boundary history review

Also consider relevant skills provided by installed plugins when they add a needed workflow. If no applicable skill is available, continue with the normal instructions. Do not claim a skill was used unless its instructions were read and applied.

For solution summaries and developer task writeups, include verified client-facing navigation and tester steps for affected workflows, with roles, prerequisites, and observable pass criteria when known. For UI changes in pull request summaries, include the same navigation when it helps reviewers/testers. If the task is backend-only or the entry point cannot be verified, give the verified API/operational path or clearly mark navigation as unavailable/unverified; never guess routes.

## Reuse existing UI components

Before creating or styling a form control, inspect the repository's shared components and reuse them whenever they meet the requirement. This applies to text inputs, textareas, selects, date pickers, upload/file controls, rich-text editors, buttons, modals, dialogs, confirmation prompts, labels, and validation helpers. Keep new forms visually and behaviorally consistent with the existing application. Create a new component only when an existing one cannot support the required interaction without a regression.

## Code formatting

Format frontend code with the repository's Prettier configuration before completing a task. Do not compress components, handlers, conditionals, object literals, or JSX into dense single-line code. Prefer readable multi-line formatting that remains easy to review and maintain.

## Grounded code navigation in plans

For every repository code-change plan, after inspecting the current codebase, include:

- **Code navigation:** Trace the relevant flow through verified files and symbols, such as the frontend component, API client, controller, service, query or repository, and DTO. Include only applicable layers. Use repository paths and line references only when verified.
- **Suggested implementation:** Recommend concrete changes that fit the existing architecture and service/controller patterns. Name relevant methods, interfaces, or DTO changes, and add a short code sketch or pseudocode when it clarifies the approach.
- **Grounding:** Tie recommendations to the inspected code. Do not invent paths or present generic suggestions as repository-specific. If a layer does not apply or the source is unclear, say so.

Keep plans concise. For small changes, combine navigation and implementation guidance while still giving a verified source location and a concrete recommendation. Omit code navigation for non-code plans.

For multi-file implementation plans, present the work as ordered steps. In each step:

- Name the exact existing files to modify and new files to create, and identify the affected symbols (for example, a component, API client method, controller route, service method, interface, query, or DTO).
- Point to the verified insertion or change location using line references when available; otherwise name the nearest verified symbol. Do not guess line numbers.
- Include a localized code sketch or pseudocode for the affected method or component when it helps the implementation agent understand what to change. Label sketches as pseudocode when they are not intended to compile as written.
- Make clear how each layer connects to the next so the implementation can be followed from the UI through the API to the server and data access layers, where applicable.

Plans should make it clear which code is reused, which code is added, and which code is changed. Avoid vague steps such as “update the service” without naming the service and method.

## Question-and-wait behavior

When a question needs the user's choice or answer before work can continue, ask it and stop the dependent work until the user replies. Do not guess the answer, treat silence or elapsed time as approval, or continue with work that depends on the answer. Independent work may continue while waiting.

## SoftwareEngineerBrain

Vault root: {{VAULT_ROOT}}.

For software engineering work, coding context, project status, and engineering priorities, use this vault as the Obsidian knowledge source. Read its AGENTS.md and CONTEXT.md, confirm the root, and inspect only the matching project Hub and relevant linked Knowledge, Area, Resource, or Inbox notes.

Always maintain this vault at the end of every coding session, including when implementation work happened in a separate repository. Create the dated session note and root log link described below; update the project Hub fields when they change.

Before repository work, find the matching project folder under 10 - Projects and read its Hub.md. If an ongoing project has no folder yet, create one from Templates/Project.md and record its repository and tracker. Read the target repository's AGENTS.md or CLAUDE.md before editing. Keep repository and issue tracker records authoritative for live code and execution status; use the vault for durable context, concise project routing, and cross-project engineering knowledge.

At the end of a coding session, update the project Hub's status, next, and updated fields when they change. Create one dated session note directly in the project folder from Templates/Coding Session.md, including Focus, What was built, Mistakes, Decisions, Wins, context links, changed files, verification (or state not run), and next action. Add a short dated link to root log.md. Keep detailed code history in the repository or tracker.

For new captures, ongoing practices, and external references, follow the vault's routing map. Link related notes instead of duplicating the same explanation. Use Graphify only with this vault as its scan root and follow its project-scoped skill. Treat inferred graph relationships as suggestions to verify against source notes.

For personal topics that are not represented in this engineering vault, ask for the relevant source rather than assuming the vault contains that information.

For questions about installed Codex agents or plugins, verify the current local Codex profile configuration; treat any vault inventory note as a dated snapshot.

## Task Documentation and Change Records

For user-visible changes intended for release, update a changelog only when the target repository already maintains one. Do not create CHANGELOG.md or another changelog file unless the user explicitly asks. Create or update an ADR through the target repository's existing process for significant technical decisions, recording the context, choice, and rationale. Do not create separate vault log entries for intermediate edits. Keep Git commits and pull requests as the detailed code history; link to them from Obsidian when useful.
