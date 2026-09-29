```
BASELINE -> LOCALIZE -> HYPOTHESIZE -> PATCH -> VALIDATE
VALIDATE --pass--> FINAL_REVIEW -> SUBMIT/COMPLETE
VALIDATE --fail--> CLASSIFY
CLASSIFY --same root cause--> REVISE (<= N per hypothesis) -> PATCH
CLASSIFY --new root cause--> REPLAN (<= M) -> LOCALIZE
limits exhausted -> submit best validated patch or stop (BLOCKED/FAILED)
Every transition records: reason, evidence, step number. Identical action + identical observation twice => forced hypothesis change.
```
