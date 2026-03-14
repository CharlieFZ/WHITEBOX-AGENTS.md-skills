---
name: whitebox-apply
description: Use only after the user explicitly approves writing reviewed code into files. Applies the approved scope, reports exactly what changed, and includes verification evidence plus remaining risks.
---

# Whitebox Apply

## Purpose

Use this skill only after the user clearly authorizes file modification.

This skill turns reviewed drafts into actual file edits while preserving an audit trail:
- what scope was approved
- what was written
- how it was verified
- what remains uncertain

## Entry Gate

Start this skill only when the user has said something equivalent to:
- `approve write`
- `apply to files`
- `directly modify`
- `write this version`

If approval is ambiguous, restate the intended file scope first.

## Hard Rules

1. Write only the scope that has been reviewed or explicitly approved.
2. Do not silently add unrelated refactors.
3. Before editing, restate the files and change areas you are about to touch.
4. After editing, run verification before claiming completion.
5. If verification is partial or fails, say so plainly.

## Default Workflow

1. Restate approved scope.
2. Apply the minimum required edits.
3. Run the most direct verification commands available.
4. Report what changed and what still needs human judgment.

## Required Output Template

### Applied Scope
- which files changed
- which reviewed chunk or approved plan each change came from

### Verification
- commands run
- pass or fail outcome
- what was not verified

### Remaining Risk
- edge cases, untested paths, or assumptions that remain

### Sources
- local files, docs, commands, and any inference markers used in the summary

## Notes

- This is still a workflow-level guardrail, not a hard sandbox block.
- If the user tries to skip review entirely on a large or risky change, compress the draft review but do not hide it.
