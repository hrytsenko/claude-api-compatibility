# api-versioning:bump-api-version

This skill automatically bumps `info.version` according to detected changes.

The skill uses the `major.minor` format for `info.version`.

## Usage

```
/api-versioning:bump-api-version <spec-file>
```

## Behavior

| Changes detected  | Action                                                    |
|-------------------|-----------------------------------------------------------|
| Any breaking      | Increment major and reset minor to 0, e.g. `1.2` → `2.0`. |
| Non-breaking only | Increment minor, e.g. `1.2` → `1.3`.                      |
| None              | Do nothing.                                               |

## Dependencies

Uses `/api-versioning:check-api-compatibility` internally to classify changes, so the same policy applies.
