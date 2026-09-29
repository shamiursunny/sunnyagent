# S02 - gemma-coder

**SOURCE:** gemma-coder

**URL:** https://github.com/shamiursunny/gemma-coder

**ACCESS STATUS:** ACCESSIBLE (cloned, HEAD df87084). gemma_coder.py (412 lines) READ IN FULL; README and docs/benchmark-evidence.md read.

**REPOSITORY/PATH:** shamiursunny/gemma-coder (main): gemma_coder.py, README.md, docs/benchmark-evidence.md, LICENSE

**LICENSE:** MIT, Copyright (c) 2026 sisyphusse1-ops

**LICENSE STATUS:** MIT, Copyright (c) 2026 sisyphusse1-ops - LICENSE read (FACT)

**RELEVANT FILES:** gemma_coder.py; README.md; docs/benchmark-evidence.md

**RELEVANT CODE:** XML-framed JSON tool protocol (<tool>{...}</tool>), tools read_file/write_file/search/run/patch/done, MAX_ITER=12, patch() rejects non-unique 'old' strings, OpenRouter/Ollama clients

**RELEVANT ARCHITECTURE:** Single-file loop; one tool call per reply; rulebook (CLAUDE.md) injected each turn

**RELEVANT IDEAS:** Unique-match patch guard; explicit done(summary) termination; iteration cap

**DIRECT REUSE CANDIDATE:** ADAPT (small pieces only, personal agent). Full file copied to source-code/gemma-coder/ for reference.

**REFERENCE-ONLY MATERIAL:** README benchmark table (informal, not reproduced; UNVERIFIED); benchmark-evidence.md (one task shown)

**COMPATIBILITY CONCERNS:** README claims 'path safety' but code has none: Path(path) used directly, no workspace confinement (FACT, from code). run() uses shell=True. README says Gemma 4 lacks native function calling; the mirrored harness config uses a 'gemma4' tool-call parser (SOURCE-DERIVED, secondary) - CONTRADICTION, unresolved.

**SECURITY CONCERNS:** HIGH if copied as-is: arbitrary file read/write and shell; must be wrapped in a confined environment.

**KAGGLE RELEVANCE:** LOW: cannot be shipped (competition forbids Python entrypoints). Ideas only, via prompts.

