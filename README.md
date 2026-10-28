# YT Risk Auditor

A reusable Agent Skill for reviewing YouTube transcripts, subtitles and supplied production materials. Works with Claude Code and can be packaged for Claude.ai upload. The same core skill is usable in Codex.

The editable watchlist currently contains 691 unique entries. A keyword match means **review**, not that YouTube prohibits the word. This skill does not guarantee monetization, edit videos, authenticate allegations or inspect media that was not supplied.

## Install in Claude Code on Windows

Run in PowerShell. Choose a destination that does not already contain another copy:

```powershell
git clone https://github.com/Link-erist/YT-Risk-Auditor.git "$env:USERPROFILE\.claude\skills\yt-risk-auditor"
```

Start Claude Code and invoke:

```text
/yt-risk-auditor Check this transcript and identify censoring priorities and new keyword suggestions.
```

Claude Code can also select the skill automatically when relevant. If you already have a competing copy or an uploaded synced version, check which skill is being invoked.

## Update continuously

Use this repository as the authoritative editable copy:

- `references/watchlist.txt`: one UTF-8 entry per line. Preserve distinct spellings and variants; deduplicate case-insensitively. A trailing `*` is a prefix rule.
- `SKILL.md`: main audit and maintenance instructions.
- `references/review-guide.md`: matching rules, context checks and output conventions.
- `agents/openai.yaml`: Codex display metadata; not required by Claude.

Ask Claude Code to add or remove terms, inspect the diff, then commit and push the intended files. An uploaded Claude.ai skill is a separate snapshot and does not push its edits back to GitHub automatically. Do not edit multiple copies independently and assume they synchronize.

To retrieve changes published elsewhere:

```powershell
git -C "$env:USERPROFILE\.claude\skills\yt-risk-auditor" pull --ff-only
```

If Git reports local modifications or diverged commits, resolve them explicitly rather than discarding them.

## Upload to Claude.ai

From the root of this cloned repository, export the committed skill with the correctly named top-level folder:

```powershell
git archive --format=zip --prefix=yt-risk-auditor/ -o ../yt-risk-auditor.zip HEAD SKILL.md references agents
```

Enable code execution/file creation in Claude, then open Customize > Skills > Create skill > Upload a skill and select the generated ZIP. Enable the uploaded skill. Re-export and update the upload after changes; a GitHub push alone does not replace that uploaded snapshot.

## What an audit provides

- Full supplied-transcript reading with source line references and version hash.
- Literal keyword matches, including cross-line phrases and overlapping rules.
- Separate censor/edit priorities, context review, evidence/framing concerns and innocent matches.
- A report, occurrence CSV, and separate suggested additions in the active workspace.
- Persistent watchlist updates only when requested, with verification of the actual saved file.

Only the skill and its maintained resources belong here. Keep private transcripts and generated audit reports outside this repository. When Claude cannot persist edits to a skill, it should provide an updated artifact and explain that limitation.

## Compatibility and verification

The skill has standard `name`/`description` YAML frontmatter, a description under 200 characters, relative resource links, UTF-8 resources, and no required executable scripts, packages or API keys. Instructions rely on the host assistant's available tools. Format and resource checks do not prove identical model behavior across hosts; no live Claude audit has been performed for this release.

Official references:

- [Claude Code skills](https://code.claude.com/docs/en/skills)
- [Create custom skills for Claude](https://support.claude.com/en/articles/12512198-how-to-create-custom-skills)
