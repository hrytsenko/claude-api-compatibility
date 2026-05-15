# Bump API version

This skill automatically bumps `info.version` according to detected changes.

The skill uses the `major.minor` format for `info.version`. It relies on `/api-versioning:check-api-compatibility` to detect changes, so the same policy applies.

## Usage

```
/api-versioning:bump-api-version <spec-file>
```

## Policy

Versioning rules are defined in `resources/API_VERSIONING.md`.

To override them for a specific project, place an `API_VERSIONING.md` file in the project root.
