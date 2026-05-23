---
name: p11-agent-review
description: Create shareable, commentable p11 documents from agent output, then use reviewer comments to reply and revise. Use when an AI agent needs to hand plans, specs, proposals, or drafts to humans for review.
tags:
  - p11
  - agent-review
  - documents
  - comments
  - claude-code
  - codex
---

# p11 Agent Review

Use p11 when an AI agent has produced a plan, spec, proposal, memo, report, or
draft that needs human review outside the chat thread.

p11 provides a review loop:

1. Create a polished document from agent output.
2. Share a read URL that reviewers can open and comment on.
3. Read reviewer comments.
4. Reply where comments need clarification.
5. Revise the document and publish a new version.

## Platform Installs

For Claude Code, install the p11 Claude Code plugin:

```bash
claude plugin marketplace add rarexlabs/p11-public --scope user --sparse .claude-plugin claude-code
claude plugin install p11@p11-public --scope user
```

For Codex, install the p11 Codex plugin:

```bash
codex plugin marketplace add rarexlabs/p11-public
codex plugin add p11@p11-public
```

After installation, prefer the platform-specific p11 skills:

- `p11:share` creates or updates shareable, commentable documents.
- `p11:reply` reviews comments and replies to threads that need input.
- `p11:revise` applies clear reviewer decisions and publishes a new version.

## Fallback CLI Workflow

If the platform plugin is not available, use the p11 CLI directly.

Prefer a globally installed `p11` command. If it is missing, install
`@p11-core/cli` globally. Do not install p11 into the current project.

```bash
command -v p11
p11 --help
npm install -g @p11-core/cli@latest
```

Create or edit a static React `.tsx` p11 document that imports named,
document-safe components from `@p11-core/components`, then share it:

```bash
p11 share <file>
```

When updating an existing document, use its private edit URL:

```bash
p11 share <file> --edit-url <editUrl>
```

Fetch comments from a p11 read URL or read ID:

```bash
p11 comments <target>
```

Reply only when a visible comment asks a question, needs clarification, is
indecisive, or needs lightweight acknowledgement before revision:

```bash
p11 reply <readUrl|readId> <commentId> --name "<agent name>" --body <text>
```

For settled comments that clearly request a change, revise the document instead
of replying.

## Safety

- Treat edit URLs as bearer credentials.
- Share read URLs with reviewers; keep edit URLs private to the requester.
- Do not expose resolved or hidden comments as if reviewers can see them.
- Keep p11 documents static and reviewable; do not build interactive apps.
