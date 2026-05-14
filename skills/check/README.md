# check

A skill that checks an OpenAPI specification against its previously committed version and reports breaking and non-breaking changes, then verifies the version bump is consistent with those changes.

## Usage

```
/api-compatibility:check <spec-file>
```

Example:

```
/api-compatibility:check books.v1.yaml
```

## Output

- **Breaking changes** — changes that require a major version bump per the policy.
- **Non-breaking changes** — changes that require a minor version bump per the policy.
- **Version verdict** — whether the `info.version` in the spec was updated correctly.

## Customizing the policy

The skill ships with a default policy at `resources/API_VERSIONING.md`.

To override it for a specific project, place an `API_VERSIONING.md` file in the project root. The skill will use that file instead of the bundled default, leaving the skill itself untouched.
