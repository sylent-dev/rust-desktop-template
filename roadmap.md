# Roadmap

The steps chosen for the application described in [specs.md](specs.md), following [process.md](process.md). Each step is delivered in its own pull request, which checks its box. What is noted and not chosen yet lives in [backlog.md](backlog.md).

## Size of the project

<!-- Chosen with the owner at the setup (process.md, Size the project): the tools this project uses, and how far. For example: « An application of several windows: every tool, in order, for the first cycle. » -->

## Reference

Read only by the steps that need them:

- [Technical choices](docs/technical-choices.md): the libraries, the services and the main designs, with their reasons.
- [Code quality](docs/code-quality.md): the rules of the code, read at the start of each step that changes code.
- [Releases](docs/releases.md): how to publish a version, and what its archives hold.
- [Lessons](docs/lessons.md): what working on the project taught, kept for the retrospectives.
- `docs/roadmap-archive.md`: the detail of the steps done, moved there once their pull request is merged.
- [Backlog](backlog.md): what is noted and not chosen yet, read when the next work is chosen.

## Models

Each step to come names the Claude model recommended for its session, so that the owner switches with `/model` before starting it; a new step or sub-step gets its model when it is written here. A judgment of what a quiet mistake would cost, not of the size of the step: Fable 5.2 for critical code (the rules of an external service the application must not break, the matching of the data a result depends on, what installs code on a user's machine); Opus 5.5 for every other step (specifications, mock-up, interface, refactoring, release, documentation). A step that decides what the user is shown as true (a price, a match, an estimate) is critical, whatever its size: rate it so when it is written.

The subagents (`code-reviewer`, `security-auditor`, `dependency-reviewer`) name no model and run on the model of the session, but a code review, whose model follows what it reads: Opus 5.5 for a pull request of tests alone or of moves alone, also in a session on Fable 5.2, a miss there leaving a weaker guard or a move to look at again, not a bug; Fable 5.2 for critical code; the model of the session otherwise. Claude Code gives `code-reviewer` its model when it launches it, and says it with the cost of the review; the notes of a review name at their top the model that wrote them, and the line of the step says which model reviewed it. If a step proves harder than its model (a review that keeps finding medium recommendations, a design that doesn't settle), say so and propose to switch.

## Steps

<!--
One line per step, small enough to be reviewed in one pull request, naming its model and the tools it needs (process.md, Size a change), for example:
- [ ] **1. Settings and local files** (model: Opus 5.5; specifications, build; 1 pull request expected): read and write `settings.toml`.
A later cycle adds its steps under a heading of its own (« Cycle 2: a history window and Windows support »), numbered after the last one.
The steps below come from the lessons of the previous projects: number them after the steps of the project, and adapt or remove them with the owner.
-->

### Cycle 1: the first release

The steps may be split into sub-steps when a pull request grows too large. When no step is left, Claude Code proposes the next items of the backlog to the owner.

- [ ] **Quality review** (model: Opus 5.5, Fable 5.2 for the critical areas): before the first release, the whole repository reviewed area by area (process.md, Release): `code-reviewer` in its area mode, one pass per area at once, each told what the others read and given the results of Clippy and of the tests run once before them, against SOLID, DRY and KISS, a design pattern only where it removes a real difficulty. Its findings split into pull requests, in this order: the fixes of behavior, the tests, what needs a mock-up, the moves last.
- [ ] **First release** (model: Opus 5.5): the security audit, the guides of `docs/tests/` run again, the notes of the version, a build by hand of every system, then the tag (`docs/releases.md`).
- [ ] **Donation method** (model: Opus 5.5): if the owner wants one, a donation link in the README, on the site and, discreetly, in the application (mock-up first). Before opening a new donation page, check what the payment service shows the donors (the legal name, the email, the statement descriptor), with one page per application (process.md, Release).
- [ ] **First retrospective** (model: Opus 5.5): right after the first release, while the lessons are fresh and the users' reports take time to come: the lessons of `docs/lessons.md` sorted one by one with the owner (process.md, Retrospective), into this project, the templates, or dropped.

### After the first release

- [ ] **Polish** (model: Opus 5.5): the last touches, picked with the owner from `backlog.md` (Polish, Edge cases), released together as a patch version.
- [ ] **Second retrospective** (model: Opus 5.5): right after the polish, the same sorting on the lessons written since the first one, with the users' reports as well.
