# Backlog

What is noted and not being done: an evolving list, read when the next work is chosen (process.md, The backlog), not at every session. When the owner picks an item, it leaves this file and becomes a step of [roadmap.md](roadmap.md).

<!--
One entry per item, in the section of its kind: what it is in one sentence, what it depends on, and the date it was noted. For example:
- The error message of a missing file doesn't say which one. Noted on 2026-11-02.
- A Windows build. Waits on: a Windows machine to test the clipboard. Noted on 2026-11-02.
-->

## Polish

<!-- Small touches, one small pull request each. -->

## Edge cases

<!-- Cases at the margin that need thought before a pull request. -->

## Features

<!-- New commands, options, outputs or screens for a later cycle. -->

## Large works

<!-- Works of several cycles, or that change the structure. -->

- A skill `rust-refactoring`: the method of the refactoring of rust-exile-market (step 17e3d) step by step, with its tools made generic. The whole area read and a numbered plan proposed; the moves first, by script, checked line by line; then one commit per improvement, the outputs compared byte for byte and the hot path timed; a brief of the review with one question per commit. The rules stay in `docs/code-quality.md` (Refactoring), which the skill points to. Its scripts, from `outputs/2026-11-11-move-scripts/` of rust-exile-market: `chunks.py` (a Rust file cut into its top-level items), `verify_moves.py` (every old line found in the new files), `open_private.py` and `errors.py` (the items made `pub(super)` from the errors of `cargo check`), and one splitter reading a plan from a small file (item → destination) in place of one script per file. About an hour, code tested on a small sample crate; for `rust-cli-template` too. Depends on nothing: when a project starts its first large refactoring, or at the second retrospective of rust-exile-market (its step 23). Noted on 2026-11-15 (owner: the refactoring brought a lot and will bring more).

## Waiting on others

<!-- What depends on someone else than the owner and Claude Code; say on whom and on what. -->

## Explorations kept

<!-- Exploration branches kept unmerged, and why. -->
