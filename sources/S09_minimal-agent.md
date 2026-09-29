# S09 - minimal-agent tutorial

**SOURCE:** minimal-agent tutorial

**URL:** https://minimal-agent.com/#environment-variables

**ACCESS STATUS:** ACCESSIBLE, READ IN FULL.

**REPOSITORY/PATH:** Site; source repo swe-agent/minimal-agent-tutorial (NOT inspected)

**LICENSE:** Page states none; repo license NOT CHECKED

**LICENSE STATUS:** Page states none; repo license NOT CHECKED - LICENSE UNVERIFIED - DO NOT COPY.

**RELEVANT FILES:** n/a

**RELEVANT CODE:** Tutorial code: query_lm/parse_action/execute_action, exception->message loop, format-error retries, env vars PAGER=cat MANPAGER=cat LESS=-R PIP_PROGRESS_BAR=off TQDM_DISABLE=1

**RELEVANT ARCHITECTURE:** ~50-line loop; every action independent subprocess

**RELEVANT IDEAS:** Feed timeouts/format errors back to the model; disable interactive tools via env vars

**DIRECT REUSE CANDIDATE:** NO (env-var list is a fact, not copyrightable code; cite anyway)

**REFERENCE-ONLY MATERIAL:** YES

**COMPATIBILITY CONCERNS:** None

**SECURITY CONCERNS:** shell=True note in tutorial

**KAGGLE RELEVANCE:** LOW: personal-agent design.

