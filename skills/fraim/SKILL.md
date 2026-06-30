---
name: fraim
description: Select and run a FRAIM phased workflow in Copilot without requiring external services.
---

# FRAIM

Use this skill when the user asks for FRAIM help, asks which workflow to run, or gives a broad delivery request that needs structured execution.

## Steps

1. Identify the user's concrete outcome, not just the requested activity.
2. Inspect the repository for local workflow hints before inventing a new process:

   ```bash
   rg --files -g "AGENTS.md" -g "fraim/**/jobs/*.md" -g "docs/evidence/**" -g "docs/rfcs/**"
   ```

3. Choose the most specific bundled FRAIM skill:
   - Use `fraim-feature-implementation` for a code change, bug fix, or product feature.
   - Use `fraim-address-feedback` for review comments, rejected submissions, or maintainer feedback.
   - Use `fraim-delivery-evidence` when the main need is proof of readiness, acceptance, or handoff status.
4. Execute the selected skill end to end. Keep work tied to observable artifacts such as files changed, tests run, issue comments, review state, marketplace labels, or live URLs.
5. If the repository has FRAIM job stubs, use them only as discovery hints unless a local FRAIM server or MCP tool provides the full job instructions.

## Guardrails

- Do not stop at planning when the user asked you to handle the work.
- Do not treat a pull request as done if the user's actual outcome is an external submission, approval, listing, or release.
- Do not claim acceptance from a prepared package. Record the real external state.
