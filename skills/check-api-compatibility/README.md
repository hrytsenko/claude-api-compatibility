# Check API compatibility

This skill detects changes in the API specification, reports breaking and non-breaking changes, and verifies that the version bump is consistent with the detected changes.

## Usage

```
/api-versioning:check-api-compatibility <spec-file>
```

## Output

- **Breaking changes** — removals, renames, type changes, narrowed value spaces.
- **Non-breaking changes** — additions, optional parameters, extended value spaces.
- **Version verdict** — whether `info.version` is consistent with the detected changes.

## Policy

Compatibility and versioning rules are defined in `resources/API_VERSIONING.md`.

To override them for a specific project, place an `API_VERSIONING.md` file in the project root.
