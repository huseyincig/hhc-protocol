# Changelog

## 5.8.2 — 2026-09-08

PATCH, 48 tools, no renames/removals/required changes:
- shell_exec documents the platform shell contract (cmd.exe /d /s /c on
  Windows, /bin/bash -lc elsewhere).
- service_list records carry `queryable` (service_status policy allowlist
  discoverability).


## 5.8.1 — 2026-09-08

Canonical tool metadata (PATCH, 48 tools, no semantic changes): human-readable
titles across the surface (e.g. Remote Shell → Run Shell Command, Browser
Snapshot → Inspect Web Page); tool-selection disambiguation signals
(dedicated-tool-first pointers, overlap pairs: uninstall/forget,
write/edit, list/tree, log snapshot/follow, restart/stop); descriptions for
all 187 input properties; annotation corrections (client_uninstall and
file_edit are destructive; pure reads are idempotent); unenforced
"confirmation required" claim on privileged_shell_exec softened to
recommended (confirm=true + mcp:admin remain enforced where implemented).

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
