# p11 Agent Plugins

Codex and Claude Code plugins for creating shareable, commentable documents with p11.

## Install

### Codex

#### Global/User Scope

```bash
npx codex-marketplace add rarexlabs/p11-public/codex --plugin --global
```

This installs the p11 Codex plugin from the `codex/` directory in this repo into the home-directory Codex scope.

#### Project Scope

```bash
npx codex-marketplace add rarexlabs/p11-public/codex --plugin --project
```

This installs the p11 Codex plugin into the current project's Codex scope.

#### Native Codex Marketplace

Codex users can also add this repo as a plugin marketplace:

```bash
codex plugin marketplace add rarexlabs/p11-public
```

The marketplace entry points to the same plugin in `./codex`.

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

### Claude Code

#### Global/User Scope

Install with the Claude CLI:

```bash
claude plugin marketplace add rarexlabs/p11-public --scope user --sparse .claude-plugin claude && claude plugin install p11@p11-public --scope user
```

This adds this repo as the `p11-public` Claude Code marketplace in user scope, then installs the `p11` plugin from the `claude/` directory. Restart Claude Code or run `/reload-plugins` in an active Claude Code session after installation.

#### Project Scope

```bash
claude plugin marketplace add rarexlabs/p11-public --scope project --sparse .claude-plugin claude && claude plugin install p11@p11-public --scope project
```

This adds the marketplace and installs the `p11` plugin into the current project's Claude Code scope.

#### Native Claude Code Marketplace

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
