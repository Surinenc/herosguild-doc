<!--
  Sync Impact Report
  ==================
  Version: 1.1.0
  History:
    1.0.0 (2026-03-17): Initial constitution with 8 principles
    1.1.0 (2026-03-17): Amended Principle V to distinguish disabled
      features (keep with banner) from fully removed features
      (remove + brief note). Driven by clarification session.
  Templates:
    - .specify/templates/plan-template.md — ✅ no updates needed
    - .specify/templates/spec-template.md — ✅ no updates needed
    - .specify/templates/tasks-template.md — ✅ no updates needed
  Follow-up TODOs: none
-->

# Hero's Guild Wiki Constitution

## Core Principles

### I. Source of Truth Is Code

Every formula, number, and mechanic description MUST be verified
against the game source at:

- `game/src/models/` — data models, constants, formulas
- `game/src/scenes/` — scene logic, UI behaviour, feature gates

The canonical game source lives at
`/Users/20018578/proj/surinenc_k8s/heroworld-speckit-test/game/src/`.

Never copy values from old wiki text. If a value cannot be found
in code, flag it with `<!-- TODO: verify -->` and move on.

### II. No Fabrication

- Do NOT invent features, mechanics, or numbers not in the code.
- Do NOT add speculative content about future features.
- Do NOT keep old values that contradict the code.

### III. Verify Before Writing

For every numerical value in a guide:

1. Grep/read the source file that computes it.
2. Read the function or constant definition.
3. Write the wiki text to match the code exactly.

Cite source files in commit messages so reviewers can trace
each change back to the authoritative code.

### IV. Preserve Style

- Do NOT restructure, rename, or reformat guide files.
- Match the existing voice (second-person, informative, concise).
- Keep existing markdown patterns (tables, code blocks, headers).
- Only change content, not structure.

### V. Handle Removals and Disabled Features

- **Disabled features** (code exists but gated behind a false
  flag in GameState.ts): Keep the full section but prepend a
  "Currently Disabled" banner. Do not describe as active.
- **Fully removed features** (code deleted or no longer present):
  Remove detailed sections, add a brief note that the feature
  was removed, update cross-references in other guides.

### VI. Handle Additions Correctly

- New features (e.g., Item Workshop, Paragon Modal) go in the
  most appropriate existing guide.
- Follow adjacent section formatting.
- Only document what the code implements.

### VII. Cross-Reference Integrity

- When updating a value, search ALL guides (`guides/*.md`) for
  mentions of the old value and update every occurrence.
- Check that cross-guide links still point to valid sections.

### VIII. Commit Conventions

- Use conventional commits: `docs(guide-name): description`.
- One commit per guide or logical change group.
- No AI attribution in commit messages.

## Source Code References

The wiki documents the Hero's Guild game, a TypeScript / Phaser 3
tactical RPG.

| Resource | Path |
|---|---|
| Game source root | `/Users/20018578/proj/surinenc_k8s/heroworld-speckit-test/game/src/` |
| Models & constants | `game/src/models/` |
| Scenes & UI logic | `game/src/scenes/` |
| Wiki guides | `guides/*.md` (this repo) |

## Wiki Workflow

1. **Identify** the guide(s) affected by a code change or
   documentation gap.
2. **Verify** every value against source code (Principle III).
3. **Edit** guide content only — preserve structure (Principle IV).
4. **Cross-check** all guides for stale references (Principle VII).
5. **Commit** using the conventional format (Principle VIII).

## Governance

- This constitution supersedes informal practices. All wiki
  edits MUST comply with the principles above.
- **Amendments** require: (a) a description of the change,
  (b) rationale, (c) version bump per semantic versioning:
  - MAJOR — principle removed or redefined incompatibly.
  - MINOR — new principle or materially expanded guidance.
  - PATCH — clarifications, wording, typo fixes.
- **Compliance review**: spot-check wiki PRs against Principles
  I–III (code-verification) and VII (cross-reference integrity).

**Version**: 1.1.0 | **Ratified**: 2026-03-17 | **Last Amended**: 2026-03-17
