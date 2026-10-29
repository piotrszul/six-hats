# Persona & model roster

A panelist = **hat** (the mode it thinks in, set by the subagent) + **persona**
(who it is, set in the prompt) + **model**. Diversity comes from these sources,
strongest first: information/tool access > model > domain/stakeholder > outlook
> temperature. Temperature can't be set in Claude Code, so the model tier and
the persona carry the diversity.

## Building personas for a problem
At setup, Blue writes a cast of 4–8 personas specific to the problem into the
board's process log. Each one is a single line with these parts:

`<tag> — <role/domain or stakeholder> — <outlook> — <time horizon>`

Example (problem: "Should our 12-person startup move from AWS to bare metal?"):
- `cfo` — finance lead, owns runway — cautious — 18 months
- `sre` — on-call infra engineer — pragmatic — next quarter
- `cto` — architect, built the AWS stack — systems thinker — 3 years
- `newhire` — junior dev, joined last month — curious outsider — now
- `customer` — enterprise customer's IT buyer — risk-averse — contract term
- `contrarian` — outside advisor — deliberately unconventional — 5 years

## Who sits on each hat's panel (default)

| Hat | Panel | Persona choice | Models |
|---|---|---|---|
| White | 2 | Different domains, with different things they'd know or look up | sonnet + haiku |
| Red | 3–4 | Stakeholders most affected | haiku (fast, gut-level) |
| Black | 2–3 | Domain experts; at least one who knows the failure modes | opus + sonnet |
| Yellow | 2–3 | Stakeholders who stand to gain, plus one sceptic forced to find value | sonnet |
| Green (generate) | 3 | Most varied outlooks; always include `contrarian` | opus + sonnet + haiku |
| Green (mitigate) | 2 | Domain experts for the risks being fixed | opus + sonnet |

The model goes in the Agent tool's `model` parameter. If it's left out, the
subagent's default applies.
