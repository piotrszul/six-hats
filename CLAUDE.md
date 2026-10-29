# Six Hats

An experiment in running de Bono's Six Thinking Hats as a multi-agent process.
**Current stage:** a prototype built only from Claude Code config (subagents
plus a skill). Next comes a plain-SDK orchestrator. See `README.md`.

## Layout
- `.claude/agents/*-hat.md`: one subagent per hat. Blue is not a subagent: the
  main session plays Blue through the `six-hats` skill.
- `.claude/skills/six-hats/`: the facilitator (`SKILL.md`), the board template,
  and the persona/model roster.
- `runs/`: session boards (gitignored; use `git add -f` to keep one as an example).

## Design rules (keep these when editing prompts)
- **The hat decides how an agent thinks; the persona decides who it is.** The
  hat always wins.
- Panels wear the **same hat at the same time** (parallel thinking), with
  diversity from persona and model tier.
- Every hat has a **strict output format**. When you change one, update the
  merge rules in `SKILL.md` and the board table it feeds.
- Blue never adds content. Every board item is tagged with its source persona.
- Disagreements are kept side by side, never averaged.
- Red output is labelled as **simulated** sentiment.

## Conventions
- Prompt files are markdown with YAML frontmatter. Keep them short and imperative.
- Restart Claude Code after adding or renaming agents or skills.
