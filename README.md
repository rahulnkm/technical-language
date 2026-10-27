# technical-language

A Claude Code skill for when you know what you want but not the words, or the years of experience, a professional would bring to it. Works in any field.

You describe the thing in plain words. Claude proves it has real expertise in that field before advising, pins down exactly what "done" looks like with you, and then does the work, writes a one-shot prompt, or explains it plainly. Every result is checked the way you would check it yourself.

## What it does

1. **Topic and field.** Problem to remove, solution to build, or thinking to clarify, and which field's experts solve it.
2. **Reads first.** Your message, files, pages, repos and saved preferences, so it only asks what it can't find.
3. **Backtests its expertise.** Finds practitioners with public, checkable results, builds an exam from real cases with known outcomes, hides a third of them, and calls them before looking. Graded against what actually happened, not an AI judge. You see a one-line scorecard.
4. **Questions and A/B rounds.** One plain question per turn. For judgment calls it shows two short versions from your own material, says what each goes for, and gives its pick. Pass/fail rounds and in/out rounds turn your answers into checks.
5. **Definition of done.** One screen: "you open X, do Y, see Z", what's in and out, and the locked rules. You approve it. Then it offers to research best practices before writing.
6. **No-uncertainty gate.** Every requirement has a check, nothing vague is left, and a fresh AI reading only the output has zero questions.
7. **Delivers.** Does the work and reports each check pass/fail with proof, or writes a one-shot prompt that carries the checks, or explains it plainly. Stops and asks after two failed tries.
8. **Teaches and remembers.** A glossary, the sentence you could have typed, and saved preferences plus a running track record of its calls, so each use needs fewer questions.

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
- The backtest uses web search on its own, scaled to the stakes. Best-practice research for the spec only runs if you say yes. Saved preferences and track records live in `~/.claude/technical-language/`.

## License

MIT
