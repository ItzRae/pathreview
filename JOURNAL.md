## Week 7 — Issue selection

**Issue link:** https://github.com/ascherj/pathreview/issues/11

**Issue title:** Add support for ingesting a portfolio website URL

**Tier:** [ ] Tier 1  [x] Tier 2  [ ] Tier 3

**Problem summary:**
Right now PathReview can use GitHub and resume data, but it cannot pull information from a user’s personal portfolio website. That means project descriptions, bios, and other useful context on a portfolio site are currently left out of the review. This issue would add a web parser that fetches and extracts relevant text from a submitted URL, then passes that content through the existing ingestion pipeline. A successful fix would store that portfolio content in the vector store alongside the user’s other profile data.

**Branch name:** feat/11-portfolio-url-ingestion

**Setup confirmation:** [x] App runs locally at localhost:5173

**Cohort ledger:** [x] Issue added to cohort ledger