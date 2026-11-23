# Context routing map

Use one canonical destination for each kind of information. Start with the matching project Hub, follow only the relevant links, and stop when you have enough context.

| Request or information | Canonical location | Handling |
| --- | --- | --- |
| New thought, clip, or unprocessed source | `00 - Inbox/` | Capture briefly with date and provenance; process later. |
| Project and its current summary | `10 - Projects/<Project>/Hub.md` | Read status, repository, tracker, source of truth, next, and updated fields. |
| Project-specific durable knowledge | `10 - Projects/<Project>/Knowledge/` | Keep domain maps and separate workflow notes; link from the Hub. |
| Coding session | Matching project folder | Create one dated note from [[Templates/Coding Session]] and add a short link to [[log]]. |
| Durable technical choice | Project Hub, canonical Knowledge note, or repository ADR | Record the choice and rationale once; link related context. |
| Ongoing cross-project responsibility | `20 - Areas/` | Keep enduring practices and review cadence here. |
| External tool, book, paper, or website | `30 - Resources/` | Preserve `source_url`; separate source claims from interpretation. |
| Completed or inactive material | `40 - Archive/` | Move only when no longer active; preserve links where practical. |
| Images and other attachments | `Attachments/` | Link from the canonical Markdown note. |
| Reusable note structures | `Templates/` | Keep templates out of the knowledge graph. |
| Current Codex skill, agent, plugin, and MCP inventory | [[PROFILE-INVENTORY]] | Treat as a dated local snapshot; verify before restoring. |

## One folder per project

Each active project gets one folder under `10 - Projects/`, a `Hub.md`, dated session notes, and an optional `Knowledge/` folder. The Hub is a router, not a duplicate of all project knowledge. Record the repository and tracker when known.

## Lightweight ICM

`AGENTS.md` explains how to work here. This file routes information. Hubs and canonical notes hold durable project context. Agents load only the files needed for the current request. Do not create staged workspaces or temporary numbered processing folders.
