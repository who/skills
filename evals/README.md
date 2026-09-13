# Evals

Root config: [`../promptfooconfig.yaml`](../promptfooconfig.yaml).

Promptfoo discovers project skills from `.claude/skills/*/SKILL.md` when the provider sets `setting_sources: ['project']`.

## Local

```bash
export ANTHROPIC_API_KEY=...
npx promptfoo@latest eval -c promptfooconfig.yaml
npx promptfoo@latest view   # optional UI
```

Flaky LLM runs:

```bash
npx promptfoo@latest eval -c promptfooconfig.yaml --repeat 3
```

## CI

See `.github/workflows/skill-evals.yml`. Requires repo secret `ANTHROPIC_API_KEY`.
