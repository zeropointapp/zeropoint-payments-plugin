---
name: build-payments
description: Add ZeroPoint Payments to the user's existing app with a supported workflow, starting read-only and ending with sandbox evidence. Use when the user asks to add payments, checkout, terminals or refunds with ZeroPoint.
argument-hint: [terminal|keyed|explore]
disable-model-invocation: true
---

The workflow is `$ARGUMENTS`. Choices: `terminal` (Take payments on a terminal), `keyed` (Take card payments online), `explore` (Help me choose). If no workflow was given, ask the
user which one fits before doing anything else, then follow only that workflow's section
below. Run `/zeropoint-payments:connect` first if this session has not confirmed the
connection yet.

## Workflow `terminal`: Take payments on a terminal

Help me add ZeroPoint payments to my existing app. The workflow I selected is Take payments on a terminal.

Start read-only. Inspect my app's framework, existing checkout screens, order model and styling. Reuse its conventions. Explain the plan in plain language and ask only for business choices you cannot infer from the project.

Search first, then write. Before writing any payment plumbing, check ZeroPoint's reviewed component library (list_snippets, then get_snippet) and the guides. Install what already exists and works, unchanged; write only the parts that are genuinely new to my app.

Using the zeropoint MCP connection, discover available tools, read get_doc("getting-started"), get_doc("api-conventions") and get_doc("integration-snippets"), then call integration_checklist and get_openapi. Confirm my platform and livemode is false. If access fails, stop and give me one clear next step. My console sign-in is separate from my agent's API access.

Read get_doc("integrate-antique-store-pos") and get_doc("troubleshoot-terminal-integration"). Use list_snippets, then get_snippet for the compatible returned bundles. The current reference IDs are zeropoint.node.terminal-pos, zeropoint.node.webhook-receiver and zeropoint.node.order-payment-evidence. Confirm these IDs, versions and requirements in the actual catalog. Read the complete README and tests before proposing changes. These are server-side components, not prebuilt browser widgets. Explain where the checkout UI belongs in my app and which existing order model it will use. Start the proposed validation with a simulated terminal; hardware acceptance is separate.

Show me which files and screens you propose to change, which components fit, their requirements, and what is still unsupported. For each component you propose, walk its manifest's host_wiring list against my actual app and name the route, model, secret store, storage path and worker that will supply each item; the not_included list is what stays mine. Do not change code or run payment operations until I approve the plan. Never ask for API keys, card data, nonces or signing secrets in chat. Use privately configured server-side credentials without printing them.

For an approved implementation, preserve the components' documented ownership, integer-cent, idempotency and signature-verification rules. Add UI for loading, success, decline, cancellation and uncertain outcomes as supported by the contract. Do not call an unknown outcome paid or automatically start another payment. Run the retrieved tests and the app's relevant checks.

Finish with evidence in three parts: reused (each library file installed unchanged, with its component id, version and sha256 from the catalog), generated (the glue written for this app, file by file, and which host_wiring item each one supplies), and still unsupported or needing my action. Then the checks: local tests, the exact sandbox payment and receipt checked, webhook delivery and independent signature checks. Keep local, hosted, hardware and live verification separate. Ask before using a physical terminal, contacting a receiver, issuing a refund or void, creating infrastructure or deploying. Do not enable live payments.

## Workflow `keyed`: Take card payments online

Help me add ZeroPoint payments to my existing app. The workflow I selected is Take card payments online.

Start read-only. Inspect my app's framework, existing checkout screens, order model and styling. Reuse its conventions. Explain the plan in plain language and ask only for business choices you cannot infer from the project.

Search first, then write. Before writing any payment plumbing, check ZeroPoint's reviewed component library (list_snippets, then get_snippet) and the guides. Install what already exists and works, unchanged; write only the parts that are genuinely new to my app.

Using the zeropoint MCP connection, discover available tools, read get_doc("getting-started"), get_doc("api-conventions") and get_doc("integration-snippets"), then call integration_checklist and get_openapi. Confirm my platform and livemode is false. If access fails, stop and give me one clear next step. My console sign-in is separate from my agent's API access.

Read get_doc("collect") and get_doc("accept-a-keyed-payment"). Use list_snippets, then get_snippet for zeropoint.node.keyed-checkout after confirming its current version and requirements in the catalog. Read its complete README and tests. It is a sandbox-only Node reference with durable SQLite order identity, not verified hosted processor acceptance. Explain the hosted card form (an iframe on form_url from get_collect_config, with ?origin= set to my page), the zeropoint.nonce message handoff, explicit retry policy and the UI states using the current documented contract. Identify missing hosted sandbox verification before proposing implementation. Do not invent a nonce, save a card or substitute a terminal component for this flow.

Show me which files and screens you propose to change, which components fit, their requirements, and what is still unsupported. For each component you propose, walk its manifest's host_wiring list against my actual app and name the route, model, secret store, storage path and worker that will supply each item; the not_included list is what stays mine. Do not change code or run payment operations until I approve the plan. Never ask for API keys, card data, nonces or signing secrets in chat. Use privately configured server-side credentials without printing them.

For an approved implementation, preserve the components' documented ownership, integer-cent, idempotency and signature-verification rules. Add UI for loading, success, decline, cancellation and uncertain outcomes as supported by the contract. Do not call an unknown outcome paid or automatically start another payment. Run the retrieved tests and the app's relevant checks.

Finish with evidence in three parts: reused (each library file installed unchanged, with its component id, version and sha256 from the catalog), generated (the glue written for this app, file by file, and which host_wiring item each one supplies), and still unsupported or needing my action. Then the checks: local tests, the exact sandbox payment and receipt checked, webhook delivery and independent signature checks. Keep local, hosted, hardware and live verification separate. Ask before using a physical terminal, contacting a receiver, issuing a refund or void, creating infrastructure or deploying. Do not enable live payments.

## Workflow `explore`: Help me choose

Help me add ZeroPoint payments to my existing app. The workflow I selected is Help me choose.

Start read-only. Inspect my app's framework, existing checkout screens, order model and styling. Reuse its conventions. Explain the plan in plain language and ask only for business choices you cannot infer from the project.

Search first, then write. Before writing any payment plumbing, check ZeroPoint's reviewed component library (list_snippets, then get_snippet) and the guides. Install what already exists and works, unchanged; write only the parts that are genuinely new to my app.

Using the zeropoint MCP connection, discover available tools, read get_doc("getting-started"), get_doc("api-conventions") and get_doc("integration-snippets"), then call integration_checklist and get_openapi. Confirm my platform and livemode is false. If access fails, stop and give me one clear next step. My console sign-in is separate from my agent's API access.

Ask me what payment experience I need after inspecting my app. Compare it with get_doc("whats-available"), get_openapi and list_snippets. Clearly identify unsupported workflows and missing contracts. Do not promise subscriptions, saved cards, payment links, deposits or automatic balance charges unless the current contract explicitly supports them. Recommend the smallest supported starting point and explain the tradeoffs.

Show me which files and screens you propose to change, which components fit, their requirements, and what is still unsupported. For each component you propose, walk its manifest's host_wiring list against my actual app and name the route, model, secret store, storage path and worker that will supply each item; the not_included list is what stays mine. Do not change code or run payment operations until I approve the plan. Never ask for API keys, card data, nonces or signing secrets in chat. Use privately configured server-side credentials without printing them.

For an approved implementation, preserve the components' documented ownership, integer-cent, idempotency and signature-verification rules. Add UI for loading, success, decline, cancellation and uncertain outcomes as supported by the contract. Do not call an unknown outcome paid or automatically start another payment. Run the retrieved tests and the app's relevant checks.

Finish with evidence in three parts: reused (each library file installed unchanged, with its component id, version and sha256 from the catalog), generated (the glue written for this app, file by file, and which host_wiring item each one supplies), and still unsupported or needing my action. Then the checks: local tests, the exact sandbox payment and receipt checked, webhook delivery and independent signature checks. Keep local, hosted, hardware and live verification separate. Ask before using a physical terminal, contacting a receiver, issuing a refund or void, creating infrastructure or deploying. Do not enable live payments.
