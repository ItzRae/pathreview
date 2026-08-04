## Week 7 — Issue selection

**Issue link:** https://github.com/ascherj/pathreview/issues/11

**Issue title:** Add support for ingesting a portfolio website URL

**Tier:** [ ] Tier 1  [x] Tier 2  [ ] Tier 3

**Problem summary:**
Right now PathReview can use GitHub and resume data, but it cannot pull information from a user’s personal portfolio website. That means project descriptions, bios, and other useful context on a portfolio site are currently left out of the review. This issue would add a web parser that fetches and extracts relevant text from a submitted URL, then passes that content through the existing ingestion pipeline. A successful fix would store that portfolio content in the vector store alongside the user’s other profile data.

**Branch name:** feat/11-portfolio-url-ingestion

**Setup confirmation:** [x] App runs locally at localhost:5173

**Cohort ledger:** [x] Issue added to cohort ledger

## Week 8 — Reproduction & solution planning

**Reproduction commit link:** https://github.com/ItzRae/pathreview/commit/103ecae18838f6b23b87fa79f2afad92ee71201a

**Reproduction summary:**
I created a profile and confirmed that the app already lets users enter a portfolio URL. However, after tracing the ingestion code, I found that the URL is only stored on the profile and is never fetched or processed. The pipeline currently supports resumes, READMEs, and repository metadata, but there is no web parser or portfolio ingestion flow to add website content to the vector store.

**PLAN.md link:** https://github.com/ItzRae/pathreview/blob/feat/11-portfolio-url-ingestion/PLAN.md

**Blockers or open questions:** None at the moment. My remaining work is primarily implementation and tracing the existing ingestion flow to determine the correct integration point.

## Week 9 — Solution building & PR submission

### Check-in 1 (mid-week)

**Current progress:**
Implemented the core portfolio website ingestion feature. I added a new `WebParser` to extract readable text and metadata from HTML pages, integrated a new `ingest_portfolio()` method into the ingestion pipeline, and added unit tests for both the parser and pipeline. I also verified the implementation by reproducing the issue locally and comparing it with the existing ingestion architecture.

**Next steps:**
Run final project checks, open a draft PR for feedback, address any review comments, and prepare the PR for final submission.

**Blockers:**
No major blockers. While tracing the codebase, I found that the existing resume and README ingestion methods are not currently wired into an application-level workflow either, so I began drafting my PR to ask/confirm whether that integration is expected as part of this issue.

---

### Check-in 2 (end of week)

**PR link:** https://github.com/ascherj/pathreview/pull/783

**Branch:** `feat/11-portfolio-url-ingestion`

**What you built:**
Implemented support for ingesting portfolio websites into the existing ingestion pipeline. The new `WebParser` extracts readable content and metadata from HTML pages, and `ingest_portfolio()` fetches portfolio pages, processes them through the existing chunking and embedding workflow, and stores the resulting content with portfolio-specific metadata.

**Tests added or updated:**
- `tests/unit/test_web_parser.py` — verifies HTML parsing, metadata extraction, ignored elements, and invalid input handling.
- `tests/unit/test_ingestion_pipeline.py` — verifies successful portfolio ingestion, metadata propagation, invalid URLs, empty pages, duplicate sources, and request failures.

**Self-review confirmation:**
- [x] make check passes (no new failures introduced beyond documented pre-existing mypy issues)
- [x] make test-unit passes

**Draft PR feedback received from:**
None (awaiting feedback)