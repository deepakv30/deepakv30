# docs: feature Apna Hisab and Hangman on profile README

**Issue:** [#1](https://github.com/deepakv30/deepakv30/issues/1)  
**Branch:** `docs/feature-apna-hisab-hangman`  
**Labels:** `sdd`, `spec-ready`, `docs`

## Outcome

GitHub profile README Featured Projects surfaces the live flagship product **Apna Hisab** and the polished public CLI **Hangman**, so recruiters and peers see the same strongest original work already shown on the portfolio site—without inventing career facts or bloating the table.

## Context

- Repo: `deepakv30/deepakv30` (profile README only; renders as https://github.com/deepakv30).
- Current Featured table (pre-change): **DevOps Mastery Guide** + **Personal Portfolio** only.
- Portfolio (`deepakv30.github.io`, Sep 2026) already showcases Apna Hisab (live) and Hangman (repo).
- Apna Hisab source `deepakv30/apna-hisab` is **private**; public proof is the live URL https://apna-hisab.ai.studio.
- Hangman source `deepakv30/Hangman` is **public**: https://github.com/deepakv30/Hangman.
- Optional learning/game: Alien Invasion (`deepakv30/AlienInvasion`)—only if the featured table stays ≤ 4–5 rows after required adds.

## Scope

**In:**
- Add a Featured Projects row for **Apna Hisab**: short split-bills blurb; link to live site; note private source if the Link cell would otherwise imply a public repo.
- Add a Featured Projects row for **Hangman**: concise CLI/game blurb; link to public repo.
- Keep the Featured table concise (target 4 rows; hard cap 5).
- Preserve existing README structure, tone, widgets (GitHub stats), About/Tech Stack/Certifications/Connect sections.

**Out:**
- Changing GitHub profile social accounts.
- Redesigning auto-generated stats widgets beyond incidental link consistency.
- Inventing career facts, employers, metrics, or skills not already present in the README or known project metadata.
- Rewriting “Currently Learning / Exploring” unless that section is clearly stale (it is not: GitOps, Platform Engineering, AI-assisted DevOps remain plausible and non-invented).
- Adding Alien Invasion when Apna Hisab + Hangman already yield a concise 4-row table (optional path deferred).

## Constraints

- HTTPS remotes and PR workflow only (`gh auth setup-git`; clone/push via `https://github.com/deepakv30/deepakv30.git`). Never SSH. Never push `main`.
- Author identity: DeepakV / deepakv.knit@gmail.com when unset.
- Match existing Featured table column layout: Project | Description | Tech Stack | Link.
- Descriptions should stay senior/impact-oriented and concise (same voice as current rows).
- Do not claim Apna Hisab source is public; prefer Live link + private-source note.

## Invariants + Check

| Invariant | Check |
|-----------|--------|
| Featured table ≤ 5 rows (prefer ≤ 4) | Count data rows after edit |
| Existing DevOps Mastery Guide and Personal Portfolio rows retained unless intentionally superseded | Diff shows keep or explicit replace rationale |
| No invented career facts | Diff touches Featured (+ specs) only; About/certs unchanged |
| Apna Hisab Link points at live HTTPS URL | Cell contains `https://apna-hisab.ai.studio` |
| Hangman Link points at public repo | Cell contains `https://github.com/deepakv30/Hangman` |
| Stats widgets and Connect block unchanged | Diff excludes those sections |
| Branch is feature branch, not `main` | `git branch --show-current` = `docs/feature-apna-hisab-hangman` |

## Prior decisions

- Issue #1 finding: omitting Apna Hisab and Hangman under-sells current work relative to the portfolio.
- Prefer live URL for private Apna Hisab over a dead/private repo link in the Link column.
- Skip Alien Invasion in this PR to keep four featured rows (DevOps Mastery Guide, Personal Portfolio, Apna Hisab, Hangman)—still within the ≤ 4–5 budget without crowding.
- Leave “Currently Learning / Exploring” unchanged; not clearly stale; do not invent skills.
- Specs at root `specs/` (not `docs/specs/`) because this repo has no docs tree beyond the profile README.

## Task breakdown

1. Write `specs/README.md` index and this spec.
2. Branch `docs/feature-apna-hisab-hangman` from up-to-date `main` (HTTPS).
3. Edit `README.md` Featured Projects: insert Apna Hisab and Hangman rows; preserve structure.
4. Self-check invariants and Given/When/Then acceptance.
5. Commit, push feature branch, open PR that Closes #1, links specs, and includes README preview test plan.

## Acceptance criteria

- **Given** a visitor opens https://github.com/deepakv30, **when** they read Featured Projects, **then** they see a row for Apna Hisab describing split-bills / settle-up value and a working link to https://apna-hisab.ai.studio (with private-source noted if a repo link is absent).
- **Given** the same Featured Projects table, **when** they look for Hangman, **then** they see a concise CLI/game row linking to https://github.com/deepakv30/Hangman.
- **Given** the updated table, **when** rows are counted, **then** there are at most 5 featured projects (this change targets 4).
- **Given** the PR diff, **when** reviewed, **then** About Me, Tech Stack, Certifications, GitHub Stats, Let's Connect, and Currently Learning are unchanged, and no new career claims appear.
- **Given** specs exist at `specs/`, **when** an agent or reviewer opens the index, **then** they can navigate to `01-featured-projects.md` and map it to issue #1.

## Implementation notes

Suggested Featured order (flagship first, then existing, then CLI):

1. **Apna Hisab** — Live split-bills PWA; Tech: React, Firebase, PWA; Link: [Live](https://apna-hisab.ai.studio) (source private).
2. **DevOps Mastery Guide** — keep existing copy/link.
3. **Personal Portfolio** — keep existing copy/link.
4. **Hangman** — tested CI-enabled Python CLI; Tech: Python; Link: [View Repo](https://github.com/deepakv30/Hangman).

Blurb seeds (shorten to table-cell length; do not invent metrics):

- Apna Hisab repo description: “The simple way for friends to split bills, track who owes whom, and settle up without awkward calculations.”
- Hangman repo description: “Clean, tested, and CI-enabled Python Hangman CLI game with ASCII art, input validation, and modern best practices.”

PR title example: `docs: feature Apna Hisab and Hangman on profile README`  
PR body must: Closes #1; link `specs/`; test plan = render README preview on GitHub.
