

You are updating task status and info and generating a daily morning briefing from Notion task databases. 
Overwrite the existing briefing page.

STEP 1 — Query these four Notion task databases and check each task, use the database IDs directly. These auto updates do not go in the Morning Briefing.
1.1. Tasks with a Due Date within a week and status "Planned" should be updated to status "To Do"
1.2 For Tasks that are blocked, check the blocking task and if its marked as "Done" unlink that task.

STEP 2 — Collect all tasks that meet the criteria below. Use the database IDs directly.

Databases:
- Personal Tasks:      9d83545e-7558-4193-8b13-ada61e7d0ae0
- AOS Work Tasks:      1289574a-4e47-4157-9c54-368ed43bb8e6
- Projects Tasks:      55f980da-3bee-43d9-a52e-ee0c3e99d1cf
- Thousand Sani Tasks: 7db62221-06e5-48e1-8315-b743bd710d49

Collect tasks where Status is any of: To Do, In Progress, Blocked
AND at least one of:
  - Due Date is today or earlier
  - Priority is High
  - Status is Blocked

Ignore tasks with Status = Done or Planned.

STEP 3 — Organize collected tasks into these sections:
  1. Overdue       — Due Date is before today, any status except Done
  2. Due Today     — Due Date is today
  3. High Priority — Priority = High, not already in sections 1 or 2
  4. Blocked       — Status = Blocked, not already listed above
  5. In Progress   — Status = In Progress, not already listed above

For each task include: task name, source database (Personal/AOS/Projects/
Thousand Sani), due date if set, priority, and status.

Omit any section that has zero tasks. If ALL sections are empty, write 
a single line: "Nothing urgent today."

STEP 3 — Overwrite the Notion page with ID:
345a2e7b-fbf7-8186-b491-efb9ecd8d853

Replace its entire content with the briefing you generated. 
Do not create a new page. Do not append — replace completely.
Format it cleanly using headers for each section.
Add a line at the top: "Generated: [today's date and time]"

STEP 4 — Analyze how these instructions could be improved and what tools or actions took a lot of tokens, give 1 idea how to optimize this process  and create a page at the bottom of todays briefing with this information 