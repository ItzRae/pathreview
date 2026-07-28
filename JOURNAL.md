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