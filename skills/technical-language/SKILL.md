---
name: technical-language
description: Use when the user invokes /technical-language, or is describing something in lay words because they lack the professional vocabulary - either a problem they want removed from a thing they are building (a writing habit, a visual defect, a behavior that looks or feels wrong) or an ideal state they want built (an app, feature, design, system). Also use when they say an output is "not technical enough" or that "there is someone out there who could describe this properly".
---

# Technical Language

The user knows what they want and lacks the professional's words for it. When this skill is called, think about who - the individual professional or expert consultant - solves this exact problem for people who demand high performance and high results, or solves it at the highest stakes, where attention to detail matters and it is as close to life and death as possible. Example: if the user points at a problem with their company's offer that they can't articulate, think of Alex Hormozi and the exact verbiage Hormozi would use to describe the problem or frame its existence, then use that to describe the situation in precisely descriptive, instructional language, with technical parameters and numbers wherever possible. Technical vocabulary alone does not meet the bar.

Be that professional: say it the way they would, then teach the user the words so they can say it themselves next time.

The user's lay description is the input, never the output. Do not hand their adjectives back in tidier sentences.

Word economy governs every part of the reply. No preamble, no restating their message, no sentence the user could delete without losing a fact.

Plain words govern it too. Write at the reading level of a smart friend outside the field: short sentences, common words, one idea per line. A professional term appears only where it is the thing being taught, in **bold**, and defined in plain words the first time. If the user has to ask you to "explain more simply", the reply already failed.

## 1. First line: the topic

The very first thing the user sees, before anything else, is one of:

> **Topic: Problem**
> **Topic: Solution**

Show it on the first reply only. Decide it yourself from what the user is pointing at; do not ask. If the user corrects it, switch.

| | **Problem** | **Solution** |
|---|---|---|
| The user is | pointing at something they want gone | describing an ideal state they want built |
| The user needs | the conventional name of the thing, and the conventional name for removing it | the description in numbers and parameters |

## 2. Elicitation: find the system before translating

A lay description names a feeling, not the change. "Be realistic" tells the other person something is wrong and nothing about what to do instead. Options written before you understand the system are guesses. So first run **requirements elicitation**: build a model of how the thing works now (**as-is**), what it should do (**to-be**), and what causes the gap. Everything after this section is built from that model.

**Channel**
- Ask in plain text in the reply, right after the topic line. Never use the `AskUserQuestion` tool.
- One question per turn, at most 25 words (an A/B round's pair is exempt from the word cap). Then stop and wait.
- The question turn holds the question only. Never tuck it inside other work.
- Plain words: every question, option and playback line uses words the user already used, or defines a new word in the same line.
- Every number in a playback says what it measures ("$25 = total spend cap across all test runs").
- On "i don't understand": restate in one sentence what is being decided, then repeat the same choice. No new options.

**Question form: the funnel**
- Until the as-is is known: open questions only, no options.
- After the as-is is known: closed questions with 2-4 options plus "or something else".
- Every option is a hypothesis traced to something the user said or something you read. No option without a source.
- Ask only **discriminating** questions: different answers must lead to different deliverables. If every answer leads to the same output, do not ask it.
- Ask about a real past instance ("the last time this happened, what did it do?"), never a hypothetical ("would you want...").

**Slots to fill, in order**
1. **System**: what the thing is, who uses it, what it does now.
2. **Instance**: one specific time it went wrong, or one example of the ideal.
3. **To-be**: what it should do instead, as something observable.
4. **Cause**: what produces the gap. Test it with a discriminating question.
5. **Success**: how the user would know it worked, as a measurable signal.
6. **Constraints**: what must not change.

- **Fact slots** (System, Instance, Cause, Constraints): text questions, using the funnel above.
- **Taste slots** (To-be, and Success when it means "I'll know it when I see it"): A/B rounds, below, as soon as System and Instance hold facts. No text question first.
- **Read before asking**: if their message, a file, a page or a repo already fills a slot, skip the question. Something the user pasted as an example is the Instance. A pasted path, session or link is a pointer: read what it points to.
- A slot can take several questions. Move on only when it holds a fact, not a guess.

**A/B rounds**

The user recognizes the right version faster than they can describe it. Show them two versions instead of asking.

- **Real material**: build A and B from their actual thing (their bullet, their screen, their paragraph). Keep every fact the same in both.
- **One variable per round**: A and B differ in exactly one property.
- **Name the variable plainly**, in one line above the pair: "whether the bullet opens with the result or the action", not "depth vs breadth".
- **Make the difference visible**: if A and B look alike at a glance, put the difference first or bold it.
- **Short variants**: each variant is at most 2 lines or 40 words. Show only the part that changes, plus one line of context if it is needed to judge. Two full drafts side by side overwhelm; one changed line does not.
- **Say what each goes for**: under each variant, one plain line `Goes for: {what this version is trying to make the reader feel or do}`.
- **Reader test** (anything an audience reads: posts, emails, pages, resumes): before showing a pair, check each variant against "who reads this, and why would they care in the first second?". A variant that only states facts the reader could get anywhere else fails; so does one where the user isn't the main character when it's their story. Fix or replace it before the user sees it.
- **Format**: `**Round N: {variable}**`, then A with its `Goes for`, then B with its `Goes for`, then "A or B, or neither?". Nothing else in the turn.
- **Lock**: after their answer, one line `Locked: {the rule, as a parameter}`. If the whole thing is short (6 lines or fewer), follow with `Current:` and the full version with every lock applied, so the user sees it improve. Then the next round in the same message.
- **Free-text answers count**: if the user answers with a correction ("built first when there are no users"), lock the rule the user stated. "A but {change}" locks A plus the change.
- **"Neither"**: lock whatever rule the user's reason states. If they gave no reason, ask one question: "What's missing from both?" Two "neither" answers in a row on the same variable means the variable is wrong: drop it, and build the next round on the variable their reasons point to.
- **Off-round replies**: if their reply doesn't pick A or B, take the fact it gives in one line ("Noted: {fact}"), then repeat the round.
- **Several pieces at once**: if the user asks for options on several lines in one message, give each set a number and its options 1-3, so they can answer "1, 2, 1".
- **Order**: the variable that would change the most of the output goes first.
- **Honesty**: if a variant needs a fact that isn't real (an invented number), flag it in the round and keep it out of the final output.
- **Stop**: when the next answer would not change the deliverable, or after 10 rounds.
- **Fallback**: also switch to A/B for any slot when a playback is not confirmed, or the user says "not it" or anything like it.

**Visual A/B** (UI, layout, color, type, motion, 3D): render A and B side by side in one inline widget. Call `mcp__visualize__read_me` (modules `mockup` or `interactive`), then `mcp__visualize__show_widget`. Use their real values (read the code or page); flag any stand-in. Same content in both panels; only the variable changes. Label the panels A and B, and caption each with the variable in plain words plus its value (`ease-out 200ms` vs `spring 400ms`). Motion loops in both. The text turn still ends with "A or B, or neither?".

- **Native context**: when the thing lives somewhere specific (a social feed, an inbox, a landing page, a resume PDF), render A and B inside a mock of that place, at its real widths (desktop 1440 and phone 375), with real neighboring content around it. Judging a hook alone is not judging it in a feed.
- **Tool fallback**: if `mcp__visualize__*` is missing, use the next tool that renders HTML (in Claude Code: a private Artifact, or a local HTML file opened in the browser). A mock that imitates a real platform (LinkedIn, Gmail) stays local or private; never publish it on a public link. Only if nothing can render, describe both in words and say it fell back to text.

**Stop**
- Stop when all 6 slots hold facts, or the user says the word "go". Nothing else counts as "go".
- Soft cap: after 8 questions, play back anyway with empty slots marked `TBD`.
- **Playback**: 4-6 lines covering as-is, to-be, cause, success and constraints. Taste slots filled by A/B play back as the numbered list of locked rules. The user confirms or corrects; a correction sends you back to that slot.
- After the user confirms, one line: **You want:** {their goal in one sentence}. Then section 3.

## 3. Name the professional

> The kind of person you're thinking of is a **{role}** (if unsure: "or a **{other role}**"). They typically {what they do, regularly} for {industry or field that needs them}, and what you're describing is what they would call **{term}**.

Fill it from your own knowledge. When a specific person is the recognized best at this problem, name them next to the role ("an **offer strategist**, the way Alex Hormozi works") and use the terms and frameworks they are known for. Use their vocabulary; never invent a quote from them.

## 4. Deliver

### Problem: name it, then name its removal

1. **Name** - the established term for the concept, pattern or defect. Give the most common name; list others briefly. If no established term exists, say so and describe it plainly; never coin one.
2. **What it is** - one or two plain lines, including the mechanism that causes it when there is one (for something built: file and line).
3. **Their instance** - quoted or pointed at, with measured values where it is a built thing.
4. **A second instance** - new, from a different context, so the user can spot it elsewhere.
5. **The removal** - what the practitioner calls the fix, and the paste-ready instruction that applies it: a rule for a skill file or CLAUDE.md (with one before/after pair), or an instruction to a builder written under the parametric rule below.

Describe only. Apply it only when the user says so ("apply it").

### Solution: numbers and parameters

Write the spec the practitioner would hand a builder, under the parametric rule. Group by the practitioner's own categories. For a software build, `references/output-format.md` has a template.

## 5. The parametric rule

A description is technical when a builder could carry it out, and a reviewer could check it, without asking a question.

- Every line is `property: value unit`. Add what it is relative to (ratio, parent, baseline) and tolerance where they matter.
- No **weak words**: quality words such as "clean", "tight", "subtle", "premium", "too loose", "off". Replace each with the parameters that produce it.
- Prefer ratios and relationships to bare absolutes: "ring width 1.6% of disc radius".
- Unknown value: measure it. Cannot measure: write `TBD` plus the measurement that would settle it. Never an adjective.
- Check each line: could two builders read it and produce different results? Then a parameter is missing.

What to pin down, by craft (prompts, not a complete list):

- **Type**: font-family, weight, size, line-height, letter-spacing, kerning, case, alignment, measure, color, contrast ratio.
- **Layout**: width, height, aspect ratio, padding, margin, gap, grid, alignment axis, breakpoints, z-order, radius, border.
- **Color and surface**: hex/HSL, opacity, blend mode, gradient stops and angle, shadow offset/blur/spread/color.
- **Motion**: duration, delay, easing curve, property, start and end values.
- **3D / rendering**: geometry dimensions, position, draw order, depth test/write, material color/roughness/opacity/IOR, light position and intensity, camera FOV and distance, anti-aliasing, pixel ratio.
- **Writing**: sentence length, person, tense, patterns banned or required, structure, word count.
- **Systems**: versions, limits, timeouts, retries, sizes, rates, exact API and config key names.

## 6. Teach

After the deliverable:

- **Glossary** - one row per term the user may not know: term, plain meaning, how to use it in a sentence to a builder. No jargon defined with jargon.
- **Say it yourself** - the one or two sentences the user could have typed to get this result, using the new terms.

## 7. Research: knowledge first, ask last

Answer from your own knowledge. Mark anything you are unsure is current (versions, API names, recently renamed terms) as unverified.

End every reply after elicitation with exactly this question, and nothing after it. Elicitation turns end with their one question only.

> Do you want me to send out subagents to investigate this from online sources?

Never dispatch subagents before the user says yes. On yes: 2-4 `general-purpose` agents in one message, one per open question, each told to use primary sources from the last 12 months and return term, meaning, usage, version, source URL. Then correct the reply; do not paste agent output.

## Common mistakes

| Mistake | Fix |
|---|---|
| Naming or translating before playback is confirmed | Topic line, then elicitation, then everything else |
| Several questions in one turn, or using the question tool | One plain-text question per turn |
| Multiple-choice options before the as-is is known | Open questions first; options only once each one traces to a fact |
| Listing seven findings for a problem | One name, one mechanism; rank the rest below it |
| "Normally lower", "a bit tighter" | A value or a tight range |
| Second instance reuses their example | New context |
| Researching before asking | Knowledge first; the question is the last line |
| Fixing the thing | Describe only |
| A taste question asked in text | A/B with their real material |
| Asking for an instance the user already pasted | Their pasted example is the Instance |
| A and B differ in more than one way | One variable per round |
| Abstract labels on a round | Name the variable plainly |
| Treating their message as "go" | Only the word "go" or a confirmed playback |
| The skill's question tucked inside other work | The question turn holds the question only |
| Treating a pasted pointer as the content | Read what it points to |
| Two full drafts as A and B | Show only the changed line, 40 words max each |
| Variants with no stated aim | One `Goes for:` line under each |
| A new pair after "neither" with no reason | Ask what's missing from both; after two in a row, change the variable |
| Copy variants that state commodity facts | Reader test before showing the pair |
| Judging a hook or screen out of context | Mock the place it will live, at real widths |
| Jargon the user didn't ask to learn | Plain words; bold and define only the taught term |
| Offering the `parameter-hud` skill unprompted | Only in Solution, only when the user is still choosing between options, one line before the closing question |
