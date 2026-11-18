# skills

Public Claude skills library under [`who`](https://github.com/who).

## Skills

### brevity

Rewrites or drafts a message in terse executive email style. It runs only when you ask for it by name (`/brevity`, `@Brevity`, or "use Brevity"), never on its own.

```bash
npx skills add who/skills --skill brevity
```

**What it is.** Ten rules for a reply: answer first, one idea per sentence, cut the padding, be specific, delegate in the reply, keep it to three lines, ask only what's needed, drop hedges, use a small sign-off, and keep every fact intact.

> Before: "Thanks so much for putting this together! I think overall it looks great, but I was wondering if maybe we could move the launch to Friday?"
>
> After: "Looks good. Launch Friday. Thanks."

**Where it came from.** In August 2026, Business Insider's Power Hours series asked CEOs how they handle email. Siemens CEO Roland Busch said he gets about 200 emails a day, keeps his inbox under 100, and answers most of them with "OK" or "No." He told the magazine his team is trained to communicate the same way. In a follow-up roundup of 100 executives, Marc Jacobs CMO Kristin Patrick described a three-line rule: if a reply needs more than three lines, she would rather get on a call. Brevity packages those habits, along with the old office joke that "Thank you so much!" shrinks to "T" as people get more senior.

- [Roland Busch's day in the life (Business Insider)](https://www.businessinsider.com/day-in-the-life-roland-busch-ceo-siemens-germany-2026-8)
- [100 CEOs and top execs on their email habits (Business Insider)](https://www.businessinsider.com/7-ways-ceos-leaders-keep-email-taking-over-their-day-2026-8)
- [Busch's one-word replies (Inc.)](https://www.inc.com/dan-schawbel/siemens-ceo-roland-busch-keeps-his-inbox-under-100-emails-his-favorite-replies-are-1-word/91393419)

**The philosophy.** The reader's attention is the scarcest thing in any message. Put the decision where they see it first, give them only what they need to act, and move anything that needs discussion into a conversation. Short only reads as rude when the reader isn't expecting it, which is why Busch sets that expectation with his team, and why this skill is opt-in rather than a default voice. Brevity changes the wording, never the commitments: a shorter message that says something different has failed.

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
