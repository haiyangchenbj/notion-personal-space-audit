---
name: notion-personal-space-audit
slug: notion-personal-space-audit
displayName: Notion Personal Space Audit
description: >
  Audit a personal Notion hub and its nested pages and databases: identify
  mixed content types, empty placeholders, weak navigation, and
  sensitivity-boundary problems, then produce a practical
  information-architecture redesign and migration map. Read-only by default —
  it never modifies Notion content without explicit authorization.
description_zh: 个人 Notion 空间审计与重构——只读审计，输出信息架构重设计与迁移方案
description_en: Notion Personal Space Audit
version: 1.0.0
agent_created: true
---

# notion-personal-space-audit

## When to use

Use when the user asks to audit a Notion personal workspace or page, inspect secondary pages or inline databases, explain why the space is hard to use, decide where ambiguous materials such as sensitive analysis reports belong, or design a safer and more searchable information architecture.

## Steps

1. Confirm the target page URL and scope. Treat the task as read-only unless the user explicitly authorizes a structural change.
2. Resolve the page ID from the URL and retrieve the page metadata.
3. Recursively retrieve block children. Follow `child_page` blocks and query `child_database` rows; preserve the parent path, page title, block count, and last-edited time.
4. Retrieve database schemas and record property names/types. Separate database rows from true navigation pages when interpreting the root layout.
5. Build an inventory by content identity using `references/audit-checklist.md`: log/event, analysis report, raw transcript/source, long-form archive, plan, reading item, person record, life utility, or inbox item.
6. Detect structural issues per the checklist: missing dashboard, mixed responsibilities, inconsistent naming, empty placeholder records, long reports inside short-log databases, stale plans without lifecycle status, and sensitive materials mixed with ordinary notes.
7. Recommend a small functional top-level architecture. Include an inbox, current actions, sensitive-analysis area, cognition/inputs, memory/archive, life tools, and archive only when evidence supports each area.
8. Map every major existing database or page to a proposed destination. For ambiguous content, state the rule explicitly: sensitive analysis reports belong in a separate high-sensitivity archive; short event logs retain event records; raw conversations remain source material and link to derived decisions.
9. Recommend minimal shared fields: content type, domain, status, occurrence date, organization date, sensitivity, and relations. Do not force one schema onto all content types.
10. Produce a concise Markdown report with evidence, signal-light findings, proposed tree, migration table, phased migration order, and a clear statement that no Notion content was changed.
11. If the user explicitly authorizes structure creation, create only empty navigation pages and usage instructions after the audit. Never move, delete, rename, or rewrite existing content unless separately authorized.

## Pitfalls

- Do not assume a page visible in the root snapshot is a standalone navigation page; inline database rows can appear as pages.
- Do not classify a sensitive analysis report as a log event merely because it concerns the same topic (emotions, relationships, health).
- Do not merge raw conversations, derived reports, and action plans into one record. Keep source, analysis, and action linked but distinct.
- Do not delete empty book/person placeholders during an audit. Put them in an archive or pending-review view first.
- Do not expose access tokens in reports, logs, or user-facing output.
- Do not modify Notion without explicit confirmation. The audit should produce a migration plan first.
- When structure creation is authorized, use idempotent title checks and create pages under the audited parent; do not move, delete, rename, or rewrite existing content as part of structure setup.
- Avoid inventing content that the API did not return. Mark inaccessible or uncertain areas explicitly.

## Verification

- Confirm the recursive crawl completed and report the page/database/row counts.
- Confirm each root database has a schema inventory and row count.
- Confirm the report includes a direct answer for ambiguous materials, especially sensitive reports.
- Confirm no Notion write endpoint was called.
- Confirm the output file exists and names the inspected page, scope, findings, and migration plan.
