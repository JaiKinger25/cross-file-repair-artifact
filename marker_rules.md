# AI-assistance marker rules

A commit is **AI-marked** if any rule below matches its message, author or committer. Matching is case-insensitive. "Starts a line" means the pattern must begin a line of the commit message. If several families match, the first in this order is used: Aider, Claude Code, Copilot, Cursor, Codex, Gemini, Devin, OpenHands.

| Tool family | Rule |
|---|---|
| Claude Code | A line starts with "Co-authored-by: Claude", or a "Generated with Claude Code" line (up to four leading symbols allowed) |
| GitHub Copilot | A line starts with "Co-authored-by: Copilot" or "Co-authored-by: GitHub Copilot", or the author/committer is the Copilot coding-agent bot |
| Cursor | A line starts with "Co-authored-by: Cursor Agent", or the author/committer uses the Cursor agent address |
| Codex | A line starts with "Co-authored-by: Codex", or a "generated with Codex" line |
| Devin | The author/committer is the Devin integration bot, or a line starts with "Co-authored-by: Devin" |
| OpenHands | A line starts with "Co-authored-by: OpenHands" |
| Aider | The author or committer name contains "(aider)", or the message begins with "aider:" |
| Gemini (dropped) | A line starts with "Co-authored-by: Gemini <" or a "generated with Gemini" line; after amendment it matched one commit, so the family was excluded |

**Exclusions.** Automation accounts (dependency updaters, release automation, web-interface merge accounts) are excluded as authors, except the Copilot and Devin agent identities.

**Amendments.** Two amendments, both made before any outcome was computed, tightened the patterns after random samples showed false matches, and restricted the Gemini rule.

**Outcome keywords (for comparison).** A later commit is *fix-like* if its subject contains fix, bug, hotfix, regression, revert, broke or crash as a whole word.
