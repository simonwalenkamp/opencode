---
description: Compact the current conversation into a handoff for another agent
---

Write a handoff document summarizing the current conversation so a fresh agent
can continue the work. Save it in the operating system's temporary directory,
not in the current workspace, and report its full path when finished.

Include a "Suggested skills" section that recommends any skills or commands the
next agent should invoke.

Do not duplicate content already captured in other artifacts such as specs,
plans, ADRs, issues, commits, or diffs. Reference those artifacts by path or URL
instead.

Redact sensitive information such as API keys, passwords, credentials, tokens,
and personally identifiable information.

The following arguments, when non-empty, describe what the next session will
focus on. Tailor the handoff accordingly:

<next-session-focus>
$ARGUMENTS
</next-session-focus>
