# Open Source Contribution

- Be proactive about contributing back. Whenever we use, debug, or read the source of an open-source tool and hit a real
  problem — a bug, a misleading error, a docs gap, a missing feature — raise the contribution as an option: file a
  GitHub issue, or, when the fix is small and self-contained, implement it and open a PR. Propose a discussion instead
  when the subject is a question, a design direction, or a "should it work this way?" rather than a defect.
- Suggest, don't publish. Writing to someone else's repo is outward-facing: surface the opportunity with a concrete
  title and a one-line body sketch, then wait for my go-ahead. Use `yeet` to publish once I approve.
- One motivation is my GitHub contribution graph, so prefer actions that count toward it: commits, opening issues,
  opening PRs, submitting PR reviews, and opening or answering discussions. Comments on existing issues and PRs do not
  count — offer them as useful, never as contributions.
- Quality bar over volume. No drive-by PRs, no issues that a search of the existing tracker or a read of the source
  would have answered. Before proposing, check for duplicates and read the repo's `CONTRIBUTING.md`. A closed-as-spam
  contribution costs more reputation than the square it fills.

## Pre-Push Review

Applies to every push, not just contributions: my repos, forks, other people's repos, and any other remote code or data
store (GitHub, GitLab, package registries, hosted databases, object storage).

- Never push blind. Before every push, read the exact set of changes about to leave the machine —
  `git diff @{push}..HEAD` (or `git diff origin/<branch>..HEAD` when no upstream is set) plus any newly added or
  untracked files — and evaluate it on the two axes below. This is a mandatory step, not a courtesy check, and it
  applies even when I authorized the push in advance.
- **Security and privacy:** does anything in the diff leak data that must not be published? Secrets, API keys, tokens,
  credentials, private keys, `.env` contents, session or cookie data, internal hostnames and URLs, personal data, client
  or employer material, or local absolute paths that expose identity or machine layout. Treat a hit as a stop condition:
  report it and wait for my call — do not push and clean up afterwards, since pushed history is effectively permanent
  and may be cached, forked, or indexed within minutes.
- **Correctness against intent:** do the changes actually achieve what this push or PR claims to achieve, and nothing
  else? Check that the diff matches the stated goal and the PR/commit description, and that it carries no debug prints,
  commented-out experiments, dead scaffolding, generated or vendored artifacts, unrelated files swept in (including
  other agents' uncommitted work), or half-finished edits. If diff and description disagree, fix one of them before
  pushing.
- Report both verdicts explicitly when reporting the push. If either check fails, do not push.
