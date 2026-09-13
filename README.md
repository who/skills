# skills

Public Claude skills library under [`who`](https://github.com/who).

## Layout

```text
.claude/skills/<name>/SKILL.md   # Claude Agent Skills (project-discovered)
promptfooconfig.yaml             # Promptfoo eval suite
evals/                           # Eval notes / future suites
.github/workflows/skill-evals.yml
```

## Add a skill

1. Create `.claude/skills/<name>/SKILL.md` with YAML frontmatter (`name`, `description`) and instructions.
2. Add Promptfoo cases in `promptfooconfig.yaml` (assert `skill-used` and any output checks).
3. Open a PR — CI runs when skills or evals change.

## Eval locally

```bash
export ANTHROPIC_API_KEY=...   # never commit this
npx promptfoo@latest eval -c promptfooconfig.yaml
npx promptfoo@latest view
```

Optional stability:

```bash
npx promptfoo@latest eval -c promptfooconfig.yaml --repeat 3
```

Docs: [Test Agent Skills](https://www.promptfoo.dev/docs/guides/test-agent-skills/).

## CI

GitHub Actions workflow **Skill evals** uses [`promptfoo/promptfoo-action`](https://github.com/promptfoo/promptfoo-action).

Required repository secret: `ANTHROPIC_API_KEY`.

Live model spend only happens when that secret is set and the workflow runs (PR/push path filters, or **Run workflow**).

## Ortus (local develop loop)

Ortus is optional for filing failing cases and grinding harness/skill text locally. It is not a substitute for Promptfoo CI. Keep work artifacts in beads if you use Ortus; do not park long skill bodies in grind session context.

## Example fixture

`hello-skill` is a tiny eval fixture that must emit `HELLO_SKILL_OK` when used. Replace or extend it with real skills.
