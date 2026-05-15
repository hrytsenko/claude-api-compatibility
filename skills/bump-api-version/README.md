# api-versioning:bump-api-version

This skill automatically bumps `info.version` according to detected changes.

The skill uses the `major.minor` format for `info.version`.

## Usage

```
/api-versioning:bump-api-version <spec-file>
```

## Policy

Versioning rules are defined in `resources/API_VERSIONING.md`.

To override them for a specific project, place an `API_VERSIONING.md` file in the project root.

## Dependencies

Uses `/api-versioning:check-api-compatibility` internally to classify changes, so the same policy applies.
