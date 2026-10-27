---
name: technical-language
description: Use when the user invokes /technical-language, or describes something in lay words because they lack the vocabulary or experience of the field - in any field (writing, design, software, offers, education, ops). Covers a problem they want removed, an ideal state they want built, or thinking they want clarified. Also use when they say an output is "not technical enough", "not what I had in my head", or that "someone out there could describe this properly".
---

# Technical Language

The user knows what they want and lacks the words and the years of experience to say it. This skill closes that gap. It ends with one of three things, each one checked against a **definition of done** the user approved:

- the work itself, done and checked the way the user would check it;
- a one-shot prompt another AI can carry out with no questions;
- a plain explanation, when the user only wants to think clearly.

The test of the whole skill: when the user opens the result, nothing in it surprises or confuses them, and nothing differs from what was in their head.

**Rules for every reply**
- **Leverage.** Do every step you can yourself. Ask the user only for what you cannot read, look up or test.
- **Word economy.** No preamble, no restating their message, no sentence they could delete without losing a fact.
- **Plain words.** Short sentences, common words, one idea per line. A professional term appears only where it is being taught: in **bold**, defined in plain words the first time. If the user has to ask you to "explain more simply", the reply already failed.
- **Elegance.** The simplest result that passes the definition of done wins. Do not add parts to satisfy a grader, a checklist or a hypothetical.
- **Their words are the input, never the output.** Do not hand their adjectives back in tidier sentences.

## 1. First line: the topic

The very first thing the user sees is one of:

> **Topic: Problem** - something they want gone
> **Topic: Solution** - something they want built
> **Topic: Clarity** - thinking they want sorted out

Then one line: **Field:** {the field whose experts solve this}. Decide both yourself; switch if the user corrects you. Show them on the first reply only.

## 2. Read first

Before asking anything, read what already exists: their message, pasted text, linked files, pages, repos, past sessions, and the memory files in section 10. Something the user pasted as an example is the Instance. A pasted path, session or link is a pointer: read what it points to. Every slot filled this way is a question the user never has to answer.

## 3. Earn the expertise: the backtest

Saying "you are a 30-year expert" gives you an expert's vocabulary with a generalist's knowledge (a **cargo cult**: the form without the substance). Experts are different because of **tacit knowledge**, things learned from years of real cases, and **recognition**: they see a situation and know at once what matters and what will go wrong. So before advising, prove you have that for this field. This is the **expert performance approach** (Anders Ericsson): test on **representative tasks** where the right answer is already known, and trade on that record the way a quant trades on a **backtested** strategy.

If `experts/{field}.md` exists (section 10) and its scorecard covers this kind of case, reuse it and skip to the scorecard line. Otherwise:

1. **Proven practitioners.** Find 2-4 people or teams whose results in this field are public and checkable (student outcomes, shipped products with numbers, published test results, a track record others cite). Popularity is not proof. Their published frameworks and words become your source and your vocabulary.
2. **Known-answer exam.** Collect 10-20 real, documented cases where the outcome is on record: published A/B tests, postmortems, ad split tests, case studies with results, the practitioners' own worked examples, graded problems. For each, write the situation without the outcome.
3. **Holdout.** Set aside at least a third of the cases before studying anything. Prefer cases newer than your training data or obscure enough that you have not memorized them; a famous case you already know the answer to tests memory, not judgment.
4. **Call it, then grade it.** For each holdout case, write your call and the cues it rests on before looking at the outcome. Grade against what actually happened. No judge, no opinion: it matched or it didn't.
5. **Novice traps.** List the mistakes the practitioners themselves say beginners make. Your calls must avoid every one.
6. **Checklist backtest.** Write the checklist this field's expert uses to judge work. Run it on documented failures: it must catch the failure that actually happened. Run it on documented successes: it must not flag them.
7. **Tested range.** Note which kinds of cases the exam covered. A case outside that range gets said out loud, not bluffed.

**Pass bar:** 80% or better on the holdout, every novice trap avoided, the checklist catches every documented failure. Below the bar: study more and retake once with fresh holdout cases. Still below: tell the user the field does not have enough on record, and what that means for trust.

**Scale to the stakes.** A one-line rewrite needs 5 holdout cases. A product build or a hire-or-fire decision needs 15-20. Never spend more on the backtest than the mistake would cost.

**Show the user only the scorecard**, in at most 4 lines, with the first question:

> **Backtest:** called {n}/{m} holdout cases from {practitioners}' published work. Missed: {case, one clause why}. Range: {kinds of cases covered}. Checklist caught {k}/{k} documented failures.

The user does not read the exam. They read the score.

## 4. Elicitation: questions and A/B rounds

Build the model of the thing: how it works now (**as-is**), what it should do (**to-be**), what causes the gap, and what done looks like. Ask as the backtested expert would: about the cues and failure modes your exam showed matter most in this field.

**Channel**
- Plain text in the reply. Never the `AskUserQuestion` tool.
- One question per turn, at most 25 words. Then stop and wait. An A/B round counts as one question.
- The question turn holds the question only.
- Every number says what it measures ("$25 = total spend cap across all test runs").
- On "i don't understand": restate in one sentence what is being decided, then repeat the same choice.

**Question form**
- Until the as-is is known: open questions, no options.
- After: 2-4 options plus "or something else". Every option traces to something the user said or something you read.
- Ask only **discriminating** questions: different answers must lead to different deliverables.
- Ask about a real past instance ("the last time this happened, what did it do?"), never a hypothetical.

**Slots, in order**
1. **System**: what the thing is, who uses it, what it does now.
2. **Instance**: one specific time it went wrong, or one example of the ideal.
3. **To-be**: what it should do instead, as something observable.
4. **Cause**: what produces the gap.
5. **Done**: the walkthrough that proves it, written as "{who} opens {X}, does {Y}, and sees {Z}". Use the check this field's experts trust in real life (section 6).
6. **Scope**: what is in and what is out.
7. **Constraints**: what must not change.

- **Fact slots** (System, Instance, Cause, Constraints): text questions.
- **Judgment slots** (To-be, Done, Scope): A/B rounds as soon as System and Instance hold facts.
- A slot can take several questions. Move on only when it holds a fact, not a guess.

**A/B rounds**

The user recognizes the right version faster than they can describe it. Three kinds of round:

- **Taste round**: two versions of their real material that differ in one property.
- **Pass/fail round**: two sample results; one meets the bar, one is quietly wrong (too broad, a detail missing, the wrong level, a novice trap). Ask "which one passes?" Each answer becomes a check in the definition of done.
- **Scope round**: one piece of work, asked "in or out?"

Rules for every round:
- **Real material**: build it from their actual thing. Keep every fact the same in both versions.
- **One variable per round**, named plainly in one line above the pair: "whether the bullet opens with the result or the action", not "depth vs breadth".
- **Short**: each version at most 2 lines or 40 words. Show only the part that changes, plus one line of context if needed to judge.
- **Goes for**: under each version, one line saying what it is trying to make the reader feel or do.
- **Reader test** (anything an audience reads): before showing a pair, check each version against "who reads this, and why would they care in the first second?" Fix a version that only states facts the reader could get anywhere.
- **Your pick**: end the round with `My pick: {A/B}, because {one clause tied to their stated priorities or a backtest finding}.` "ok" accepts it.
- **Format**: `**Round N: {variable}**`, A + Goes for, B + Goes for, My pick, then "A or B, or neither?". Nothing else in the turn.
- **Lock**: after their answer, one line `Locked: {the rule, as a parameter or a check}`. If the whole thing is 6 lines or fewer, follow with `Current:` and the full version with every lock applied. Then the next round in the same message.
- **Free text counts**: lock the rule the user stated. "A but {change}" locks A plus the change.
- **"Neither"**: lock whatever rule their reason states. No reason: ask "What's missing from both?" Two "neither" in a row on the same variable means the variable is wrong: switch to the one their reasons point to.
- **Several pieces at once**: number each set and its options 1-3, so they can answer "1, 2, 1".
- **Order**: the variable that changes the most of the result goes first.
- **Honesty**: if a version needs a fact that isn't real (an invented number), flag it and keep it out of the final output.
- **Stop**: when the next answer would not change the result, or after 10 rounds.

**Visual rounds** (UI, layout, color, type, motion): render A and B side by side with `mcp__visualize__read_me` (modules `mockup` or `interactive`) then `mcp__visualize__show_widget`. Use their real values; flag any stand-in. Caption each panel with the variable and its value (`ease-out 200ms` vs `spring 400ms`). Motion loops in both.
- **Native context**: when the thing lives somewhere specific (a feed, an inbox, a landing page, a resume PDF), mock that place at its real widths (desktop 1440, phone 375) with real neighboring content.
- **Tool fallback**: no `mcp__visualize__*` → a private Artifact or a local HTML file. A mock that imitates a real platform stays local or private, never on a public link. Nothing can render → describe both in words and say so.

## 5. Playback and the definition of done

Stop eliciting when every slot holds a fact, or the user says "go". Nothing else counts as "go". After 8 questions, play back anyway with empty slots marked `TBD`.

Show one screen, at most 12 lines:

> **You want:** {their goal in one sentence}
> **Done means:**
> 1. {who} opens {X}, does {Y}, sees {Z}
> 2. ...
> **In:** {list} · **Out:** {list}
> **Must not change:** {list}
> **Locked rules:** {numbered, from A/B rounds}

These checks are the **acceptance criteria**. The user approves the screen or fixes a line; a fix sends you back to that slot. Then ask once, as its own turn:

> Want me to research best practices online before I write this? (y/n)

On yes: search primary sources from the last 12 months (the backtested practitioners first). Use 2-4 `general-purpose` subagents only when there are several independent questions. Fold what you find into the spec; do not paste research output. If it changes a check, show the changed line.

## 6. How "done" gets checked

A check is only real if it is the experience the user, or their user, will actually have. Use the check this field's experts trust:

- **Software / UI**: open the running product in a browser and click through the walkthrough at the real widths. Not "the tests pass".
- **Writing for an audience**: read it cold, in a mock of where it will be read (feed, inbox), as the target reader.
- **Offers and sales**: run it against a real buyer's situation and objections from the record, and check value, risk and effort as the backtested practitioners frame them.
- **Performance work**: measure the number before and after, on real inputs.
- **Clarity**: the user can explain the decision back in two sentences and make it.

An AI grader may run as a side signal only. 80% from a grader is fine. Never loop to raise a grader score: it rewards the grader's blind spots and adds complexity the user then has to live with.

## 7. The no-uncertainty gate

Before anything ships, it must pass every rule:

1. **Two-reader test**: could two capable builders read it and produce different results? Then a parameter or a check is missing.
2. **Coverage**: every requirement has a check in "Done means", and every check traces to a requirement (**traceability**).
3. **Scope**: in and out are both listed.
4. **No weak words and no `TBD`** (section 9).
5. **Cold read**: one fresh subagent reads only the output and lists every question it would have to ask before starting. The list must be empty. Each question it finds goes back to a slot or a round, then the gate runs again.

## 8. Deliver

Give the user the output they asked for. If unclear, offer "do it / prompt / explanation" as a one-line closed question with your pick.

### Do it
1. Do the work. The simplest version that passes every check.
2. Run every check in "Done means" yourself, the way section 6 says.
3. Report in at most 5 lines: each check, pass or fail, with proof (screenshot, real output, the measured number).
4. A check fails twice: stop and ask the user, with what failed and your best guess why. Do not spiral.

### One-shot prompt
The prompt the practitioner would hand a builder, under the parametric rule, grouped by the practitioner's categories (template: `references/output-format.md`). It always ends with:

> **Verify before done:** run every check above as {the real-user walkthrough}. Report each as pass or fail with proof. Do not report done while any check fails. After two failed attempts on a check, stop and ask.

### Explanation (Clarity)
The decision or concept in the practitioner's framework, in plain words: what matters most, what to ignore, what they would do next. End with the two-sentence version the user should be able to say back.

### For a Problem, inside any of the three
1. **Name**: the established term. If none exists, say so; never coin one.
2. **What it is**: one or two plain lines, including the mechanism.
3. **Their instance**, quoted or pointed at.
4. **A second instance** from a different context.
5. **The removal**: what the practitioner calls the fix, and the paste-ready rule (with one before/after pair).

Apply changes to the user's files only when they say "apply it" or chose "do it".

## 9. The parametric rule

A description is technical when a builder could carry it out, and a reviewer could check it, without asking a question.

- Every line is `property: value unit`, with what it is relative to (ratio, parent, baseline) and tolerance where they matter.
- No **weak words**: "clean", "tight", "subtle", "premium", "too loose", "off". Replace each with the parameters that produce it.
- Prefer ratios to bare absolutes: "ring width 1.6% of disc radius".
- Unknown value: measure it. Cannot measure: `TBD` plus the measurement that would settle it, and resolve it before the gate.

What to pin down, by craft (prompts, not a complete list):

- **Type**: font-family, weight, size, line-height, letter-spacing, case, alignment, measure, color, contrast ratio.
- **Layout**: width, height, aspect ratio, padding, margin, gap, grid, alignment axis, breakpoints, z-order, radius, border.
- **Color and surface**: hex/HSL, opacity, gradient stops and angle, shadow offset/blur/spread/color.
- **Motion**: duration, delay, easing curve, property, start and end values.
- **3D / rendering**: geometry, position, draw order, material color/roughness/opacity, light, camera FOV and distance, anti-aliasing.
- **Writing**: sentence length, person, tense, patterns banned or required, structure, word count.
- **Systems**: versions, limits, timeouts, retries, sizes, rates, exact API and config key names.

## 10. Teach and remember

After the deliverable:

- **Glossary**: one row per term the user may not know: term, plain meaning, how to use it in a sentence. No jargon defined with jargon.
- **Say it yourself**: the one or two sentences the user could have typed to get this result.

Then save, without asking. Use `~/.claude/technical-language/` when it can be written; otherwise the project's memory folder.

- `taste.md`: every locked rule, grouped by field, one line each, with the date. Read it in section 2 every time, so the user never states the same preference twice. A new lock that contradicts an old one replaces it.
- `experts/{field}.md`: the practitioners and why they count, the exam cases (holdout marked), the scorecard, the tested range, the checklist.
- **Forward record**: in `experts/{field}.md`, log each call you make on the user's real work before the outcome is known. When the outcome arrives (the user tells you, or a later session sees it), mark it hit or miss. Show the running record in the scorecard line. This is how trust grows or shrinks on real results, like a strategy moving from backtest to live trading.

## Common mistakes

| Mistake | Fix |
|---|---|
| Playing the expert without the backtest | Scorecard first, then advice |
| Grading the backtest with an AI judge | Grade against what actually happened |
| Holdout cases you have memorized | Newer or obscure cases |
| A backtest bigger than the stakes | 5 cases for small asks, 15-20 for big ones |
| Asking what a file, page or past session already says | Read first |
| Several questions in one turn, or the question tool | One plain-text question per turn |
| Options before the as-is is known | Open questions first |
| A round with no pick | `My pick:` with one clause why |
| Two full drafts as A and B | Only the changed line, 40 words max each |
| A new pair after "neither" with no reason | Ask what's missing; after two, change the variable |
| "Done" written as a feeling | "{who} opens X, does Y, sees Z" |
| Checking with tests or a grader instead of the real experience | The section 6 check for the field |
| Looping to raise a grader score | 80% is fine; stop |
| Research after the spec is written | Offer it right after the playback is approved |
| Shipping with a question a cold reader would ask | Run the gate |
| Reporting done without proof | Each check, pass or fail, with proof |
| Spiraling on a failing check | Two fails, then ask |
| Not saving locked rules | taste.md every time |
| Treating their message as "go" | Only the word "go" |
| Offering the `parameter-hud` skill unprompted | Only for a Solution, only while the user is choosing between options |
