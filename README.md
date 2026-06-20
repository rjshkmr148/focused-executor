# Focused Executor

A Claude skill that prevents task drift, unnecessary clarification, scope menus, and meta-discussion. It forces Claude to infer the intended deliverable from context and execute it.

## What it fixes

Focused Executor is designed for cases where Claude starts discussing the request instead of completing it. It specifically suppresses behaviors such as:

- redefining obvious terms from the conversation,
- asking avoidable clarification questions,
- presenting a menu of possible scopes,
- explaining how it plans to work instead of doing the work,
- ignoring established context,
- stopping at a plan when a completed deliverable was requested.

## Repository structure

```text
focused-executor/
├── SKILL.md
├── README.md
└── evals/
    └── evals.json
```

`SKILL.md` is intentionally at the repository root so the repository can be downloaded as a ZIP and prepared for Claude skill upload with minimal changes.

## Install in Claude.ai

1. Download this repository as a ZIP from GitHub.
2. Extract the ZIP.
3. Open the extracted `focused-executor-main` folder.
4. Select `SKILL.md`, `README.md`, and the `evals` folder.
5. Compress those selected items into a new ZIP so that `SKILL.md` is at the ZIP root.
6. Open Claude.
7. Go to **Customize > Skills**.
8. Choose the option to create or upload a custom skill.
9. Upload the new ZIP and enable **Focused Executor**.

## Install in Claude Code

Copy or clone this repository into either:

```bash
~/.claude/skills/focused-executor
```

or inside a project:

```bash
.claude/skills/focused-executor
```

## Recommended use

Keep the skill enabled for project work, coding, document creation, research, analysis, handovers, and continuation across chats.

For important tasks, reinforce it with:

```text
Use Focused Executor. Infer the intended deliverable from the full conversation, do not ask non-blocking questions, and complete the actual work rather than discussing how to approach it.
```

## Core behavior

- Treats established conversation context as authoritative.
- Uses sensible defaults for reversible details.
- Asks questions only when ambiguity is truly blocking and consequential.
- Produces the deliverable before discussing optional improvements.
- Handles “complete knowledge” handovers as operational transfer documents.
- Stops unnecessary scoping interviews and execution delays.
- Preserves safety, accuracy, and honesty when information is genuinely missing.

## Evaluation cases

The `evals/evals.json` file contains test scenarios for:

1. complete project handovers,
2. continuation from established context,
3. non-blocking formatting ambiguity,
4. genuinely blocking irreversible actions,
5. recovery after the user says Claude is drifting.
