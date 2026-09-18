# Twitter bookmark harvest

Curated on 2026-09-17 from the complete visible X bookmark history, from the newest saves back to the oldest item shown (2020).

The goal is to turn durable bookmarks into useful project inputs without bulk-installing untrusted code. Links were checked against official repositories or product documentation where practical.

## Agent access

This repository is the git mirror for Codex, Claude, and other coding agents. It includes the full 250-bookmark export, not only the curated selections below.

- `data/catalog.json` — complete machine-readable catalog, priority queue, and manually shared items.
- `data/all-bookmarks.csv` — one row per captured bookmark.
- `data/priority-queue.csv` — 143 bookmarks with a concrete install, reference, research, or project action.
- `data/twitter-bookmarks-complete.xlsx` — unchanged export of the authoritative Google Sheet.
- `AGENTS.md` and `CLAUDE.md` — safe-use and refresh instructions.
- `sources.lock.json` — pinned revisions for code repositories inspected during the audit.

The source Sheet remains available in [Google Drive](https://docs.google.com/spreadsheets/d/129a0kNYoIIGTySJiPQkzAw_-CVQ8VFlV3QU6FHlIXh0/edit), but nothing in this repository requires Drive access.

## Downloaded and installed

| Resource | Local path | Best fit | Status |
| --- | --- | --- | --- |
| Jev Ultrafast | `/Users/imtisaalmian/jev-ultrafast` | Browser-agent experiments; `lab-zero-hub` research | Installed in an isolated `uv` environment; 31 tests, Ruff, JavaScript syntax checks, and package build passed. Requires TypeSafe and text-model API keys before live use. |
| Wafer GPU Performance Engineering Resources | `repos/gpu-perf-engineering-resources` | `semantic-photo-search`, `Zero2Hero-JuliaWorkshop`, `monte-carlo-option-pricing` | Shallow-cloned. Reference material only; the upstream repository currently has no declared license, so do not redistribute its contents. |
| ADHD-friendly response skill | `~/.codex/skills/i-have-adhd` | Optional focused, action-first Codex responses | Skill files installed. Invoke only when wanted; it was not enabled globally. |
| Anti-slop installer skill | `~/.codex/skills/install-anti-slop` | TypeScript/JavaScript projects | Installer skill only. No lint rules or packages were added to any project. Apply later in an isolated branch because its rules are intentionally opinionated. |
| Goose Graphics skill | `~/.codex/skills/goose-graphics` | Social graphics, carousels, posters, and visual explainers | Skill files installed. Browser/render dependencies were not installed, and no login, publishing, or paid API action was run. |
| Remotion core skills | `~/.codex/skills/remotion-*` | Programmatic video, captions, multimedia, and rendering | Installed the official `best-practices`, `create`, `markup`, `interactivity`, `captions`, `multimedia`, and `render` skill files. The companion skills keep `remotion-create` cross-links intact. No Remotion app or heavyweight render dependencies were added. |

Large repositories were not cloned because this Mac had less than 1 GB of free disk space during the harvest. Their verified links and intended uses are preserved below.

## Use now

### Funding deadline: September 18, 2026

The Canadian Women’s Economic and Leadership Opportunities Fund closes at **12:00 noon Pacific / 3:00 p.m. Toronto on September 18, 2026**. Lab Zero may be a fit only if the applicant is a legally constituted Canadian nonprofit with relevant women’s-equality experience.

- [Official call](https://www.canada.ca/en/women-gender-equality/funding/funding-opportunities/advancing-leadership/about.html)
- [Eligibility](https://www.canada.ca/en/women-gender-equality/funding/funding-opportunities/advancing-leadership/eligibility.html)
- [Application instructions](https://www.canada.ca/en/women-gender-equality/funding/funding-opportunities/advancing-leadership/apply.html)
- Maximum funding: $625,000 local, $1 million regional, or $1.4 million pan-Canadian.
- Do not start an application until legal status, prior equality work, project scope, and the one-application limit are confirmed.

### Reusable engineering references

- [How complex systems fail](https://how.complexsystems.fail/) — concise resilience principles for `Lab-Zero-Primer`, `lab-zero-hub`, `elevate-studio`, and `lab-zero-outreach`.
- [Sid Bharath’s AI Coding Best Practices](https://sidbharath.com/blog/mastering-ai-coding-the-universal-playbook-of-tips-tricks-and-patterns/) — planning, small reviewable changes, living docs, testing, branches, and human review.
- [Jane Street: I design with Claude more than Figma now](https://blog.janestreet.com/i-design-with-claude-code-more-than-figma-now-index/) — use disposable working prototypes as living design proposals, then validate before productionizing.
- [Vercel Labs vgpu](https://github.com/vercel-labs/vgpu) — MIT-licensed WebGPU library for shaders, math visualization, GPU tensors, and neural networks. Candidate for future visual experiments, not an immediate dependency.
- [Public APIs](https://github.com/public-apis/public-apis) — consult when a project needs a new data source; do not bulk-integrate APIs without reviewing terms, provenance, privacy, and uptime.
- [BackSearch](https://www.gr.inc/backsearch) — point-in-time search for reproducible historical evaluation. Paid usage; integrate only when an evidence cutoff is a real product requirement.

## Project map

| Project | High-value bookmark inputs | Recommended use |
| --- | --- | --- |
| `lab-zero-hub` | [Voice UI collection](https://www.mobbin.com/collections/d9129e4b-afa4-4c7b-8e31-b26edbaa858f/mobile/screens?via=rachel&referrer_creator_id=19356198-8b7a-4072-bcbf-c6955b61517f), [How complex systems fail](https://how.complexsystems.fail/), Jev Ultrafast | Reference listening, transcription, interruption, and error states; strengthen episode recovery and bounded-agent evaluation. Do not copy proprietary screenshots or add speculative services. |
| `Lab-Zero-Primer` | [How complex systems fail](https://how.complexsystems.fail/), [AI coding playbook](https://sidbharath.com/blog/mastering-ai-coding-the-universal-playbook-of-tips-tricks-and-patterns/), [Jane Street prototype workflow](https://blog.janestreet.com/i-design-with-claude-code-more-than-figma-now-index/) | Use as review/evaluation heuristics for deterministic mastery, RLS, invitations, and instructor evidence flows. |
| `elevate-studio` | [Voice UI collection](https://www.mobbin.com/collections/d9129e4b-afa4-4c7b-8e31-b26edbaa858f/mobile/screens?via=rachel&referrer_creator_id=19356198-8b7a-4072-bcbf-c6955b61517f), [Melies cinematic techniques](https://melies.co/cinematic-techniques), [Landing Love](https://www.landing.love/) | Improve multimodal listening states, workshop motion, sponsor demos, and short explainers. Use references, not copied assets. |
| `semantic-photo-search` | Local Wafer GPU resources, [vgpu](https://github.com/vercel-labs/vgpu), [Vercel WebGPU testing notes](https://github.com/vercel-labs/agent-browser/blob/main/skill-data/core/references/webgpu.md) | Profile CLIP/ONNX/WASM and worker memory first; consider WebGPU only behind measured feature detection and fallbacks. |
| `minimal-embodiment` | Existing upstream build guide, [Andon Labs embodied-agent evaluation](https://x.com/andonlabs/status/2080691090328584222) | Preserve the current dirty worktree. Use the evaluation idea for repeatable sensor/actuator tasks; no extra framework was added. |
| `Zero2Hero-JuliaWorkshop` | [Math-To-Manim](https://github.com/HarleyCoops/Math-To-Manim), local Wafer GPU resources | Use selected animations or offline explainers as teaching supplements. Do not vendor the large repository into the upstream-tracking workshop. |
| `monte-carlo-option-pricing` | [Math-To-Manim](https://github.com/HarleyCoops/Math-To-Manim), local Wafer GPU resources | Potential visual explanation of paths, confidence intervals, and variance reduction; profile before adding acceleration. |
| `icd-10-mapping-reference-tool` | [Rare-disease agent challenge context](https://x.com/danielmckinn0n/status/2092348534825906646), [How complex systems fail](https://how.complexsystems.fail/) | Inspiration for explicit evidence and benchmark design only. Never let an agent silently recode or diagnose. |
| `lab-zero-website` | [Curated Design](https://curated.design/), [Landing Love](https://www.landing.love/), [Saaspo](https://saaspo.com/), [Navbar Gallery](https://www.navbar.gallery/), [CTA Gallery](https://www.cta.gallery/), [Melies](https://melies.co/cinematic-techniques) | Landing-page structure, navigation, calls to action, and motion references. Maintain accessibility, performance, bilingual routes, legal flows, and checkout safety. |
| `imtisaal-portfolio` | [Grace Wang portfolio](https://gracewang.design/), [Farza Figma deck](https://www.figma.com/file/kWVJ3L2eQkNwxUjW4Meaj2/template_deck?type=design&node-id=0%3A3&mode=design), [Curated Design](https://curated.design/) | Interaction and case-study storytelling references. The Figma file is public-view but has no declared license: duplicate for internal reference only. |
| `lab-zero-outreach` | [Twenty CRM](https://github.com/twentyhq/twenty), [First Round sales program](https://www.firstround.com/sales-combine) | Product-pattern references only. Keep the existing HubSpot/SQLite/SMTP pipeline; do not connect third-party autonomous outreach agents or trigger sends from bookmark code. |

## Large source repositories saved but not cloned

- [Shubhamsaboo/awesome-llm-apps](https://github.com/Shubhamsaboo/awesome-llm-apps) — Apache-2.0 pattern library with many independent demos. It is large and has heterogeneous dependencies/API-key requirements; select one example at a time into an isolated environment.
- [HarleyCoops/Math-To-Manim](https://github.com/HarleyCoops/Math-To-Manim) — visual math/physics explainer pipeline. Useful for education and finance demos, but rendering dependencies and media make it unsuitable for the remaining disk budget.
- [chaitanyagiri/munder-difflin](https://github.com/chaitanyagiri/munder-difflin) — MIT local multi-agent office. Early prototype with broad project read/write and agent-CLI execution; trial only in a disposable directory, not against important repos.
- [vercel-labs/vgpu](https://github.com/vercel-labs/vgpu) — use as a package or study selected examples when a measured WebGPU need emerges.

## Design, motion, and video library

- [Melies Cinematic Techniques](https://melies.co/cinematic-techniques) — 424 camera, framing, lighting, editing, and genre techniques.
- [Curated Design](https://curated.design/) — general live-site inspiration.
- [Landing Love](https://www.landing.love/) — motion-focused landing-page recordings.
- [Saaspo](https://saaspo.com/) — SaaS page structure.
- [Navbar Gallery](https://www.navbar.gallery/) and [CTA Gallery](https://www.cta.gallery/) — focused pattern libraries.
- [60fps apps](https://60fps.design/apps) — live alternative to the dead `appmotion.design` bookmark.
- [Runway Ruby HDR guide](https://help.runwayml.com/hc/en-us/articles/creating-hdr-videos-with-runway-ruby) — reference only; requires Runway and is relevant when HDR delivery is actually requested.
- [Farza Figma template deck](https://www.figma.com/file/kWVJ3L2eQkNwxUjW4Meaj2/template_deck?type=design&node-id=0%3A3&mode=design) — internal layout reference; no declared reuse license.

## Advanced learning

- [Qwen-2.5-1B-RLCD model](https://huggingface.co/harshatheg/Qwen-2.5-1B-RLCD) and [parallel constrained-decoding demo](https://huggingface.co/spaces/drinkmoonshine/parallel-constrained-decoding) — this is the resource from the specifically shared X post. Use the hosted demo: its fast local MLX path targets Apple Silicon, while the PyTorch CPU fallback would be slow and consume several gigabytes on this Intel Mac.
- [Jane Street: positional encodings through group theory](https://blog.janestreet.com/using-group-theory-to-explore-positional-encodings-attention/)
- [Jane Street neural-network reverse-engineering puzzle](https://blog.janestreet.com/can-you-reverse-engineer-our-neural-network/)
- [Jane Street: visualizing piecewise-linear neural networks](https://blog.janestreet.com/visualizing-piecewise-linear-neural-networks/)
- [How LLMs Really Do Arithmetic](https://arxiv.org/abs/2601.15714)
- [Roadmap.sh AI Engineer](https://roadmap.sh/ai-engineer)
- [A Gentle Introduction to the Art of Mathematics](https://osj1961.github.io/giam/)

## Opportunities saved for manual review

- [WAGE Women’s Economic and Leadership Opportunities Fund](https://www.canada.ca/en/women-gender-equality/funding/funding-opportunities/advancing-leadership/about.html) — urgent; deadline above.
- [First Round Sales Combine](https://www.firstround.com/sales-combine) — November 6–7, 2026 in San Francisco; career-placement program, not a Lab Zero funding resource.
- [Supabase careers](https://supabase.com/careers)
- [Microsoft for Startups](https://www.microsoft.com/en-us/startups), [AWS Activate](https://aws.amazon.com/startups/credits), and [Google for Startups Cloud](https://cloud.google.com/startup/benefits) — apply only when the chosen cloud matches a real deployment plan. Google’s program excludes nonprofits, agencies, consultancies, and dev shops.

## Skipped on purpose

- Temporary `trycloudflare.com` downloads and anonymous “free skill” endpoints: unverifiable and unsafe.
- TikTok private/mobile API scraping: legal, account, rate-limit, and platform-policy risk.
- Watermark-removal tools and unverified “uncensored” model weights: not needed for current projects and introduce provenance/safety risks.
- Autonomous sales services (`Explee`, `Okara`, similar): overlap the live outreach pipeline and could transmit contact data or send messages.
- Deprecated IcePanel MCP repository: the current hosted MCP requires a paid IcePanel account; write access can mutate or delete architecture objects.
- `appmotion.design`: dead link; replaced above with a current alternative.
- Medical claims and anecdotal treatment bookmarks: excluded from project inputs.
