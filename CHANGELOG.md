# Changelog

## 5.10.2 — 2026-09-09

PATCH, 51 tools, no wire changes: service start/stop/restart `required`
follows canonical `unit` (the `service` fallback stays runtime-accepted
but is no longer advertised as required).


## 5.10.1 — 2026-09-09

PATCH, 51 tools, no wire changes: documents win32 process_list rows
(pid+name only), keeping the schema honest per platform.


## 5.10.0 — 2026-09-09

MINOR, 51 tools, backward compatible: new `job_get` (poll job lifecycle state)
and `job_cancel` (best-effort advisory cancel) close the async-handle loop;
`service_start/stop/restart` accept `unit` as preferred alias for `service`.
Plus PATCH-grade corrections: process_list documents its real flat dual-scope
shape; system_snapshot gains release/loadavg; client_list top-level client_id
nullable; 30 envelope statuses narrowed to completed|failed; file_stat
wording; enforced input bounds; pid/exit_code nullability; service naming
cross-references.

## 5.9.1 — 2026-09-09

PATCH, 49 tools, backward compatible (no wire changes; schemas now describe
the runtime truth): client_list items use the real inventory fields
(client_id, hostname, client_version, status, transport, capabilities);
file_read_many, directory_tree, process_list, browser_find, browser_tabs,
browser_console_messages, browser_network_requests, browser_file_upload
results are typed (no generic object[]) and nested under result like the
wire; audit_query entries are typed audit rows; file_read documents
bytes/truncated; file_edit gains the enforced 64-hex sha pattern;
process_start/shell bounds mirror runtime enforcement; service unit/service
naming cross-referenced; pid/exit_code nullability matches runtime.

## 5.9.0 — 2026-09-08

MINOR, 49 tools, backward compatible: new `gui_close` tool closes a GUI
application previously launched via `gui_launch`, by its reported process
id. Only agent-launched PIDs are accepted (GUI_PID_NOT_MANAGED otherwise),
so no new privilege is introduced. No renames, removals, or required-field
changes.


## 5.8.3 — 2026-09-08

PATCH, 48 tools: audit_query documents the action vocabulary (tool calls
are recorded under action "tool.execute" with the tool name in
payload.tool).


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
