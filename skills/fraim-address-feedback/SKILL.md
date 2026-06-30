---
name: fraim-address-feedback
description: Convert review comments, rejected submissions, or maintainer feedback into a tracked correction loop.
---

# FRAIM Address Feedback

Use this skill when work has been reviewed, rejected, or corrected and the next step is to understand and address every item.

## Steps

1. Gather all feedback from the system of record.

   ```bash
   gh pr view <number> --comments --json title,state,reviews,comments
   gh issue view <number> --comments --json title,state,labels,comments
   ```

2. Separate feedback by type:
   - `blocking`: must be fixed before resubmission.
   - `clarifying`: needs a response or evidence.
   - `informational`: useful context, not a required change.

3. Identify the root cause.
   - For marketplace rejections, inspect the submitted package and accepted peer submissions.
   - For PR reviews, inspect the exact files and line anchors before editing.

4. Make the correction.
   - Update source files, submission metadata, docs, or package contents.
   - Keep the fix targeted to the feedback.

5. Revalidate the corrected artifact.

   ```bash
   git diff --check
   npm test
   npx tsc --noEmit
   ```

6. Resubmit or reply in the same thread when the platform requires continuity.
   - Explain what changed.
   - Provide the new commit, version, or evidence link.
   - Use the platform's retry command only after the artifact is updated.

## Output

Return a feedback ledger:

```text
Feedback:
- Source:
- Reason:
- Fix:
- Validation:
- Resubmission:
```

## Guardrails

- Do not argue with a maintainer rejection before understanding the policy behind it.
- Do not rerun intake against the same rejected artifact.
- Do not hide required external-service setup; make any optional service dependency explicit.
