---
name: fraim-delivery-evidence
description: Create an acceptance matrix and validation record for PR, release, marketplace, or stakeholder handoff.
---

# FRAIM Delivery Evidence

Use this skill when the main task is to prove what is ready, what is accepted, and what remains blocked.

## Steps

1. Define the acceptance target.
   - Examples: merged PR, marketplace listing, release artifact, live endpoint, customer-ready document.

2. Build an evidence matrix.

   ```text
   | Target | Current State | Evidence | Next Action |
   |---|---|---|---|
   ```

3. Verify each target from the system of record.
   - Use GitHub labels and comments for GitHub submissions.
   - Use portal status for vendor app reviews.
   - Use live URLs or install commands for public listings.

4. Distinguish real acceptance from preparation.
   - `package-prepared` means source is ready.
   - `submitted` means the external system has received it.
   - `in-review` means vendor review is pending.
   - `accepted` means users can discover, install, or use it.
   - `rejected` means the rejection reason and recovery path are recorded.

5. Record validation commands and dates.

   ```bash
   git status --short
   gh issue view <number> --comments
   curl -I <public-url>
   ```

## Output

Return a compact status report:

```text
Status:
- Accepted:
- In review:
- Rejected / blocked:
- Evidence:
- Next action:
```

## Guardrails

- Do not collapse `submitted`, `in review`, and `accepted` into one status.
- Do not rely on memory for current marketplace state; verify the live tracker.
- Do not use internal readiness as a substitute for external acceptance.
