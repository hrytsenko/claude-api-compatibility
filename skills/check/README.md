# api-compatibility:check

A skill that checks an OpenAPI specification against its previously committed version, reports breaking and non-breaking changes, and verifies that the version bump is consistent with the detected changes.

## Usage

```
/api-compatibility:check spec.yaml
```

## Output

- **Breaking changes** — changes that require a major version bump according to the policy.
- **Non-breaking changes** — changes that a minor version bump according to the policy.
- **Version verdict** — whether the info.version value in the specification was updated consistently with the detected changes.

## Policy

The skill ships with a default policy at `resources/API_VERSIONING.md`.

To override it for a specific project, place an `API_VERSIONING.md` file in the project root. The skill will use that file instead of the bundled default, leaving the skill itself unchanged.
