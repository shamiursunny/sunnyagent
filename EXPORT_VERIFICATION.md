# EXPORT_VERIFICATION

Date: 2026-09-29. Checks run by the export agent on the local export directory.

| Check | Result |
|---|---|
| Required documents present (19) | PASS |
| Required dirs sources/ source-code/ architecture/ experiments/ manifests/ | PASS |
| JSON files parse | PASS |
| 12 copied source files byte-identical to clones | PASS |
| Each source-code repo dir contains its LICENSE | PASS |
| Secret-pattern scan | PASS (0 hits) |
| Unsupported-claim phrase grep in authored docs | REVIEW [('V5.5_IMPLEMENTATION_PLAN.md', 14, '| ST11 | Kaggle submit | user go-ahead | official result recorded; "Kaggle SUCCESS" only i')] |

Note on the REVIEW line: the only hit is the text of a rule in V5.5_IMPLEMENTATION_PLAN.md ('Kaggle SUCCESS' only if Kaggle reports it); it is not a claim. Reviewed manually: OK.

## Not verifiable / not done (honest limits)
- V0.5 unchanged: the export agent never had read or write access to the implementation repo and executed no push or write commands against any remote (only `git clone`/`git ls-remote` read operations on public repos). It cannot assert the V0.5 branch state. NOT VERIFIED.
- Export has NOT been uploaded to gemma4-v5.5-research (that repo was not readable/writable from here).
- License verification = LICENSE files read in clones; NOTICE files and per-file headers not checked. Licenses of papers, minimal-agent.com, ProgramBench, and the organizer mirror NOT established (marked DO NOT COPY).
- No exported code was executed or tested.
- Kaggle claims: excerpt-level (search-engine text of the competition page) plus a third-party mirror; the official HARNESS_README, rules and dataset were not read. No Kaggle compatibility is claimed for anything.
- No benchmark was executed.
- The manifest excludes itself (EXPORT_MANIFEST.json) to avoid a self-referential hash; its own SHA256 is reported in the final response and inside the ZIP hash.
