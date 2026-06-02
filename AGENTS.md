<!-- second-brain-kb:start -->

## Second Brain KB

Canonical repo: `C:\Users\hgeec\github\second-brain-kb`

When a user asks about second-brain knowledge bases, durable memory, chat-history import, KB health checks, or cross-agent knowledge continuity, use this repo first. If `C:\Users\hgeec\github\second-brain-kb\.second-brain-kb\local.json` is missing, run setup from the repo root:

```powershell
python -m pip install -e ".[dev]"
python -m second_brain_kb bootstrap
```

Then follow `C:\Users\hgeec\github\second-brain-kb\AGENTS.md`.

<!-- second-brain-kb:end -->

## Cross-session handoffs

When one agent session spawns, delegates to, or waits on another session before deciding the next step, do not rely on chat context alone. Use the filesystem as the shared coordination layer.

- Before spawning or delegating, the host session must create or name a handoff file under `C:\Users\hgeec\github\second-brain-kb\knowledge\agent-workflows\state\session-handoffs\`.
- The host must write the question, dependency, expected output, source repo, and blocking decision into that handoff file.
- The spawned session must write its outcome, evidence, files changed, commands run, validation result, blockers, and recommended next action into the same file or a clearly linked response file.
- The host session must read the handoff outcome before continuing work that depends on it.
- While the dependency is active, the spawned session should update `Status` and `Last updated` immediately when work starts, blocks, completes, or changes recommendation.
- The host session should reread the handoff immediately before each dependent decision; a missing or stale outcome means the dependency is unresolved.
- If a spawned session cannot write the handoff file, the host must treat the dependency as unresolved and ask for the missing result rather than guessing.
- Do not commit ad hoc session handoff files unless the user explicitly asks; they may contain private task context. Commit only the protocol docs and templates.

## New repository onboarding

When a new Git repository is created under `C:\Users\hgeec\github`, onboard it immediately so it participates in global instructions, Claude workflows, and second-brain cross-repo visibility.

- Add or update repo-local `AGENTS.md` with the managed global-workspace pointer to `C:\Users\hgeec\github\AGENTS.md`.
- Add or update repo-local `CLAUDE.md` with the managed global-workspace pointer to `C:\Users\hgeec\github\CLAUDE.md` and `C:\Users\hgeec\github\AGENTS.md`.
- Refresh the second-brain workspace repository inventory and wiki map in `C:\Users\hgeec\github\second-brain-kb`.
- Record the new repo in the `agent-workflows` KB as processed source material.
- Do this as part of repo creation, before relying on the repo in a spawned session or cross-repo workflow.

## Canonical artefact conventions

Four artefact shapes recur across the workspace and are parsed by downstream tooling (the matrix harness, the Seeding Alignment Gate, the journey runner, traceability checks). Author them to match the existing surface rather than inventing a new shape:

1. BulletTrain 14-column functional test or use-case matrix (the `reduced_json_matrices` JSON format).
2. Requirement IDs and traceability (FR, NFR, REQ-PROMPT, CA-, component- and sibling-scoped IDs, and the requirement to use-case to test RTM).
3. Real-service integration tests (a BulletTrain cross-system journey `*.scenario.yaml` plus runner, or a single-sibling backend `conftest.py`).
4. Seed data (a seeder definition, the FastAPI lifespan loader, and the persona-journey reset).

Disambiguation: the 14-column matrix covers functional use cases; the caid-agent 18-column `V2_18COL` matrix covers non-functional requirements (ISO/IEC 25010). Both are correct, one per requirement class.

Reference, with verbatim samples and canonical `path:line` citations: `C:\Users\hgeec\github\CANONICAL_ARTEFACT_SAMPLES_HANDOFF.md`. Claude Code sessions also load this as the global skill `canonical-artefact-conventions` at `C:\Users\hgeec\.claude\skills\canonical-artefact-conventions\`. Agents that cannot load skills should read the handoff doc directly.

## Anti-AI-writing self-instructions

Source: `https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing`

Apply these rules to prose, documentation, comments, commit messages, PR descriptions, summaries, and generated article-style content. If a higher-priority instruction, user request, or target file format requires one of these patterns, use it deliberately, minimally, and only for that purpose.

Core rule: write like a pragmatic human maintainer. Prefer specific facts, concrete reasoning, verified sources, and direct language. Do not smooth weak information into grand claims.

### Content

- Do not inflate significance with generic claims about legacy, importance, broader trends, pivotal moments, enduring impact, or transformative effects.
- Do not prove notability by piling up canned references to independent coverage, media attention, active social presence, or source types. State sourced facts instead.
- Do not add superficial analysis, especially vague participle clauses such as "highlighting", "underscoring", "reflecting", "symbolizing", "contributing to", or "fostering" unless the claim is specific and sourced.
- Do not write promotional, advertisement-like, brochure-like, or travel-guide prose. Avoid puffery such as "boasts", "vibrant", "rich", "profound", "groundbreaking", "renowned", "nestled", "in the heart of", "showcasing", or "diverse array".
- Do not use vague attribution such as "many believe", "critics argue", "some say", "observers note", or "experts suggest" without naming and citing the source.
- Do not add boilerplate "Challenges", "Future prospects", "Future outlook", or "Challenges and legacy" sections unless the user asked for that structure and the content is evidence-based.
- Do not treat list titles, broad article titles, or generic categories as if they are proper named entities.

### Language

- Keep the density of stereotypical AI vocabulary low. Avoid words such as "delve", "underscore", "showcase", "robust", "intricate", "intricacies", "tapestry", "meticulous", "pivotal", "crucial", "key", "landscape", "interplay", "enduring", "valuable", and "fostering" unless they are the clearest exact word.
- Use plain copulatives when they are right. Do not rewrite simple "is" or "are" statements into ornate constructions.
- Avoid canned contrast patterns: "not only X but also Y", "not just X but Y", "not merely X", and similar negative parallelisms.
- Do not force the rule of three. Use the number of examples or clauses the content actually needs.
- Do not use elegant variation at the cost of clarity. Repeat the correct term when repeating it is clearer than using a synonym.

### Style and formatting

- Use sentence case for headings unless the project style requires title case.
- Use bold sparingly. Do not use bold inline labels as a substitute for clear structure.
- Avoid inline-header vertical lists unless the target format clearly benefits from them. Prefer concise prose, a normal list, or a table chosen for a real reason.
- Avoid em dashes as default punctuation. Use commas, colons, semicolons, or parentheses when they read more naturally.
- Do not create unusual tables for content that should be prose or a simple list.
- Use straight quotes and apostrophes in repo files unless the existing file style or publication target requires typographic quotes.
- Do not skip heading levels.
- Do not insert thematic breaks before headings unless the existing document style requires them.
- Do not use emoji as formatting.

### User communication

- Do not open with canned assistant phrases such as "Of course", "Certainly", "You're absolutely right", or "I hope this helps". Start with the answer or the action being taken.
- Do not use stock closing phrases such as "let me know if you need anything else" or "would you like me to..." unless asking a necessary, concrete question.
- Do not include knowledge-cutoff disclaimers by habit. For current facts, verify them. For uncertainty, state the exact uncertainty and next verification step.
- Do not leave placeholder text, template prompts, or phrasal scaffolding in final output.

### Markup and citations

- Use the markup required by the destination. Use Markdown in Markdown/chat contexts and wikitext in Wikipedia/wikitext contexts; do not mix them accidentally.
- Never leave AI tool artifacts such as `turn0search0`, `turn0image0`, `contentReference`, `oaicite`, `oai_citation`, `attached_file`, `grok_card`, `attribution`, or `attributableIndex`.
- Do not invent categories, templates, policies, guidelines, shortcuts, DOIs, ISBNs, URLs, page numbers, or source metadata.
- Validate external links, DOI and ISBN targets, and source relevance before citing them.
- For book citations, include page numbers or a usable URL when they are needed for verification.
- Do not add `utm_source` tracking parameters to citations.
- Do not declare named references that are unused in the body.
- Do not use unconventional reference layouts unless the existing project style requires them.

### Wikipedia-specific hygiene

- Do not add pre-placed maintenance templates, submission statements, or permissions-gaming text.
- Do not transclude maintenance templates accidentally when mentioning them; escape or wrap template names according to the target wiki's conventions.
- Do not cite non-existent Wikipedia policies, guidelines, or shortcuts.
- Keep edit summaries concise, factual, and proportional to the edit. Do not write exhaustive policy restatements for simple changes.

### Self-review before finalizing

Scan the output for generic importance claims, promotional language, vague attribution, unsupported synthesis, canned contrast patterns, forced triads, overformatted lists, title-case headings, excessive bold, unnecessary em dashes, typographic quote drift, broken markup, placeholder artifacts, hallucinated citations, hallucinated policies, and canned openers or closers. Fix any occurrence before presenting the result.
