# Locker Protocol Agentic for Codex

**Your private key is nowhere: not on our servers, not on the agent's machine, not with anyone.**

The agent trades. It holds nothing.

- **Where the key is:** the account's private key stays in Locker Vault, an offline app on a phone or tablet. The computer only holds an agent key, sealed under a password, that expires on its own (six months by default, the longest Hyperliquid allows).
- **Who can withdraw:** only the vault, by a QR code a person scans and signs. Hyperliquid refuses the agent key every withdrawal and every send; the one movement of funds it accepts from that key is a deposit into a Hyperliquid vault, which lpa never signs (measured on mainnet, 2026-09-28).
- **What goes where:** Hyperliquid for orders and reads, public Arbitrum nodes for deposits and balances, hyperkeel.com only when one of its tools is called. No server of ours, no account, no telemetry.

**Documentation:** [doc.lockerprotocol.com/agent-wallet](https://doc.lockerprotocol.com/agent-wallet/agent): install, the setup in steps, how it trades and every command. **Website:** [hyperagentictrader.com](https://hyperagentictrader.com).

This repository is the Codex plugin of [Locker Protocol Agentic](https://github.com/locker-protocol/agentic). Its skill is a pinned copy of [locker-protocol/agent-skills](https://github.com/locker-protocol/agent-skills), version 2.0.2: the files are not written here, see [SKILL_SOURCE.md](SKILL_SOURCE.md).

## Install

```sh
codex plugin marketplace add locker-protocol/agentic-codex-plugin
codex plugin add locker-agentic@locker-protocol
```

The plugin runs the `lpa` command on your computer, which it never installs: see the [install section of the skill repository](https://github.com/locker-protocol/agent-skills#install). Codex runs the plugin's session-start hook only after you review and trust it; the hook runs `lpa doctor --format json` and never fails a session.

The MCP server is configured apart, in `~/.codex/config.toml`, at `@latest` the same way:

```toml
[mcp_servers.locker]
command = "npx"
args = ["-y", "--ignore-scripts", "@locker-protocol/agent-wallet-hyperliquid-trader-mcp@latest"]
```

## Licence

LOCKER PROTOCOL PROPRIETARY NON-COMMERCIAL LICENSE. See `LICENSE`.
