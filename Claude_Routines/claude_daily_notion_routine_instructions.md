# Daily Notion Briefing Routine

You are updating task status and generating a daily morning briefing from Notion task
databases. Overwrite the existing briefing page.

The four task databases are exposed through pre-built filtered views on the
**Claude_Util** page (Status IN [To Do, In Progress, Blocked]). Use these views as
the entry point — do not search the underlying databases directly.

Claude_Util page: https://app.notion.com/p/351a2e7bfbf7818eb808c96ff542af18

Linked active-task views on Claude_Util (fetch each one in STEP 2):

| Source         | Linked view URL                                              |
|----------------|--------------------------------------------------------------|
| Personal       | https://app.notion.com/p/351a2e7bfbf78161b96cd078d196b5e3    |
| AOS Work       | https://app.notion.com/p/351a2e7bfbf781778291e2ab962353a0    |
| Projects       | https://app.notion.com/p/351a2e7bfbf78189939fd09c7b4fed36    |
| Thousand Sani  | https://app.notion.com/p/351a2e7bfbf781e39ef4d8b3ca413075    |

Each view is filtered to Status IN [To Do, In Progress, Blocked] and sorted by Due
Date ascending. Properties returned per row: Task, Status, Due Date, Priority,
Blocked By. This eliminates the per-page `notion-fetch` loop that previously
dominated token cost, and removes the 25-result search cap.

---

## STEP 1 — Auto-updates

Apply both of these directly. They do NOT appear in the Morning Briefing output.

1.1. **Promote due-soon Planned tasks.** For any task with `Status = Planned` and
     `Due Date` within the next 7 days (inclusive of today), update `Status` to
     `To Do`. Note: these views filter out Planned tasks, so for this step query
     each underlying data source for `Status = Planned` AND `Due Date <= today + 7d`
     directly — keep this query narrow.

1.2. **Unlink resolved blockers.** For each task currently in `Status = Blocked`
     (visible in the views), inspect each `Blocked By` relation. If the blocker's
     `Status = Done`, remove it from the `Blocked By` relation. If after this all
     blockers are removed, update Status to Planned.

---

## STEP 2 — Collect tasks for the briefing

Fetch the four linked view URLs above. Each returns the active tasks for that
source with full property values in a single call.

From the combined result set, **include a task in the briefing if it meets at
least one of these conditions:**
- Due Date is today or earlier (overdue or due today)
- Priority = High
- Status = Blocked

Tasks with `Status = Done` or `Status = Planned` will not appear in the views by
construction — no extra filtering needed.

---

## STEP 3 — Organize and format

Group included tasks into these sections, **in this order**, and place each task
in the FIRST section it qualifies for (do not duplicate across sections):

1. 🔴 **Overdue** — Due Date < today
2. 📅 **Due Today** — Due Date = today
3. ⭐ **High Priority** — Priority = High, not already in 1 or 2
4. 🟠 **Blocked** — Status = Blocked, not already in 1–3
5. 🟡 **In Progress** — Status = In Progress, not already in 1–4

For each task line include: task name, source (Personal / AOS / Projects /
Thousand Sani), due date if set, Priority, Status.

Omit any section that has zero tasks. If ALL sections are empty, write the single
line: `Nothing urgent today.`

Also include an **Auto-Updates Applied This Morning** section above section 1
listing what STEP 1 changed (or "No updates required today" if nothing changed).
For 1.2, list any Blocked tasks whose blockers are still not Done so the user can
see what's still in flight.

---

## STEP 4 — Overwrite the briefing page

Replace the entire content of:

`345a2e7b-fbf7-8186-b491-efb9ecd8d853`

Do not create a new page. Do not append. Use `notion-update-page` with
`command: replace_content`.

Add this line at the top of the new content: `*Generated: [today's date and time]*`

Format with markdown headers per section.

---

## STEP 5 — Optimization note

Append a `## 🔧 Process Optimization Note` section at the bottom of the briefing
covering:
- Approximate tool-call breakdown for this run (counts of fetch / search / update)
- One concrete optimization idea, only if a meaningful one exists — otherwise
  write "No new optimization to propose this run."
- If proposing a new optimization, also create a corresponding task in the
  Personal Tasks data source (`e3b71cac-4b6b-4f15-9851-47eb51b02454`) with
  `Board = Other`, `Status = To Do`, `Priority = Medium`, due 30 days out.
