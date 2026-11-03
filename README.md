# ProjectFunnel

An adaptive project-conception skill for Claude Code and Codex. Start with a vague idea; answer one multiple-choice question at a time; leave with a standalone prompt for a fresh conversation. Works for apps, research, writing and other projects. Choose Light (10), Medium (20) or Precise (30) core questions, including clarifications and a midpoint checkpoint, followed by up to four optional improvement proposals. It never builds the project itself.

## Install

The only instruction source is `skills/project-funnel/SKILL.md`. Copy that folder into one of these locations (create parent directories if needed):

| Tool | Project installation | Personal/global installation | Explicit invocation |
| --- | --- | --- | --- |
| Claude Code | `<project>/.claude/skills/project-funnel/SKILL.md` | `~/.claude/skills/project-funnel/SKILL.md` | `/project-funnel` |
| Codex | `<project>/.agents/skills/project-funnel/SKILL.md` | `~/.agents/skills/project-funnel/SKILL.md` | `$project-funnel` |

`~` means your home directory (on Windows, typically `C:\Users\your-name`). Copy the folder's contents, not an extra enclosing repository folder. Choose one scope per tool to avoid duplicate installations. Recopy the canonical file when updating; installed copies are deployment artifacts, not additional sources to edit. No symlinks, generator, wrapper or tool-specific instruction file is required. Cloning this repository alone does not install the skill.

For example, from this repository in PowerShell, install personally for Claude Code:

```powershell
New-Item -ItemType Directory -Force "$HOME/.claude/skills/project-funnel"
Copy-Item ./skills/project-funnel/SKILL.md "$HOME/.claude/skills/project-funnel/SKILL.md"
```

For Codex, use `.agents` instead of `.claude` in both commands. Check for an existing installation before copying; copying replaces its instructions. For project scope, use the target project's path instead of `$HOME`.

Both tools can also select the skill from its description. Codex CLI/IDE provides `/skills` and `$` selection. If it does not appear, restart the tool and verify the destination path. These instructions target local installations, not Claude cloud account skill management.

## Compatibility decisions and sources

Checked against official documentation on October 28, 2026:

- [Claude Code skills](https://code.claude.com/docs/en/skills): local project/personal directories, slash invocation, optional `name` and recommended `description` frontmatter.
- [Codex skill creation and invocation](https://learn.chatgpt.com/docs/build-skills): requires `name` and `description`; explicit and implicit invocation.
- [Codex installation locations](https://learn.chatgpt.com/docs/customization/overview): `.agents/skills` for projects and `~/.agents/skills` for user skills.

The shared frontmatter includes both fields. No Claude-only argument substitution or Codex-only UI metadata is needed. Questions prefer the native selectable-choice interface when available and permitted; numbered text is a fallback. Live host tool rules determine availability. This is a skill, not a separate autonomous subagent configuration.

## Usage

Claude Code: `/project-funnel I want a simple tool for planning my meals.`

Codex: `$project-funnel I want to define a dissertation project about local libraries.`

Select an answer in the native interface, or use a short label, number or free text in fallback mode. Choose precision at the start. Say `stop` or `generate` whenever you want the prompt. The skill follows your language. The phase ranges are guidance: already-known subjects are skipped, and a complete brief may finish early. A save offer follows the final prompt; saving requires agreement and available local file tools.

## Complete short session

This is an illustrative authored example, not a recorded runtime test. A detailed initial idea intentionally makes early completion possible.

**User:** I want a personal meal-planning app for myself. I am a beginner, have no budget, and want a local prototype in two weekends. It should store recipes and plan seven dinners. No accounts, cloud sync or nutrition tracking. I already have ten recipes in text. Success means planning my week in under ten minutes. First deliverable: a clickable mockup.

**Assistant:** The outline is emerging. You want a small local meal planner that turns your recipes into a weekly dinner plan.

Precision selection (outside the counter): Light / Medium / Precise; custom response available.

User: Medium.

Question 1/20 — Which capability should come first?
1. Weekly dinner planning
2. Recipe entry
3. Shopping list
4. Other

**User:** 1

**Assistant:** Question 2/20 — How should the first prototype retain your data?
1. Browser storage
2. A local file
3. Decide later
4. Other

**User:** 1

**Assistant:** Question 3/20 — The brief is sufficient for a first prompt. How would you like to proceed?
1. Move to recommendations
2. Refine priorities
3. Refine constraints
4. Other

**User:** 1

**User:** Generate now; skip the optional recommendations.

**Assistant:**

```markdown
Act as a project specialist. Resolve necessary uncertainties, plan the work, then deliver the first milestone described below.

## Language contract
User interaction: English. Project outputs: English (assumed from the interview). Preserve these languages independently of the handoff language.

## Project context and objective
Create a personal local meal-planning app. Success: plan seven dinners in under ten minutes. Ten existing recipes are available as text, but their contents have not yet been provided.

## Target audience
One person: the project owner.

## Prioritized features
1. Plan seven dinners for the week.
2. Enter and store recipes.

## Constraints
Beginner user; zero budget; prototype within two weekends. Persist data in browser storage. Other technology choices remain open.

## Out of scope
Accounts, cloud sync, nutrition tracking. A shopping list was not selected as a priority and needs explicit scope agreement before inclusion.

## Decisions already made
Local prototype, weekly planning first, browser persistence. First milestone: a clickable mockup.

## Open questions to resolve
Choose a suitable implementation approach and confirm whether the mockup needs persistence or whether that belongs in a later milestone. Clarify acceptable data-loss risk and backup needs before relying on browser storage.

## Instructions for the new conversation
Ask remaining necessary questions first, propose a plan suited to a beginner and the two-weekend limit, then deliver the first milestone: a clickable mockup. Explain how to use and review it.
```

**Assistant:** Would you like me to save this prompt as `PROJECT_PROMPT.md` in the current directory?

**User:** No, I will copy it.

See [the app session](examples/app.md) and [the nontechnical dissertation session](examples/dissertation.md).

## Scope and verification

Instruction-only: no dependencies, scripts, network calls or API keys. The host assistant still needs its usual runtime. The optional prompt save is the only intended file write during the interview. An explicitly selected native handoff may start work in a fresh chat. No third-party game code, data or artwork is included.

The examples are authored demonstrations. Real model behavior can vary; the instructions do not enforce a limit programmatically. Before release, try explicit invocation in both hosts, a vague answer, a contradiction, a midpoint correction, immediate `stop`, and completion at the selected limit. Confirm no implementation begins and existing prompt files are not overwritten without permission.

## License

[MIT](LICENSE).


## Interaction and prompt design (updated October 28, 2026)

The Keeper of Beginnings is an original old sage with a visible introduction, brief reactions and stage transitions, including inside popup question text. Questions and the final prompt remain literal. The examples above show the text fallback; native interfaces display selectable options instead. Mode selection is uncounted. Without extensions, maximum interview totals are 14, 24 and 34 including bonuses; with accepted extensions the maximum is 44. Intake, extension choices and delivery choice are separate. Stop/generate skips all remaining questions.

A bonus is a proposal, not another requirements question. For example, after the app interview:

> Bonus 1/4 (optional): A small export/import feature could protect your recipes if browser data is cleared. It adds implementation work, so I suggest keeping it after the mockup. Adopt / Defer / Reject; custom response available.
>
> User: Defer.
>
> Assistant: Recorded as a later possibility, outside the first milestone.

Only accepted recommendations enter confirmed scope. Deferred, rejected and unanswered suggestions are never silently added. Up to four worthwhile recommendations are allowed; none are required when they would only add noise.

Prompt design follows [OpenAI's official prompting guidance](https://developers.openai.com/api/docs/guides/prompt-engineering): explicit task, Markdown boundaries, relevant context, precise output requirements and clear separation of facts from instructions. The prompt retains the eight project sections and adds an opening task directive, acceptance checks and explicit uncertainty handling. This is a portable design choice, not a measured quality guarantee.

Native question support is conditional: Claude Code exposes AskUserQuestion in supported environments; Codex may expose request_user_input_async or request_user_input with mode-specific restrictions. The installed skill checks the live tool contract rather than assuming availability. A skill cannot force a host to render buttons or remove its submit action. See also [Codex mode commands](https://learn.chatgpt.com/docs/developer-commands). No network call is required during an interview.

Suggested manual checks: each precision mode; native and fallback choices; asynchronous unanswered choice; contradictory answer; midpoint correction; early completion; four bonuses; adoption versus rejection; stop during a bonus; final Markdown scope consistency. These remain behavioral checks to run in the host applications.


## V3 interaction fixes

- The sage introduces himself and speaks at stage transitions; questions and the AI handoff remain clear and literal.
- Choose single selection, multiple selection or ranking according to the question. Native multi-select is used only when exposed by the tool. Otherwise enter several labels together. Ranking falls back to an ordered sequence such as `C > A > B`; there is no promised drag-and-drop UI.
- The midpoint summary is embedded in the popup question itself, so validation does not depend on a hidden preceding message.
- One short question call at a time; no polling or retry loops. On tool error, reuse the same question number in text mode. Say “use text mode” to avoid popups. These instructions cannot repair a host or model that is already hung.
- Final delivery offers manual copy/paste, file saving, and a fresh conversation only when a native creation tool exists. Selecting creation sends the exact prompt and may start execution. Codex desktop can expose this tool; availability elsewhere varies. No fork or nested CLI is used as a substitute.

[Claude Code's CLI reference](https://code.claude.com/docs/en/cli-reference) documents starting an interactive session with a prompt; that is not a universal skill-callable new-chat API. Native tool schemas in the current host remain authoritative for UI features.

### Popup checkpoint example (Light mode)

The complete question field contains:

> I unfold my notebook; here is the path you have chosen.
>
> Question 5/10 — Goal: plan seven dinners in under ten minutes. Audience: you alone. Priorities: weekly planning, then recipe entry. Constraints: no budget, two weekends, beginner. Open: backup approach.
>
> Does this summary accurately describe your project?

Choices: Confirm / Correct scope / Correct constraints; free text available. The user can see every fact they are validating without dismissing the popup.

### Ranking example

> Question 8/10 — Rank these from most to least important: A weekly planning, B recipe entry, C shopping list. Enter an order such as B > A > C; ties are allowed.

User: A > B > C. The final prompt retains that ordering; ranking alone does not authorize expanding the agreed scope.

These are authored examples, not recorded UI tests. Verify popup visibility, multi-select availability and handoff in your actual client before release.


The sage celebrates once when the project is sufficiently clear, before offering early completion. The exclamation appears inside the popup when used; unresolved uncertainties remain explicit.


## English handoff and conditional extensions

The final artifact is an English Markdown document (PROJECT_PROMPT.md when saved), optimized for concise AI-to-AI transfer. A Language contract explicitly preserves the user's conversation language and the project's output languages; English prompt text must not silently turn a French project into an English one. Unspecified project language defaults to the interview language as a disclosed assumption. Brevity must preserve requirements; token savings are model-dependent.

Initial modes remain 10/20/30. At a ceiling, only consequential unresolved blockers trigger an offer to extend: 10 → 20 → 30 → 40. Each extension requires acceptance, preserves answers and continues numbering. The extension choice is an uncounted control question. Sufficiently clear projects receive no extension offer. Declining preserves open points; generate skips all remaining questions. No more than 40 core questions and four bonuses are permitted across the full session.

Boundary checks for manual testing: sufficient brief at 10 (no offer), blocking ambiguity at 10 (offer 20), declined extension (no repeat), accepted extension (question 11/20), unresolved brief at 30 (offer 40), unresolved brief at 40 (no offer), French interview with English project explicitly requested (preserve both language choices).


