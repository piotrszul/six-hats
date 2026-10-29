# Six Hats: a Claude Code prototype

A zero-code prototype of de Bono's Six Thinking Hats as a multi-agent process.
Use it to test the hat prompts and the board format before building a real
orchestrator.

```
           ┌──────────── Blue (main session, /six-hats skill) ────────────┐
           │ frame → pick hat → assemble panel → merge → evaluate → loop  │
           └──────┬──────────────────────────────────────────────▲────────┘
                  │ parallel Agent calls (same hat, diverse      │ merged, tagged
                  ▼ persona + model)                             │ items
   ┌─────────────┬─────────────┬─────────────┐            runs/<date>-<slug>/board.md
   │ <hat>-hat   │ <hat>-hat   │ <hat>-hat   │
   │ persona A   │ persona B   │ persona C   │
   │ opus        │ sonnet      │ haiku       │
   └─────────────┴─────────────┴─────────────┘
```

## Status
| Stage | What | State |
|---|---|---|
| 1 | Claude Code prototype (subagents + skill) | ✅ here |
| 2 | Plain-SDK orchestrator: enforced loop limits, temperature, tests | planned |
| 3 | Framework version (LangGraph or Mastra) if the loop logic grows | maybe |

## Files
| Path | Role |
|---|---|
| `.claude/agents/{white,red,black,yellow,green}-hat.md` | Hat subagents with strict output formats |
| `.claude/skills/six-hats/SKILL.md` | Blue facilitator: sequencing, loop rules, merging |
| `.claude/skills/six-hats/board-template.md` | Shared board (state) |
| `.claude/skills/six-hats/personas.md` | Persona cast and model defaults for each hat |
| `runs/` | One board per session (gitignored) |
| `CLAUDE.md` | Project instructions for Claude Code |

## Run
Start Claude Code in this directory, then:
```
/six-hats Should a 12-person startup move from AWS to bare metal? --interactive
```
Flags: `--interactive`, `--blind`, `--steps N`, `--panel N`.

## Known limits of this prototype
- You can't set temperature, so diversity comes from personas and model tiers only.
- Blue is the main session's LLM, so the loop limits are followed as
  instructions. Nothing enforces them in code.
- Not batch-runnable or unit-testable. That's the job of the plain-SDK version.
