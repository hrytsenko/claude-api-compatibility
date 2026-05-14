# claude-api-compatibility

A Claude Code plugin that checks OpenAPI specification backward compatibility and verifies the version bump.

## Installation

```
/plugin install https://github.com/hrytsenko/claude-api-compatibility
```

## Usage

```
/api-compatibility:check <spec-file>
```

Compares the current spec file against its previously committed version and reports:

- **Breaking changes** — removals, renames, type changes, narrowed value spaces.
- **Non-breaking changes** — additions, optional parameters, extended value spaces.
- **Version verdict** — whether `info.version` was bumped correctly per the changes detected.

## Compatibility policy

The plugin ships with a default policy at `skills/check/resources/API_VERSIONING.md`.

To override it for a specific project, place an `API_VERSIONING.md` file in the project root. The skill will use that file instead of the bundled default.

## License

MIT
