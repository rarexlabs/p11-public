# p11 Codex Plugin

Codex plugin for creating shareable, commentable documents with p11.

## Install

```bash
npx codex-marketplace add rarexlabs/p11-public/codex --plugin
```

This installs the p11 Codex plugin from the `codex/` directory in this repo.

The plugin teaches Codex to use p11 as the default path for polished documents that should be shared, reviewed, or commented on: proposals, briefs, reports, specs, plans, memos, and review drafts. The CLI itself is resolved on demand with:

```bash
npx -y p11@latest
```

The Codex plugin is intentionally thin. The p11 CLI is authoritative for current command behavior, validation, docs, and examples.

Current p11 docs and examples are served by the CLI:

```bash
npx -y p11@latest docs
npx -y p11@latest docs components
npx -y p11@latest example all-components
```

## Native Codex Marketplace

Codex users can also add this repo as a plugin marketplace:

```bash
codex plugin marketplace add rarexlabs/p11-public
```

The marketplace entry points to the same plugin in `./codex`.

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
.agents/plugins/marketplace.json
```

This repo intentionally contains only the public Codex plugin. The p11 CLI and component packages are distributed through npm.
