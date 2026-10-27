# Output Format Templates

The one-shot prompt and its glossary, in order. Every prompt carries its definition of done; a prompt without `Done means` and `Verify before done` fails the no-uncertainty gate. Fill the braces. Keep prose tight and reading level low.

---

## Deliverable A - The Technical Spec (ready to paste)

A self-contained description the user can paste back to a builder agent. Lead with a one-line summary, then organize by axis. Use the researched vocabulary in-place (the glossary defines it right after).

```
## {What} - technical spec

**Goal:** {one line - what this is and what it's for}

**Stack:** {framework + version, libraries, runtime - using exact current names}
**Platform / APIs:** {where it runs, what it calls - exact API/SDK names + versions}
**Architecture:** {the pattern in correct terms - e.g. "SSR with edge runtime", "event-sourced", "optimistic UI with server reconciliation"}
**Key parameters:**
- {parameter}: {chosen value} - {1-clause why}
- {parameter}: {chosen value} - {1-clause why}

**Build notes:** {anything a builder must not get wrong - deprecations, version pins, gotchas surfaced in research}

**In scope:** {list}
**Out of scope:** {list}
**Must not change:** {list}

**Done means** (acceptance criteria - each one is a real-user walkthrough):
1. {who} opens {X}, does {Y}, sees {Z}
2. ...

**Verify before done:** run every check above as {the real-user walkthrough, e.g. "open the running app at 1440 and 375 wide and click through"}. Report each as pass or fail with proof (screenshot, real output, measured number). Do not report done while any check fails. After two failed attempts on a check, stop and ask.
```

Keep it dense and correct. This is the artifact, not an essay.

---

## Deliverable B - The Glossary (teaches each term)

Scannable. Group by axis. Every non-obvious term in the spec appears here. Don't define jargon with more jargon.

```
## What these terms mean

### {Axis, e.g. Stack}

| Term | What it means | How you use it | What it affects |
|------|---------------|----------------|-----------------|
| {term} | {one plain line} | {phrase/config/call} | {trade-off - perf/cost/UX/security} |

_Current as of research: {note any versions / deprecations} · sources: {links}_
```

After the tables, one line:

> Want me to go deep on any of these - what it really does under the hood and when you'd reach for it instead of the alternative? Name it.

---

## Notes

- If an axis had no meaningful terms, drop its section.
- Put recency/version notes and source links at the foot of each axis group, not inline in every row (keeps rows readable).
- If research flagged a term as **deprecated** or **renamed**, mark it in the glossary (~~old~~ → new) so the user learns the current word, not the stale one.
