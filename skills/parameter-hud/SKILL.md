---
name: parameter-hud
description: Build an interactive HUD (heads-up display) that lets the user flip a project's technical parameters and watch the generated technical spec/prompt rewrite itself in real time. Use when the user accepts the HUD offer at the end of the technical-language skill, or asks for a live control panel to tune build parameters (stack, auth, rendering, model, etc.) and see the spec update instantly. Renders a self-contained interactive widget - each parameter is a control, changing it regenerates the spec client-side with no round-trip.
---

# Parameter HUD

A live control panel for a build spec. Each technical parameter becomes a control (dropdown / toggle / slider). The spec/prompt text regenerates **client-side, instantly** as controls change - so the user can explore "what if I switch Postgres→SQLite, SSR→SSG, JWT→sessions" and see the spec rewrite without a chat round-trip.

Usually invoked right after `technical-language` delivered a spec + glossary and the user said yes. It inherits that skill's researched parameters.

## What this skill needs (gather before building)

From the prior `technical-language` output (or by asking):

1. **Parameters** - each tunable axis, with its options. For every option capture:
   - `label` (what the user sees), `value` (id)
   - `spec` - the exact text fragment this option injects into the spec
   - `affects` - one line on the trade-off (shown live as a hint)
2. **The spec template** - the Deliverable A text, with `{paramId}` placeholders where each parameter's chosen fragment goes.
3. **Current/default choice** per parameter.

If invoked cold (no prior research), run a quick pass: identify 4–8 parameters that genuinely have alternatives for this project, with 2–4 options each. Don't invent fake choices - only include axes where switching is real.

## Workflow

1. **Call `mcp__visualize__read_me` first** (modules: `interactive`) - required before `show_widget`. Don't narrate that call.
2. **Read `assets/hud-template.html`** - the working skeleton. Adapt it:
   - Fill the `PARAMS` array with the real parameters/options/affects.
   - Set `SPEC_TEMPLATE` to the real spec text with `{paramId}` slots.
   - Match control types to the parameter: discrete choices → segmented buttons or dropdown; on/off → toggle; numeric range → slider.
3. **Render via `mcp__visualize__show_widget`** with the adapted HTML. Use a specific `title` (e.g. `fees_dashboard_param_hud`).
4. Tell the user, briefly: flip controls → spec on the right updates live; **Copy** grabs the current spec; **Send to chat** pushes it back as a message to build from.

## The live-update mechanism (how the template works)

- `PARAMS` holds every parameter and its options (each option carries its `spec` fragment + `affects` hint).
- On any control change, `render()` rebuilds the spec string by replacing each `{paramId}` in `SPEC_TEMPLATE` with the selected option's `spec` fragment, and refreshes the trade-off hints. Pure client-side - no model call, genuinely real-time.
- **Copy** writes the current spec to clipboard. **Send to chat** calls the global `sendPrompt(text)` so the tuned spec returns to the conversation as a build instruction.

## Guardrails

- Only include parameters with **real** alternatives - a HUD of fake knobs wastes the user's time.
- Keep `affects` hints honest and one line - this is still teaching.
- The widget must be self-contained (inline CSS/JS, theme via CSS variables per the visualize read_me). No external fetches.
- Don't rebuild the glossary here - that's `technical-language`'s job. This is the tuning surface.
