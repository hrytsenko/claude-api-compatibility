# Check API compatibility

This skill detects changes in the API specification, reports breaking and non-breaking changes, and verifies that the version bump is consistent with the detected changes.

## Usage

```
/api-versioning:check-api-compatibility <mode> <spec-file>
```

## Modes

- **`head <spec>`** — previous version from the repository, current version from disk. Use this before committing changes.
- **`log <spec>`** — both versions from the repository. Use this to verify a committed version bump.
- **`diff <old-spec> <new-spec>`** — both versions from disk. Use this to compare two local files directly.

## Output

- **Compatibility verdict** — breaking and non-breaking changes between the two versions.
- **Version verdict** — whether `info.version` is consistent with the detected changes.

## Policy

Compatibility and versioning rules are defined in `resources/API_VERSIONING.md`.

To override them for a specific project, place an `API_VERSIONING.md` file in the project root.
