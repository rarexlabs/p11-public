# p11 Agent Plugins

## Install

### Codex

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
claude plugin marketplace add rarexlabs/p11-public --scope user --sparse .claude-plugin claude && claude plugin install p11@p11-public --scope user
```

#### Project Scope

```bash
claude plugin marketplace add rarexlabs/p11-public --scope project --sparse .claude-plugin claude && claude plugin install p11@p11-public --scope project
```

Restart Claude Code or run `/reload-plugins` in an active Claude Code session after installation.
