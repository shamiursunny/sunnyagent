# S07 - ProgramBench usage page

**SOURCE:** ProgramBench usage page

**URL:** https://mini-swe-agent.com/latest/usage/programbench/

**ACCESS STATUS:** ACCESSIBLE, READ IN FULL.

**REPOSITORY/PATH:** Docs page; config shown inline; benchmark repo referenced: github.com/facebookresearch/programbench (NOT inspected)

**LICENSE:** Page: none stated. mini-swe-agent repo is MIT. ProgramBench license NOT CHECKED

**LICENSE STATUS:** Page: none stated. mini-swe-agent repo is MIT. ProgramBench license NOT CHECKED - LICENSE UNVERIFIED - DO NOT COPY.

**RELEVANT FILES:** n/a

**RELEVANT CODE:** Config shows containers run with --network none; step_limit 1000; wall_time 21600s; wrap-up warnings when <20 steps or <10 min remain

**RELEVANT ARCHITECTURE:** Reverse-engineering benchmark; scoring by hidden tests on rebuilt executable; anti-shortcut prompt rules (no wrapping the reference binary, no decompiling)

**RELEVANT IDEAS:** Anti-shortcut rules; wrap-up warnings; trajectory + submission.tar.gz output layout

**DIRECT REUSE CANDIDATE:** NO

**REFERENCE-ONLY MATERIAL:** YES

**COMPATIBILITY CONCERNS:** Different task type (rebuild a binary) than competition (patch issues)

**SECURITY CONCERNS:** n/a

**KAGGLE RELEVANCE:** LOW: methodology only (anti-shortcut, wrap-up warning).

