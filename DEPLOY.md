# Deploying Project Squad to a New Project

## Step-by-Step

### 1. Copy the Portable Toolkit

Copy these files into your project root:

```bash
# From your project root
cp -r /path/to/project-squad/.squad .
cp /path/to/project-squad/.claude/commands/create-sprint.md .claude/commands/
cp /path/to/project-squad/.claude/commands/create-spike.md .claude/commands/
cp /path/to/project-squad/.claude/commands/init-project-squad.md .claude/commands/
```

### 2. Run the Scaffolding Command

Open Claude Code in your project and run:

```
/init-project-squad
```

This creates the `research/` directory with empty living document templates.

### 3. Copy the Example Files

```bash
cp -r /path/to/project-squad/examples/sprints/ research/sprints/
cp -r /path/to/project-squad/examples/spikes/ research/spikes/
cp -r /path/to/project-squad/examples/decisions/ docs/decisions/
```

### 4. Populate the Living Documents

These files need your project's context:

| File | What to Add |
|------|------------|
| `research/PRINCIPLES.md` | Your project's design and technical principles |
| `research/PERSONAS.md` | Your project's user personas (the real people who use the product) |
| `research/DECISIONS.md` | Any existing technical decisions worth recording |

### 5. Run Sprint 000 (Foundation)

Your first sprint should be a Foundation sprint to establish baseline context. Run `/create-sprint` and use it to populate the living documents with your project's real content.

---

## What NOT to Modify

- `.squad/project-squad.md` — The 7 persona definitions are the portable constant. Do not change them per-project.
- `.claude/commands/create-sprint.md` — The sprint command is project-agnostic.
- `.claude/commands/create-spike.md` — The spike command is project-agnostic.
- `.claude/commands/init-project-squad.md` — The scaffolding command is project-agnostic.

---

## Verification Checklist

After deploying, verify:

- [ ] `.squad/project-squad.md` exists with all 7 personas
- [ ] `.claude/commands/create-sprint.md` exists
- [ ] `.claude/commands/create-spike.md` exists
- [ ] `.claude/commands/init-project-squad.md` exists
- [ ] `research/PRINCIPLES.md` exists and is populated
- [ ] `research/PERSONAS.md` exists and is populated
- [ ] `research/DECISIONS.md` exists
- [ ] `research/sprint-status.md` exists
- [ ] `research/dissent-register.md` exists
- [ ] `research/sprints/sprint-000-foundation/brief.md` exists
- [ ] `research/sprints/sprint-000-foundation/summary.json` is valid JSON
- [ ] `docs/decisions/000-adr-template.md` exists

---

## Creating a Project Context File

When deploying to a new project, it helps to create a `_meta/PROJECT_CONTEXT.md` file with project-specific information that Claude can use to populate the living documents. Use `examples/project-context-template.md` as a starting point.
