# Agent Configuration Upgrade: Spec-Driven Slice-by-Slice Workflow
> **Live State**: Phase 6 — Delivery & Commits — Ready to Commit
Level: 2 · Spec: N/A (Level 2 config task) · Approved: 2026-10-01

## Requirements
| REQ | Requirement | Acceptance criteria |
|---|---|---|
| REQ-001 | Remove waterfall-sdlc legacy remnants | Given legacy waterfall-sdlc skill and references in AGENTS.md, when purged via git rm and edited, then 0 references to waterfall-sdlc or formal gates remain in AGENTS.md. |
| REQ-002 | Update Section 3 (Level table & skill intents) | Given Section 3 of AGENTS.md, when updated, then Level 2/2.5/3 rows include `/plan, /build, /preview`, Level 4 links wayfinder, domain-modeling & wayfinder intents match spec, and waterfall-sdlc intent is deleted. |
| REQ-003 | Update Section 4 with 6-phase slice loop & skeleton | Given Section 4 of AGENTS.md, when updated, then the 5-phase lifecycle is replaced by the 6-phase slice loop, state engine rules include slice commit rules and docs/DECISIONS.md replacement, and the PLAN.md skeleton is embedded. |
| REQ-004 | Update Section 8 Workflows table | Given Section 8 of AGENTS.md, when updated, then the table contains exactly the 9 workflows (`/plan`, `/build`, `/preview`, `/design`, `/review`, `/commit`, `/wayfinder`, `/to-spec`, `/to-tickets`) with 1-line purposes. |
| REQ-005 | Add Section 9 Design Discipline verbatim | Given AGENTS.md, when Section 9 is added, then all 9 design discipline rules (Language, Decisions, Never answer for the user, Highest seam, Vertical slices, Expand-contract, Change control, Fix loop, Minimal CI) are present verbatim. |
| REQ-006 | Create plan, build, and preview workflows | Given `.agents/workflows/`, when created, then `plan.md`, `build.md`, and `preview.md` exist with valid YAML frontmatter (`---` + 1-line `description:`) and detailed numbered steps matching specifications. |
| REQ-007 | Align commit workflow | Given `.agents/workflows/commit.md`, when edited, then its final step checks all REQs in PLAN.md are user-accepted and REVIEW.md verdict is not "Request changes" before offering push. |
| REQ-008 | Verification & zero-stale reference audit | Given all modified and created files, when validated, then all frontmatter starts with `---` + 1-line description, 0 stale references (`waterfall`, `claude-mem`, `/compact`, `file:///`, `whitespace-nowrap`, `plugin.json`) exist in config, and all relative links resolve. |

## Slices
### Slice 1 — Remove Waterfall SDLC & Clean References (REQ-001)
- [x] A1: Remove waterfall-sdlc skill folder (`.agents/skills/waterfall-sdlc` / `skills/waterfall-sdlc`) via `git rm -r`
- [x] A2: Remove every reference to `waterfall-sdlc` and "formal gates" from `AGENTS.md`
- [x] Preview checkpoint (Config diff inspection)

### Slice 2 — AGENTS.md Core Upgrades (REQ-002, REQ-003, REQ-004, REQ-005)
- [x] B1: Update Section 3 Level table (Levels 2, 2.5, 3, 4) and rewrite/remove skill intents
- [x] B2: Replace 5-Phase lifecycle with 6-Phase slice loop and update state engine rules (local slice commits, docs/DECISIONS.md)
- [x] B3: Add the PLAN.md skeleton to Section 4
- [x] B4: Update Section 8 Workflows table to final 9-workflow list
- [x] B5: Add Section 9 Design Discipline verbatim
- [x] Preview checkpoint (AGENTS.md structural inspection)

### Slice 3 — Workflow Definitions & Alignment (REQ-006, REQ-007)
- [x] C1: Create `.agents/workflows/plan.md` with YAML frontmatter and 8 steps
- [x] C2: Create `.agents/workflows/build.md` with YAML frontmatter and 8 steps
- [x] C3: Create `.agents/workflows/preview.md` with YAML frontmatter and 8 steps
- [x] D: Update `.agents/workflows/commit.md` final step to verify PLAN.md REQ acceptance and review verdict
- [x] Preview checkpoint (Workflow syntax & step inspection)

### Slice 4 — Verification & Delivery Audit (REQ-008)
- [x] E1: Verify frontmatter (`head -4`) across `.agents/skills/*/SKILL.md` and `.agents/workflows/*.md`
- [x] E2: Run grep check across config (`AGENTS.md`, `.agents/`) for forbidden strings (`waterfall`, `claude-mem`, `/compact`, `file:///`, `whitespace-nowrap`, `plugin.json`)
- [x] E3: Verify all relative markdown links in `AGENTS.md` resolve to existing targets
- [x] E4: Generate verification summary report for user review

## Acceptance
| REQ | AI verified (evidence) | User accepted |
|---|---|---|
| REQ-001 | ✅ Verified (git rm skills/waterfall-sdlc, 0 occurrences in AGENTS.md) | ✅ |
| REQ-002 | ✅ Verified (AGENTS.md Section 3 Level table updated with workflows, wayfinder map link, intents rewritten) | ✅ |
| REQ-003 | ✅ Verified (AGENTS.md Section 4 updated with 6-phase slice loop, rule 4, PLAN.md skeleton) | ✅ |
| REQ-004 | ✅ Verified (AGENTS.md Section 8 table updated with all 9 workflows) | ✅ |
| REQ-005 | ✅ Verified (AGENTS.md Section 9 Design Discipline added verbatim) | ✅ |
| REQ-006 | ✅ Verified (Created plan.md, build.md, preview.md in .agents/workflows/ with valid frontmatter) | ✅ |
| REQ-007 | ✅ Verified (Updated .agents/workflows/commit.md step 10 with REQ acceptance & review check) | ✅ |
| REQ-008 | ✅ Verified (All 7 config files head -4 verified, stale references grepped, links checked) | ✅ |

## Change log
- 2026-10-01 — Initial plan drafted and approved by user
- 2026-10-01 — Executed Slice 1 (waterfall-sdlc removal), Slice 2 (AGENTS.md overhaul), Slice 3 (workflows creation & commit alignment), and Slice 4 (verification suite)
- 2026-10-01 — User accepted all REQs and approved commit to main
