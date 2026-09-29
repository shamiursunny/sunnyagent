# S05 - MemGovern paper (arXiv 2601.06789v2)

**SOURCE:** MemGovern paper (arXiv 2601.06789v2)

**URL:** https://arxiv.org/html/2601.06789v2

**ACCESS STATUS:** ACCESSIBLE, READ IN FULL via fetch.

**REPOSITORY/PATH:** arXiv HTML; code repo referenced: github.com/QuantaAlpha/MemGovern (NOT inspected)

**LICENSE:** Paper license NOT CHECKED. LICENSE UNVERIFIED

**LICENSE STATUS:** Paper license NOT CHECKED. LICENSE UNVERIFIED - DO NOT COPY text/figures.

**RELEVANT FILES:** n/a

**RELEVANT CODE:** n/a (repo not inspected)

**RELEVANT ARCHITECTURE:** Experience Governance -> experience cards (Index layer + Resolution layer); Agentic experience search = Searching (top-k) + Browsing; built on SWE-agent

**RELEVANT IDEAS:** Card schema fields: Problem Summary, Signals(10-18), Root Cause, Fix Strategy, Patch Digest, Verification. Search-then-browse beat single-shot RAG in their ablation. Reported +4.65% avg on SWE-bench Verified with 135K cards (paper claim; NOT reproduced).

**DIRECT REUSE CANDIDATE:** NO

**REFERENCE-ONLY MATERIAL:** YES - schema and method as ideas

**COMPATIBILITY CONCERNS:** Their 135K-card corpus, embeddings and search tool do not exist in the offline sandbox (INFERENCE). Cards from public GitHub issue/PR data may overlap hidden held-out tasks (INFERENCE; competition rule UNKNOWN).

**SECURITY CONCERNS:** n/a

**KAGGLE RELEVANCE:** MEDIUM: ideas only; must be re-implemented as static markdown cards + offline skill script, size-bounded by 32k context.

