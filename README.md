# p11 Agent Plugins

p11 provides three focused skills:

- `p11:share` creates or updates shareable, commentable documents.
- `p11:reply` reviews comments/replies and responds to visible threads that ask questions, are unclear, are indecisive, or need input.
- `p11:revise` applies clear reviewer decisions and shares a new version.

## Install

### Codex

#### Codex App UI

1. Open the Codex app.
2. Go to the plugins or marketplaces settings.
3. Click **Add marketplace**.
4. Set **Source** to:

   ```text
   rarexlabs/p11-public
   ```

5. Leave **Git ref** as:

   ```text
   main
   ```

6. Leave **Sparse paths** empty.
7. Click **Add marketplace**.
8. Open the newly added `p11-public` marketplace.
9. Install the `p11` plugin.

The installed Codex plugin exposes `p11:share`, `p11:reply`, and `p11:revise`.

#### CLI

#### Global/User Scope

```bash
npx -y codex-marketplace add rarexlabs/p11-public/plugins/p11 --plugin --global
```

#### Project Scope

```bash
npx -y codex-marketplace add rarexlabs/p11-public/plugins/p11 --plugin --project
```

### Claude Code

#### Global/User Scope

```bash
claude plugin marketplace add rarexlabs/p11-public --scope user --sparse .claude-plugin claude-code && claude plugin install p11@p11-public --scope user
```

#### Project Scope

```bash
claude plugin marketplace add rarexlabs/p11-public --scope project --sparse .claude-plugin claude-code && claude plugin install p11@p11-public --scope project
```

Restart Claude Code or run `/reload-plugins` in an active Claude Code session after installation.

The installed Claude Code plugin provides matching `p11:share`, `p11:reply`, and `p11:revise` workflows through its `share`, `reply`, and `revise` skills.

## Generic Skill Registries

This repository also includes a registry-facing root `SKILL.md` for directories
that index `SKILL.md` files directly.

This wrapper is for discovery in generic skill registries. The authoritative
platform packages remain the Claude Code plugin under `claude-code/` and the
Codex plugin under `plugins/p11/`.
