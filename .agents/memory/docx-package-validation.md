---
name: Word package namespace validation
description: Compatibility checks for repairing DOCX packages without changing user content.
---

A DOCX can be ZIP- and XML-valid while Word rejects it when `mc:Ignorable` or `mc:Choice/@Requires` names prefixes that are not declared on the same part's root. Repair only those namespace declarations, then compare non-root XML content and media hashes.

**Why:** Word enforces markup-compatibility prefix declarations more strictly than generic XML parsers.

**How to apply:** Validate ZIP integrity, XML parsing, relationship targets, content types, and MC prefixes; when repairing, preserve all text, relationships, media, and non-root XML bytes.