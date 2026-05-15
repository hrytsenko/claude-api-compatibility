---
name: bump-api-version
description: Bump the API specification version according to detected API changes.
argument-hint: <spec-file>
---

## Instructions

You are performing an automated API version bump. Follow every step below in order.

### Step 1 — Detect changes

Run `/api-versioning:check-api-compatibility $ARGUMENTS` and capture the result.

### Step 2 — Choose bump

Based on the check result, apply the versioning rules from the API versioning policy.

### Step 3 — Apply bump

Extract `info.version` from the current spec file at `$ARGUMENTS`. Treat it as a `major.minor` string (e.g. `1.0`, `2.3`).

Compute the new version according to Step 2, then update the `info.version` field in the file on disk.

### Step 4 — Report bump

Print a short summary:

- Major bump: `Breaking changes detected — major version bumped (<old> → <new>).`
- Minor bump: `Non-breaking changes detected — minor version bumped (<old> → <new>).`
- No changes: `No changes detected — version unchanged (<version>).`
