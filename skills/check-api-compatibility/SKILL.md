---
name: check-api-compatibility
description: Check API compatibility and verify the version bump.
argument-hint: <spec-file>
---

## Instructions

You are performing a structured API backward-compatibility review based on the provided policy. Follow every step below in order.

### Step 1 — Read policy

Check whether `API_VERSIONING.md` exists in the project root. If it does, use it as the policy. Otherwise fall back to `resources/API_VERSIONING.md` bundled with this skill.
This is your authoritative definition of what constitutes a breaking vs. non-breaking change. Keep it in mind throughout.

### Step 2 — Find current specification

The spec path is provided in `$ARGUMENTS`. Trim any surrounding whitespace. If the argument is empty or missing, ask the user to supply the path and stop.

Confirm the file exists. Confirm the file is in the OpenAPI format. If it does not, tell the user and stop.

### Step 3 — Obtain previous version

**Previous version (committed):** run:

```bash
git show HEAD:"$ARGUMENTS"
```

If the command fails because the path has no committed version, tell the user "No previous committed version found for `<path>` — nothing to compare against." and stop.

**Current version:** read the file at `$ARGUMENTS` from disk.

### Step 4 — Compare specifications

Carefully compare the two spec versions yourself. Identify every difference: added, removed, renamed, or changed operations, parameters, request fields, response fields, headers, data types, and value constraints.

Do not count changes to `info.version` as a functional API change.

### Step 5 — Classify changes

Using the policy from Step 1, classify each difference as **breaking** or **non-breaking** and append a **Compatibility verdict** section:

```
## Compatibility verdict

### Breaking changes

<bulleted list, or "None.">

### Non-breaking changes

<bulleted list, or "None.">
```

If there are no differences at all (excluding version):

```
No changes detected.
```

Keep each bullet to one line: name the operation or field, describe what changed, and include the line number in the current spec where the change appears — e.g. `GET /books: added optional isbn query parameter (line 42)`. Be concise and human-readable.

### Step 6 — Check version

Extract `info.version` from both the old and new spec. Treat it as a `major.minor` string (e.g. `1.0`, `2.3`).

Determine the **required** bump using the versioning rules from the policy read in Step 1. Compute the **expected version** by applying that bump to the old version.

Compare the actual version change to the required one and append a **Version verdict** section:

```
## Version verdict

<verdict line>
```

Verdict lines:

1. No changes, version unchanged: `✓ No changes — version unchanged (<old>).`
2. Breaking changes, major bumped: `✓ Breaking changes — major version correctly updated (<old> → <new>).`
3. Non-breaking changes, minor bumped: `✓ Non-breaking changes — minor version correctly updated (<old> → <new>).`
4. No changes, incorrect version: `✗ No changes detected — expected <old> (unchanged), not <new>.`
5. Breaking present, incorrect version: `✗ Breaking changes detected — expected <expected>, not <new>.`
6. Non-breaking present, incorrect version: `✗ Non-breaking changes detected — expected <expected>, not <new>.`
