# p11 Agent Plugins

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
