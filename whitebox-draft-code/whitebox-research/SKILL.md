---
name: whitebox-research
description: Use when the user wants rigorous, inspectable research, technical analysis, fact-checking, or design discussion with explicit citations, labeled inference, and a source list at the end.
---

# Whitebox Research

## Purpose

Use this skill when the user wants research or technical reasoning that can be audited like a lab note or paper margin.

This skill prioritizes:
- explicit citations for checkable claims
- clear separation between facts and inference
- visible uncertainty instead of smooth but unsupported prose

## When To Use

Use this skill when the user asks for:
- literature or documentation lookup
- fact-checking
- design discussion with evidence
- comparison of methods, tools, or workflows
- scientific or technical reasoning that should remain reviewable

If the task becomes code design without file writes, hand off to `whitebox-draft-code`.
If the user explicitly approves file modification, hand off to `whitebox-apply`.

## Hard Rules

1. Any checkable factual claim should carry a citation marker.
2. Any statement not directly supported by a source must be labeled as inference or unverified.
3. Do not blur recommendation with evidence. If something is a judgment call, say so.
4. Keep quotations short and cite them.
5. End with a `Sources` section.

## Citation Scheme

- `[S1]` external source such as a paper, website, API doc, or official documentation
- `[L1]` local source such as a file, config, log, or command output
- `[I1]` inference based on `[S#]` or `[L#]`

## Default Workflow

1. Identify which parts of the request are factual, inferential, and open.
2. Gather the minimum sources needed to answer responsibly.
3. Present the answer in a way the user can audit quickly.
4. Keep unknowns visible.

## Preferred Answer Shape

Adapt the size to the task, but default to:

### Conclusion
- a short answer with citation markers

### Verified Facts
- facts supported by `[S#]` or `[L#]`

### Inference Or Judgment
- recommendations, interpretations, or synthesis labeled with `[I#]`

### Open Questions
- what remains uncertain or should be checked next

### Sources
- list every `[S#]`, `[L#]`, and `[I#]`

## Notes

- Concision still matters. Whitebox does not mean verbose.
- If a source is weak, say it is weak.
- If the user asks for "just the answer", keep it short but do not drop citation hygiene.
