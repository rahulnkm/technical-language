# technical-language

A Claude Code skill for when you know what you want but not the words a professional would use for it.

You describe the thing in plain words. Claude asks you one question at a time until it understands the system, names the kind of expert who solves this for a living, then hands back what that expert would say: the real name for the problem, or a spec written as `property: value unit` that a builder could follow without asking you anything. It ends with a glossary so you can say it yourself next time.

## What it does

1. **Topic line.** Decides whether you're pointing at a problem to remove or a result to build.
2. **Elicitation.** One plain question per turn: what the thing is, one real example, what it should do, what causes the gap, how you'd know it worked, what must not change. For taste questions it shows you a short A and B built from your own material, each with a line on what it goes for, and shows them where they will live (a feed, an inbox, a page) when that matters.
3. **Names the professional** whose job this is, and the term they'd use.
4. **Delivers.** Problem: the conventional name, the mechanism, your instance, a second instance, and the fix as a paste-ready rule. Solution: a parametric spec. No "clean", "tight" or "premium" - only values.
5. **Teaches.** A glossary, plus the one or two sentences you could have typed to get the same result.

## Install

Copy the skills into your Claude Code skills folder:

```bash
git clone https://github.com/rahulnkm/technical-language
cp -R technical-language/skills/* ~/.claude/skills/
```

Then type `/technical-language` in Claude Code, or just describe something in lay words and it triggers on its own.

## What's in here

- `skills/technical-language/` - the skill, plus a spec and glossary template in `references/output-format.md`.
- `skills/parameter-hud/` - optional companion. Turns a spec into a live panel where you flip parameters (database, auth, rendering...) and watch the spec rewrite itself.

## Notes

- Visual A/B rounds and the parameter HUD use the inline widget tool (`mcp__visualize__*`) in the Claude desktop app. Without it, the skill renders a private Artifact or a local HTML file, and only falls back to text when nothing can render.
- The skill answers from Claude's own knowledge first and only sends out research subagents if you say yes.

## License

MIT
