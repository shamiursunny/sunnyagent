# V5.5_EXPORT - Gemma 4 Developer Agent competition, V5.5 research package

Purpose: let another AI understand, audit and continue the V5.5 project without the originating conversation. Nothing here is implemented software; nothing was submitted to Kaggle; V0.5 was never accessed or modified.

## Read order
1. PROJECT_STATE.md + PROJECT_STATE.json (state; note the WARNING: implementation repo was unreadable)
2. DECISION_LOG.md (open decisions OD-1..OD-5 need the user)
3. KAGGLE_SPECIFICATION.md (labels: OFFICIAL-EXCERPT vs SOURCE-DERIVED secondary)
4. V5.5_RESEARCH_AND_ARCHITECTURE_PLAN.md -> ARCHITECTURE.md and design docs
5. SOURCE_INDEX.md, SOURCE_REUSE_MATRIX.md, SECURITY_AND_LICENSE_AUDIT.md
6. EXPERIMENT_PLAN.md, V5.5_IMPLEMENTATION_PLAN.md, RISKS_AND_UNKNOWNS.md
7. EXPORT_VERIFICATION.md, EXPORT_MANIFEST.json

## Headline findings
- The competition submission is a declarative ADK-style config zip (agent.yaml at root); a mirror of the organizer docs says Python entrypoints are not accepted, network is off, context is 32,768 tokens. So the personal Python agent cannot be the Kaggle artifact; share the POLICY core instead (OD-1).
- The V0.5 baseline and project history are UNKNOWN to this package.
- gemma-coder has no path confinement despite its README (verified from code).

## Continuity command
"Read gemma4-kaggle/PROJECT_STATE.md from my GitHub repository and continue the Gemma 4 competition project from the first incomplete stage." - interpretation steps are in PROJECT_STATE.md (section at bottom) and architecture/CONTINUITY_AND_AUTOSAVE.md.

## Directory
sources/ (22 audit records + inventory/), source-code/ (verbatim licensed copies with LICENSE files; see ORIGIN.md), architecture/, experiments/, manifests/.
