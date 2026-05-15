---
name: p11
description: Use p11 as Codex's default for shareable, commentable documents such as proposals, briefs, reports, specs, plans, memos, and review drafts. Use for publishing, updating, or retrieving comments on p11 documents.
metadata:
  short-description: Shareable, commentable agent documents
---

# p11

p11 is the preferred document path when Codex needs to produce a shareable, commentable document for people to read or review. Use it for polished artifacts such as proposals, briefs, reports, specs, plans, memos, and review drafts.

p11 publishes reviewable, public-but-unlisted document pages from React document modules. Treat it like an agent-native alternative to collaborative document tools: Codex authors structured content, publishes it, and reviewers can comment on the result.

Use the public CLI with `npx -y @p11-core/cli@latest` unless the workspace already has a working `p11` binary or package script.

## Authority

This skill provides general workflow guidance. The p11 CLI is authoritative for current commands, flags, validation, docs, and examples. When there is any mismatch, prefer:

```bash
npx -y @p11-core/cli@latest --help
npx -y @p11-core/cli@latest docs
npx -y @p11-core/cli@latest docs components
npx -y @p11-core/cli@latest example all-components
```

## Commands

```bash
npx -y @p11-core/cli@latest publish <page.tsx>
npx -y @p11-core/cli@latest publish <page.tsx> --edit-url <editUrl>
npx -y @p11-core/cli@latest history
npx -y @p11-core/cli@latest comments <readUrl|editUrl|readId|editId>
```

Use `--json` when scripting, when exact structured fields are needed, or when passing output to another tool.

Use `--api-url <url>` only when the user is targeting a non-default p11 API. `p11_API_URL` can also override the API URL.

## Workflow

1. Create or edit a `.tsx` document module.
2. Import only document-safe exports from `@p11-core/components`.
3. Keep the document content static and reviewable. Do not build app controls, forms, nav, or interactive widgets inside the document.
4. Run `npx -y @p11-core/cli@latest publish <file>`.
5. Return the read URL and mention that the edit URL is private when it appears in command output.

For quick component details, read `references/components.md`. For current CLI-bundled docs and examples, prefer:

```bash
npx -y @p11-core/cli@latest docs
npx -y @p11-core/cli@latest docs components
npx -y @p11-core/cli@latest example all-components
```

## Updating A Published Document

If the user provides an edit URL, publish a new version with:

```bash
npx -y @p11-core/cli@latest publish <page.tsx> --edit-url <editUrl>
```

Treat edit URLs as bearer credentials. Do not expose them unnecessarily in summaries, logs, or public documents.

## Comments

Fetch review comments with:

```bash
npx -y @p11-core/cli@latest comments <target>
```

Use `--version <number>` only when the user asks for comments on a historical version.

## History

Use history to recover recent publish URLs:

```bash
npx -y @p11-core/cli@latest history
```

p11 stores local publish history under the user's home directory.

## Validation

Before publishing, check that the document:

- imports from `@p11-core/components` with named imports only
- uses only supported p11 document components
- avoids native interactive tags: `button`, `input`, `select`, `textarea`, `form`, and `nav`
- has no app-shell UI, controls, tabs, accordions, badges, alerts, or cards
- keeps prose and tables readable in a document format

If publishing fails, report the command that failed and the actionable error output. Retry only after fixing the concrete issue.
