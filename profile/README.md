<p align="center">
  <img src="https://raw.githubusercontent.com/leakferrethq/leakferret/master/brand/logo.png" alt="leakferret" width="420">
</p>

<p align="center">
  <b>MCP-native secret scanner — finds hardcoded secrets, verifies which are <i>actually live</i>, and rewrites the leak to read from an environment variable.</b>
</p>

<p align="center">
  <a href="https://leakferret.com">leakferret.com</a>
  ·
  <a href="https://github.com/leakferrethq/leakferret">main repo</a>
  ·
  <a href="https://github.com/leakferrethq/leakferret#readme">docs</a>
  ·
  MIT
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/leakferrethq/leakferret/master/brand/demo.gif" alt="leakferret finds a leaked secret, verifies it against the provider, and rewrites the literal to read from an env var" width="760">
</p>

---

### Why leakferret

Most scanners stop at *"this looks like a secret."* leakferret goes two steps further:

- **Verify** — one harmless API call to the provider (AWS, GitHub, GitLab, Stripe, OpenAI, Anthropic, Slack, …) confirms which keys are *still live*, so you fix what's actually exploitable instead of triaging regex noise.
- **Rewrite** — swaps the hardcoded literal for an `os.environ` / `process.env` / `ENV.fetch` lookup, adds a `.env.example` line, and prints seed commands for your secret manager.
- **MCP-native** — exposes the whole pipeline over the Model Context Protocol, so a coding agent can self-check *before it commits*.

> **Privacy by construction:** the full secret value never leaves your machine — only a redacted `AKIA…4XYZ` preview ever leaves the process. A dedicated test enforces it.

### Install

```bash
cargo install leakferret-cli      # Rust
npm   i -g @leakferret/cli        # npm
gem   install leakferret          # Ruby

leakferret verify .               # scan, then confirm which keys are live
```

### Where it runs

| | |
|---|---|
| 🦀 &nbsp;**CLI / engine** | [`leakferret`](https://github.com/leakferrethq/leakferret) — one fast Rust binary |
| 🤖 &nbsp;**MCP server** | `leakferret mcp` — for Claude Code, Cursor, Continue, Claude Desktop |
| ⚙️ &nbsp;**CI** | [`leakferret-action`](https://github.com/leakferrethq/leakferret-action) — SARIF → GitHub Code Scanning |
| 🧩 &nbsp;**VS Code / Cursor** | [`leakferret-vscode`](https://github.com/leakferrethq/leakferret-vscode) — scan on save, one-click fix |
| 💎 &nbsp;**Ruby** | [`leakferret-ruby`](https://github.com/leakferrethq/leakferret-ruby) |
| 📦 &nbsp;**npm** | [`leakferret-npm`](https://github.com/leakferrethq/leakferret-npm) |
| 🐹 &nbsp;**Go** | [`leakferret-go`](https://github.com/leakferrethq/leakferret-go) |
| 📚 &nbsp;**Catalog data** | [`leakferret-catalog`](https://github.com/leakferrethq/leakferret-catalog) — signed known-public examples |

<sub>MIT-licensed engine, CLI, MCP server, and wrappers · fixture-catalog data CC-BY-SA-4.0 · maintained by Maria Khan</sub>
