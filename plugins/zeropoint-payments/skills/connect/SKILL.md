---
name: connect
description: Check the ZeroPoint Payments MCP connection read-only. Use when the user asks whether ZeroPoint is connected, after installing this plugin, or before any payment integration work.
disable-model-invocation: true
---

Run this connection check against the `zeropoint` MCP server this plugin configures. The
server needs `ZEROPOINT_TEST_API_KEY` set in the environment that launched Claude Code; if the
tools are missing or answer an authentication error, say so and stop.

Check my ZeroPoint MCP connection without changing anything. Discover the available tools, read get_doc("getting-started") and call integration_checklist. Confirm the returned platform and that livemode is false. Do not print credentials or create any resources. If a tool or permission is unavailable, give me the exact problem and one next step. Report the observed result; an enabled server entry alone is not proof of a working connection.
