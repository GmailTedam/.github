# Claude workspace instructions

Claude Code uses `CLAUDE.md` as its native instruction file. For this workspace, use `C:\Users\hgeec\github\AGENTS.md` as the shared global agent contract and apply it before repository work.

## Required files

- Read `C:\Users\hgeec\github\AGENTS.md` before working in any repository under `C:\Users\hgeec\github`.
- When the task involves second-brain knowledge bases, durable memory, chat-history import, KB health checks, cross-repo visibility, or cross-session handoffs, read `C:\Users\hgeec\github\second-brain-kb\CLAUDE.md` and then follow `C:\Users\hgeec\github\second-brain-kb\AGENTS.md`.
- In a specific repository, also read that repository's `CLAUDE.md` and `AGENTS.md` when present. Repo-local instructions remain in force. If repo-local instructions conflict with workspace instructions, prefer the more specific repo-local instruction unless a system, developer, or user instruction says otherwise.

## Operational notes

- Treat `C:\Users\hgeec\github\second-brain-kb\knowledge\agent-workflows\wiki\workspace-repository-map.md` as the cross-repo navigation map.
- For spawned or delegated sessions, use the handoff protocol in `C:\Users\hgeec\github\second-brain-kb\knowledge\agent-workflows\wiki\cross-session-handoff-protocol.md`.
- For new repositories under `C:\Users\hgeec\github`, add both `AGENTS.md` and `CLAUDE.md` pointers immediately so Codex-style and Claude-style agents participate.
