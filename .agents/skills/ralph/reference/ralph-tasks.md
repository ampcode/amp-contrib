# Ralph Tasks

`scripts/ralph-tasks` is Ralph's task helper. It keeps task state in hidden Git refs instead of files in the worktree.

## Ref Layout

- `refs/ralph/features/<feature-id>`: per-feature state history.
- `refs/ralph/active`: symbolic ref to the active feature.

Each feature ref points to a commit containing a small state tree with feature metadata, task files, patterns, and progress entries.

## Resolve The Helper Path

```bash
RALPH_SKILL_URL="$(amp skill info ralph | sed -n 's/^Path: //p')"
RALPH_SKILL_PATH_ENCODED="${RALPH_SKILL_URL#file://}"
RALPH_SKILL_PATH="$(printf '%b' "${RALPH_SKILL_PATH_ENCODED//%/\\x}")"
RALPH_TASKS="$RALPH_SKILL_PATH/scripts/ralph-tasks"
```

## Common Commands

### Create And Activate A Feature

```bash
"$RALPH_TASKS" init-feature \
  --title "Legal Agent Expense Upsert Tool" \
  --description "Expense CRUD and listing support for the legal agent"
```

### List Features

```bash
"$RALPH_TASKS" list-features
"$RALPH_TASKS" list-features --json
```

### Show Or Activate A Feature

```bash
"$RALPH_TASKS" show-feature --feature 20260331-101500-expense-upsert-a1b2c3
"$RALPH_TASKS" activate-feature --feature 20260331-101500-expense-upsert-a1b2c3
"$RALPH_TASKS" current-feature
```

### Create A Task

```bash
cat <<'EOF' | "$RALPH_TASKS" add-task \
  --title "Create expense tool skeleton" \
  --description-file -
Create the initial tool file, Zod schema, and registration wiring.

**Files:**
- `workflows/tools/upsert-expense.ts`

**Acceptance criteria:**
- Tool is registered
- `npm run typecheck` passes
EOF
```

### Create A Dependent Task

```bash
cat <<'EOF' | "$RALPH_TASKS" add-task \
  --title "Implement category mapping" \
  --depends-on task-001 \
  --description-file -
Implement category lookup and alias handling.

**Acceptance criteria:**
- Category names resolve to IDs
- `npm run typecheck` passes
EOF
```

### Create A Nested Task

```bash
cat <<'EOF' | "$RALPH_TASKS" add-task \
  --title "UI follow-up" \
  --parent-task task-010 \
  --depends-on task-005 \
  --description-file -
Implement the UI task grouped under the existing container task.
EOF
```

### Inspect Status

```bash
"$RALPH_TASKS" status
"$RALPH_TASKS" list-tasks --ready --leaf-only
"$RALPH_TASKS" list-tasks --ready --leaf-only --json
```

### Update A Task

```bash
"$RALPH_TASKS" update-task --task task-002 --status completed
```

Replace dependencies:

```bash
"$RALPH_TASKS" update-task \
  --task task-004 \
  --replace-depends-on task-002 \
  --replace-depends-on task-003
```

### Append Progress

```bash
cat <<'EOF' | "$RALPH_TASKS" append-progress \
  --task task-002 \
  --title "Implement category mapping" \
  --thread-url "https://ampcode.com/threads/[thread-id]"
- Added category lookup.
- Files changed: `workflows/tools/upsert-expense.ts`
- Learnings for future iterations:
  - Reuse income-tool lookup aliases.
EOF
```

### Add A Reusable Pattern

```bash
cat <<'EOF' | "$RALPH_TASKS" add-pattern
When adding legal-agent finance tools, reuse the income tool's parsing helpers before branching into domain-specific behavior.
EOF
```

### Validate The Graph

```bash
"$RALPH_TASKS" validate-feature
```

This checks for:

- Missing parent tasks
- Missing dependencies
- Dependency cycles
- Parent cycles
- Invalid task status values

### Complete The Feature

```bash
"$RALPH_TASKS" complete-feature
```

This only succeeds when all leaf tasks are completed. It marks remaining container tasks completed and clears `refs/ralph/active` if this feature was active.

## Output Notes

- Most commands support `--json`.
- `status` reports ready and blocked leaf tasks.
- `list-tasks --ready --leaf-only` is the main queue Ralph should use.
- `show-feature --json` includes `codebasePatterns`, `progress`, and augmented task metadata such as `ready`, `blockedOn`, and `isLeaf`.

## Sync Notes

Custom refs are not synced by normal branch fetches and pushes.

If you want to share Ralph state between clones, explicitly fetch and push the Ralph refs you care about.

Examples:

```bash
git fetch origin refs/ralph/active:refs/ralph/active
git fetch origin refs/ralph/features/<feature-id>:refs/ralph/features/<feature-id>

git push origin refs/ralph/active:refs/ralph/active
git push origin refs/ralph/features/<feature-id>:refs/ralph/features/<feature-id>
```

For long-term use across clones, consider adding a dedicated fetch refspec for `refs/ralph/*` to the remote config.
