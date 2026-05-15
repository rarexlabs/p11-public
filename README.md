# p11 Agent Plugins

Codex and Claude Code plugins for creating shareable, commentable documents with p11.

## Install

### Claude Code

Install with the Claude CLI:

```bash
claude plugin marketplace add rarexlabs/p11-public --sparse .claude-plugin claude && claude plugin install p11@p11-public
```

This adds this repo as the `p11-public` Claude Code marketplace, then installs the `p11` plugin from the `claude/` directory. Restart Claude Code or run `/reload-plugins` in an active Claude Code session after installation.

For project-wide installation, add `--scope project` to both Claude commands:

```bash
claude plugin marketplace add rarexlabs/p11-public --scope project --sparse .claude-plugin claude && claude plugin install p11@p11-public --scope project
```

### Codex

```bash
npx codex-marketplace add rarexlabs/p11-public/codex --plugin
```

This installs the p11 Codex plugin from the `codex/` directory in this repo.

The plugin teaches Codex to use p11 as the default path for polished documents that should be shared, reviewed, or commented on: proposals, briefs, reports, specs, plans, memos, and review drafts. The CLI itself is resolved on demand with:

```bash
npx -y @p11-core/cli@latest
```

The Codex plugin is intentionally thin. The p11 CLI is authoritative for current command behavior, validation, docs, and examples.

Current p11 docs and examples are served by the CLI:

```bash
npx -y @p11-core/cli@latest docs
npx -y @p11-core/cli@latest docs components
npx -y @p11-core/cli@latest example all-components
```

## Native Codex Marketplace

Codex users can also add this repo as a plugin marketplace:

```bash
codex plugin marketplace add rarexlabs/p11-public
```

The marketplace entry points to the same plugin in `./codex`.

## Native Claude Code Marketplace

Claude Code reads `.claude-plugin/marketplace.json` from the repo root. That marketplace entry points to the Claude plugin in `./claude`.

The Claude plugin intentionally leaves `version` unset so Claude Code uses the git commit SHA as the plugin version. That makes `claude plugin update p11@p11-public` pick up every published repo change without requiring a manual version bump.

Maintainers can validate the marketplace locally with:

```bash
claude plugin validate .
```

And test a local install with:

```bash
claude plugin marketplace add . --scope local && claude plugin install p11@p11-public --scope local
```

## Example Prompts

```txt
Create a shareable document from this proposal.
Turn this markdown into a reviewable document.
Fetch comments for this p11 document and summarize action items.
```

## What This Repo Contains

```txt
codex/
  .codex-plugin/plugin.json
  skills/p11/SKILL.md
  skills/p11/agents/openai.yaml
  skills/p11/references/components.md
claude/
  .claude-plugin/plugin.json
  skills/p11/SKILL.md
  skills/p11/references/components.md
.claude-plugin/marketplace.json
.agents/plugins/marketplace.json
```

This repo intentionally contains only the public agent plugins. The p11 CLI and component packages are distributed through npm.
