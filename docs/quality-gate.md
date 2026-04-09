# Content Quality Gate

Every post must pass this gate before publishing. No exceptions.

## What It Checks

The `avoid-ai-writing` skill audits content for:
- AI-isms: generic filler phrases, preamble, over-hedging
- Non-specific claims that could apply to anything
- Robotic sentence structures and passive voice overuse
- Words flagged as AI tells: "delve", "it's important to note", "in conclusion", etc.

## How to Run the Gate (ContentCreator)

1. Draft your post content
2. Invoke the `avoid-ai-writing` skill on the draft
3. Review flagged issues
4. Rewrite flagged sections until the audit passes
5. Post only after passing

## Gate Criteria

A post passes when:
- No AI-isms flagged by the skill
- Content is specific (includes concrete details, not vague generalities)
- Voice sounds like a knowledgeable human, not a language model

## Pre-Publish Checklist

Before every post, run through this list:

- [ ] `avoid-ai-writing` audit passed (no flags)
- [ ] At least one specific fact, number, or named example
- [ ] No opening preamble ("In today's fast-paced world...")
- [ ] No closing platitudes ("The future is bright for...")
- [ ] Post would make sense if a human expert said it

## Common Fixes

| Flagged Pattern | Fix |
|----------------|-----|
| "It's important to note that..." | Delete it. Lead with the fact. |
| "In conclusion..." | Delete it. End with the point. |
| "AI is transforming..." | Name a specific transformation with evidence. |
| Passive voice clusters | Rewrite with active subject doing the action. |

## Questions

If you're unsure whether something passes, err on the side of rewriting. A shorter, clearer post beats a longer qualified one.

---
*Last Updated: 2026-04-09 | Related: [ABA-6](/ABA/issues/ABA-6)*
