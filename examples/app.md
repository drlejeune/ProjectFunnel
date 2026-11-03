# App session
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


