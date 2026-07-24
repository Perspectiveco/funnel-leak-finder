# Funnel Leak Finder — a Claude skill

Find out exactly where a **Perspective** funnel is losing leads, whether the leads it does deliver actually turn into customers, and what to fix first. Every finding is backed by the user's own numbers pulled live through the Perspective MCP, not generic best-practice advice.

Built for [Perspective](https://www.perspective.co), the AI funnel platform.

## What it does

1. **Pick the analysis mode** based on real traffic: change-detection (what changed in the last 7 days vs. the 7 before), structural audit (where does this funnel leak by design), or dormant-funnel (traffic has collapsed, so that is the headline).
2. **Pull the data** per funnel: sessions, leads, conversion rate, step-by-step drop-off, mobile vs. desktop split, UTM sources, and, when connected, ad spend and CRM outcomes.
3. **Read the actual funnel copy** by walking the live pages in the browser, because the metrics tell you where people drop and only the real pages tell you why.
4. **Locate the leak** down a fixed ladder: traffic, ad-to-funnel gap, step, device, then lead quality, stopping at the level that explains most of the loss.
5. **Check lead quality, not just volume**: which answer segments actually move forward, where the CRM status ceiling is, whether the qualification questions filter anyone, and how the email sequences nurture or lose leads.
6. **Rank every leak by impact** in leads lost per month, highest first.
7. **Report and offer the fix**, with a consistent structure so repeat runs stay comparable, and offer to ship the top fix directly (never touching a live funnel without explicit confirmation).

## Requirements

- **Perspective MCP** connector, to read the real funnel data. No account yet? See [How to connect the Perspective MCP with Claude](https://intercom.help/perspective-funnels/en/articles/15374243-how-to-connect-perspective-mcp-with-claude) (about 2 minutes).
- **Ad platform connection** (Meta, Google), optional, to judge ad-to-funnel fit and CPL.
- **CRM data** (the native Perspective CRM or your own CRM connected in Claude), optional, to judge whether leads become customers.
- **Browser** connector, optional, to read the live funnel copy during the walkthrough.

The diagnosis runs with whatever is connected and states in one line what each missing connection would add. It never presents a partial diagnosis as a complete one.

## Install

1. Download **`funnel-leak-finder.skill`** from this repo.
2. In Claude (Cowork / desktop), open it and click **Save skill**, or add it under **Settings, Capabilities**.
3. Make sure the Perspective MCP is active, then ask something like *"why did my CPL jump?"* or *"audit my funnel."*

You can also install from source by copying `SKILL.md` into your skills directory.

## Repository structure

```
.
├── README.md
├── funnel-leak-finder.skill     # packaged, installable skill
└── SKILL.md                     # skill instructions + frontmatter
```

## Guardrails

- Everything is backed by the user's actual numbers. A generic tip without data pointing at it is treated as worse than no tip.
- Never fabricates or estimates a metric the data does not show. Missing data goes under "What I could not check."
- Never submits the final contact form during a walkthrough, because that would create a fake lead and could trigger live email sequences.
- Never changes a live funnel without explicit confirmation, and states exactly what it is about to change first.

## License

No license file is included yet. Add one (e.g. MIT) if you want to set explicit reuse terms.
