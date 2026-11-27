# ZeroPoint Payments plugin for Claude Code

One install connects Claude Code to the ZeroPoint Payments MCP server and adds two skills that
carry the same connection check and integration prompts as the sandbox console.

```bash
export ZEROPOINT_TEST_API_KEY=zp_test_...        # from your ZeroPoint operator; never paste it in chat
claude plugin marketplace add zeropointapp/zeropoint-payments-plugin
claude plugin install zeropoint-payments@zeropoint
```

Set `ZEROPOINT_MCP_URL` to another server's `/mcp` address to use a different deployment; it
defaults to the hosted sandbox. Restart Claude Code after changing either variable.

Then, in a session:

- `/zeropoint-payments:connect` checks the connection read-only and reports your platform and
  that `livemode` is false.
- `/zeropoint-payments:build-payments terminal` (or `keyed`, or `explore`) inspects your app,
  checks the reviewed component library before writing any payment plumbing, wires what fits
  to your routes and models, and proposes a plan you approve before any
  code changes or sandbox payments.

The server's own prompts also appear as `/mcp__plugin_zeropoint-payments_zeropoint__getting_started`,
`..._integrate_card_present` and `..._integrate_keyed`.

Questions and issues: ask your ZeroPoint contact.
