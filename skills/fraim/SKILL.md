---
name: fraim
description: Use FRAIM to discover and execute phased jobs, reusable skills, rules, and mentoring workflows.
---

# FRAIM

Follow this process:

1. If the user did not specify a FRAIM job or topic, inspect local FRAIM job stubs in `fraim/ai-employee/jobs/`, `fraim/ai-manager/jobs/`, and `fraim/personalized-employee/jobs/` first. If local files are unavailable, use the FRAIM MCP job catalog.
2. Match the user's request to a FRAIM job or a likely FRAIM skill.
3. For jobs, load full content with `get_fraim_job({ job: "<job-name>" })`. For skills, load content with `get_fraim_file({ path: "skills/<category>/<skill-name>.md" })`.
4. Execute the phased instructions. Use `seekMentoring` when the job requires phase transitions.

Job stubs are for discovery only. Do not execute a job from stub content.

