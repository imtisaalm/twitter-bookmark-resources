# Anti-slop code review agents

Research snapshot: 2026-09-17. X was used for discovery; official repositories and vendor documentation were used for verification.

## Recommendation for these projects

Use a layered review stack rather than trusting one AI reviewer:

1. Run a semantic review over the diff and relevant codebase context.
2. Require deterministic lint, typecheck, tests, and security checks.
3. Use an independent reviewer from a different model family when the authoring agent made a high-risk change.
4. Keep every new reviewer advisory until its signal-to-noise ratio is measured.

### Best immediate option

[Addy Osmani's `code-review-and-quality` skill](https://github.com/addyosmani/agent-skills/blob/main/skills/code-review-and-quality/SKILL.md) is the best no-new-service starting point. It reviews correctness, readability, architecture, security, performance, tests, needless complexity, dead code, and dependency risk. It can be invoked by Codex against a working-tree diff, branch, or commit.

A current [X comparison by Eric Bouck](https://x.com/ericbouck/status/2100626485484879936) reported that GPT-5.6 Sol with this skill found more and more serious issues on branches Greptile had already reviewed. This is useful discovery evidence, not a controlled benchmark.

Do not install it automatically yet. Keep the official source link here, and use it from the cloud or install only the individual skill when a review task needs it.

### Deterministic companion already available

The installed [`dmmulroy/anti-slop`](https://github.com/dmmulroy/anti-slop) skill is an Oxlint rule installer, not an autonomous reviewer. It targets concrete TypeScript/JavaScript problems such as unsafe assertions, `unknown` laundering, suspicious reflection, module mocking, and inefficient accumulator copying.

- First report-only sandbox: `imtisaal-portfolio`.
- First enforceable pilot after manual review: `icd-10-mapping-reference-tool`, which currently has a clean lint/type/test baseline including 59 passing tests.
- Do not roll it into dirty or live repositories yet: `elevate-studio`, `semantic-photo-search`, `lab-zero-outreach`, `lab-zero-website`, `Lab-Zero-Primer`, `labzerosite`, or `minimal-embodiment`.
- It adds no value to Python or Julia projects; keep Ruff/Pyright/Pytest or Julia-native checks there.

## Hosted PR reviewers

### 1. Greptile — best independent pilot

[Greptile](https://www.greptile.com/docs/introduction) builds a codebase graph and posts context-aware PR findings. The strongest independent X signal found was a team that tried CodeRabbit, Qodo, Graphite, Greptile, and Copilot and selected Greptile for learned context, priority labels, and sandboxed branch testing: [X post](https://x.com/housecor/status/2080644603477217589).

Its [current pricing](https://www.greptile.com/) includes a free starter for one active developer with 50 monthly credits; Pro is $30 per seat per month with 50 credits per seat and paid overages. If piloted, use one clean non-sensitive repository, advisory comments only, no autofix or auto-merge, and review repository-retention terms first.

### 2. CodeRabbit — broadest hosted workflow, but not the first spend

[CodeRabbit](https://www.coderabbit.ai/) combines PR and local reviews, custom checks, linters/SAST, fixes, multi-repository context, and higher-tier architecture analysis. Its portable [code-review skill](https://github.com/coderabbitai/skills/blob/main/skills/code-review/SKILL.md) is MIT licensed.

The hosted product starts at [paid per-developer tiers with possible per-file overages](https://www.coderabbit.ai/pricing). It is mature, but X discussion included recent dissatisfaction and alternative-shopping. Evaluate it only through a measured trial against the same PR set as the local Codex review.

### 3. Qodo / PR-Agent — best open, remote-run option

[PR-Agent](https://github.com/The-PR-Agent/pr-agent) is MIT licensed and supports GitHub, GitLab, Bitbucket, Azure DevOps, and Gitea through CLI, Actions, Docker, and webhooks with many model providers. It should run in GitHub Actions or another cloud runner; do not clone its roughly 100 MB repository onto this Mac.

The project now describes itself as a community-maintained legacy project of Qodo, so expect less context depth and support than the hosted [Qodo](https://www.qodo.ai/) product. Use BYO-model spend limits and pin the workflow by commit SHA.

The ready-to-copy [`templates/pr-agent-advisory.yml`](templates/pr-agent-advisory.yml) keeps PR-Agent cloud-only and advisory. It has no checkout, shell, content-write, approval, autofix, or merge capability. It also disables comment commands, repository-controlled settings, skills, and artifacts. Install it only after adding a `PR_AGENT_OPENAI_KEY` Actions secret to the target repository.

### 4. Cursor Bugbot or Graphite Agent — only if already using the platform

- [Cursor Bugbot](https://prod.cursor.com/docs/bugbot) reviews bugs, security, and quality and accepts repository-specific `.cursor/BUGBOT.md` rules. It has separate/usage-based billing, so it is not compelling unless Cursor is already the team's main environment.
- [Graphite AI Reviews](https://www.graphite.com/docs/ai-reviews) are most useful when the team already wants Graphite's stacked-PR and merge workflow. Limited AI review exists on the free tier; unlimited review is part of its paid team offering.

## Useful X-discovered review skills

- [`code-review-and-quality`](https://www.skills.sh/addyosmani/agent-skills/code-review-and-quality) — strongest general review workflow; preferred.
- [`skill-security`](https://github.com/superagent-ai/skills/blob/main/skills/skill-security/SKILL.md) — offline static scanner plus semantic inspection for auditing agent skills before installation. Use before trusting future community skills.
- [`code-review-excellence`](https://github.com/wshobson/agents/blob/main/plugins/developer-essentials/skills/code-review-excellence/SKILL.md) — disciplined human-style review checklist, but overlaps the preferred Addy Osmani skill.
- [`frontend-code-review`](https://www.skills.sh/langgenius/dify/frontend-code-review) and [`typescript-review`](https://www.skills.sh/aiagentskills/skills/typescript-review) — useful specialists, but overlap the existing Vercel React/Next.js skills.
- [`simplify`](https://www.skills.sh/ahgraber/skills/simplify) — useful after correctness review; never treat fewer lines as proof of better code.

Source roundup: [the seven-skill X post](https://x.com/Soumyapx/status/2091981349980983343).

## Project-specific rollout

- `imtisaal-portfolio`: run a local report-only comparison first. ESLint passes, but standalone TypeScript currently needs its Cloudflare ambient-type baseline fixed before it can be a hard gate.
- `icd-10-mapping-reference-tool`: best first clean GitHub pilot, but medical context means every finding must be manually verified and bulk autofix stays disabled.
- `lab-zero-hub`: postpone. It already has a pinned `raye-deng/open-code-review` workflow and currently has a noisy lint baseline; its project instructions also prohibit adding third-party bots without explicit authorization.
- Live or dirty worktrees: no automatic reviewer installation until current changes are isolated and the baseline is green.

## Security requirements

Automated review agents must treat repository text as untrusted data. The [AI Now Institute's Friendly Fire research](https://ainowinstitute.org/publications/friendly-fire-policy-brief) demonstrates that instructions planted in repository files can manipulate coding agents into executing attacker-controlled code.

For every PR agent:

- Start in advisory mode.
- Pin actions by full commit SHA.
- Prefer `pull_request` for same-repository PRs. Use `pull_request_target` for fork reviews only when the job never checks out or executes PR-controlled code.
- Grant only repository read and PR-comment permissions.
- Disable autofix, auto-commit, and auto-merge during evaluation.
- Run untrusted pull requests in an isolated cloud runner without production secrets.
- Measure accepted findings, false positives, review cost, and escaped defects before expanding rollout.

Repository text can still manipulate an AI review. Keep at least one human approval required, leave “Allow GitHub Actions to create and approve pull requests” off, and never make the AI comment itself a required merge gate.

## Browser versus X API

Browser/computer use was the better choice for this one-off search because the existing signed-in session exposed current posts, full threads, engagement, and outbound links without developer setup. X results were valuable for discovery but included vendor promotion and anecdotes, so every recommendation was checked against an official source.

Use the X API only for a recurring trend monitor or a large reproducible dataset. It would provide structured pagination and metrics but requires a developer project, credentials, rate-limit handling, and ongoing storage. It is unnecessary for an occasional curated scan.
