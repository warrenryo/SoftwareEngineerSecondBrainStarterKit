# Install the global Codex instructions

This step makes Codex consult and maintain `SoftwareEngineerBrain` even when a coding task starts in a different repository. The root `AGENTS.md` applies when this vault is open as the workspace; the global instructions route engineering sessions back to this vault.

## Install or update

1. Open the global Codex instructions file: `$CODEX_HOME/AGENTS.md` when `CODEX_HOME` is set; otherwise `~/.codex/AGENTS.md` on Linux/macOS or `%USERPROFILE%\.codex\AGENTS.md` on Windows.
2. Keep a backup of the existing file. Preserve unrelated global instructions. If another vault is already named there, replace only that vault integration block when switching the primary vault.
3. Merge the contents of [[Codex Setup/Global AGENTS]] into the global file. If the shared rules already exist, update only the vault-specific block; if the global file is empty, use the full template. Replace `{{VAULT_ROOT}}` with the absolute path to this `SoftwareEngineerBrain` folder on this machine.
4. Confirm the global section directs every software engineering session to read this vault's `AGENTS.md`, `CONTEXT.md`, and matching project `Hub.md`; it must also require a dated session note and root `log.md` link at the end of each coding session.
5. Save the file, restart Codex or start a new session, and confirm that a task launched from another repository still consults this vault.

Do not overwrite the global file wholesale when it contains other useful rules. Never add credentials, API keys, private MCP settings, session history, or machine-specific MCP command details to the template. If this vault moves, update the absolute `VAULT_ROOT` in the global instructions.
