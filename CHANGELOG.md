# Changelog

## 5.3.0 — 2026-09-07

New tool `hhc_feedback` (42 total): structured product-issue reporting with server-side enrichment,
secret redaction, deterministic fingerprint dedup and severity computation. All annotations false
(internal sink); outputSchema-validated structured result.

## 5.2.0 — 2026-09-07

20 new tools (41 total): client_ping/uninstall, file_read_many/edit/stat, directory_tree,
process_start/output/input/list/terminate (opaque handles, no shell strings), service_list/start/stop/restart,
log_follow_start/read/stop, browser_create/close (+optional browser_id), audit_query.
All tools carry annotations + rich property descriptions; client_id mirrors x-mcp-header Client-Id.
Deterministic categorical ordering for prompt-cache stability. shell_exec is now documented fallback.

## 2026-09-07 — Initial public release

Extracted from the private monorepo canonical sources. Agent protocol
`1.0.0`, MCP contract `5.1.0` (20 tools), host-policy contract `1.0.0`
(18 capabilities). Clean root commit; prior history intentionally omitted.
