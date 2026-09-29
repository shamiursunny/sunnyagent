# S06 - mini-swe-agent

**SOURCE:** mini-swe-agent

**URL:** https://github.com/shamiursunny/mini-swe-agent

**ACCESS STATUS:** ACCESSIBLE (cloned, HEAD 04d809c). agents/default.py READ IN FULL; README read; environments/local.py copied (not analysed in depth).

**REPOSITORY/PATH:** shamiursunny/mini-swe-agent (main): src/minisweagent/{agents,environments,models,run}

**LICENSE:** MIT, Copyright (c) 2025 Kilian A. Lieret and Carlos E. Jimenez

**LICENSE STATUS:** MIT, Copyright (c) 2025 Kilian A. Lieret and Carlos E. Jimenez - LICENSE.md read (FACT)

**RELEVANT FILES:** src/minisweagent/agents/default.py (190 lines), environments/local.py (~3.6KB), environments/{docker,singularity,extra/bubblewrap}.py, models/*, config/

**RELEVANT CODE:** DefaultAgent.run/step/query: linear message history, step_limit, cost_limit, wall_time_limit, max_consecutive_format_errors, exit messages, trajectory save each step

**RELEVANT ARCHITECTURE:** Agent/Model/Environment separation; each action = independent subprocess.run; bash-only tools

**RELEVANT IDEAS:** Recovery via exceptions-as-messages; hard limits; trajectory == messages

**DIRECT REUSE CANDIDATE:** ADAPT (personal agent loop; design copied conceptually). default.py and local.py copied verbatim into source-code/ with LICENSE.

**REFERENCE-ONLY MATERIAL:** docs, benchmark runners

**COMPATIBILITY CONCERNS:** Depends on pydantic, jinja2 and mini-swe-agent Model/Environment classes; copying default.py alone will not run (FACT, from imports).

**SECURITY CONCERNS:** local.py executes commands with no sandbox by itself (INFERENCE from README: docker/bubblewrap envs exist for isolation).

**KAGGLE RELEVANCE:** LOW: cannot be shipped; loop ideas map to prompt/limits in eval_config.yaml.

