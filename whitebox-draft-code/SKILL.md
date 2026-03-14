---
name: whitebox-draft-code
description: Use when the user wants code help but has not yet approved file writes, especially when they want segmented code drafts, detailed explanations, and explicit human review before any edit is applied.
---

# Whitebox Draft Code

## Purpose

Use this skill to keep coding transparent and reviewable before any file is modified.

The core idea is simple:
- code is shown in the conversation first
- the user reviews it section by section
- nothing is written to disk until approval is explicit

## When To Use

Use this skill when the user:
- asks for code but wants to inspect it first
- says they need detailed explanation to review it
- asks for draft-only code
- has not yet said `approved for write`, `apply to files`, `directly modify`, or equivalent

If the request is still mostly research or technical judgment, use `whitebox-research` first.
If the user has already approved writing reviewed code into files, switch to `whitebox-apply`.

## Hard Rules

1. Do not modify files.
2. Do not present a large unsegmented wall of code unless the user explicitly asks for a full file.
3. Default to one functional chunk at a time.
4. Every chunk must include explanation and a review target.
5. If assumptions are required, list them before the code.

## Chunking Rules

- Prefer chunks of roughly 20 to 80 lines.
- Split by function, class responsibility, pipeline stage, or config block.
- If the user asks for a full script, still break it into labeled segments unless they explicitly waive reviewability.

## Required Output Template

For each code chunk, use this order:

### Goal
- what this chunk is supposed to do

### Assumptions
- dependencies, data shape, calling context, or interface assumptions

### Draft Code
- only the current chunk

### Explanation
- explain the logic in plain language

### Review Focus
- call out the most failure-prone points for the user to check

### Next Command
- `approve next chunk`
- `approve write`
- or a concrete revision instruction from the user

## Review Focus

Ask the user to review at least these dimensions:
- input and output shape
- edge cases
- whether the API matches real use
- whether the algorithm matches the scientific or engineering intent

## Source Hygiene

- If the chunk depends on local files or existing code, cite them with `[L#]`.
- If the design depends on docs or web material, cite them with `[S#]`.
- If something is your own synthesis, label it `[I#]`.

## Notes

- The goal is not merely to explain code after writing it.
- The goal is to make the generation path inspectable before writing anything.
