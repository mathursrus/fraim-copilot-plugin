---
name: fraim-feature-implementation
description: Implement a feature or bug fix with FRAIM-style scoping, tests, validation, and evidence.
---

# FRAIM Feature Implementation

Use this skill when the user asks Copilot to build, fix, or finish product work in a repository.

## Steps

1. Scope the request against the repository.
   - Read the issue, nearby docs, existing tests, and analogous code before editing.
   - Name the user-visible outcome and the files likely to change.

   ```bash
   gh issue view <number> --comments
   rg -n "<feature term>|<existing behavior>|<error text>" .
   rg --files -g "*test*" -g "*.spec.*"
   ```

2. Reproduce or define the behavior.
   - For bugs, capture the failing behavior first.
   - For features, define the acceptance checks before implementation.

3. Add or update durable tests.
   - Prefer existing project test conventions.
   - Test observable behavior, not implementation details or formatted strings.

4. Implement the smallest coherent change.
   - Follow local patterns.
   - Avoid unrelated refactors.
   - Preserve user changes already present in the worktree.

5. Validate with the right gates.

   ```bash
   npm test
   npx tsc --noEmit
   rg -n "TODO|FIXME|placeholder" <changed-files>
   ```

6. Produce evidence.
   - Summarize what changed.
   - List tests and manual checks.
   - Record known residual risk or follow-up.

## Output

Return a concise implementation report:

```text
Summary:
- Changed:
- Validation:
- Evidence:
- Remaining risk:
```

## Guardrails

- Do not skip tests because the change is small.
- Do not call work complete while the external acceptance state is still unknown.
- Do not overwrite unrelated local changes.
