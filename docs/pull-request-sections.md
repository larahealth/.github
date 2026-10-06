# Pull request section rules

Use this contract for human- and tool-authored pull request descriptions. The
[template](../pull_request_template.md) provides the starting structure. Keep exact
heading names and the order below; remove optional sections when they do not apply.
Keep detail proportional to the change. Documentation and small maintenance PRs
still retain the four required sections.

| Order | Heading | Include when | Content |
| --- | --- | --- | --- |
| 1 | `Key Takeaways` | Always | One to three concise bullets, most important first. Prefer one sentence per bullet; maximum three sentences per bullet. State the important outcomes or reviewer decisions. |
| 2 | `Summary` | Always | The problem, resulting behavior, scope, and issue link when appropriate. Explain meaningful design choices and concrete before/after behavior where useful. |
| 3 | `GraphQL Changes` | The actual GraphQL API schema changes | A focused before/after schema fragment or diff, compatibility impact, affected consumers, and required sequencing. |
| 4 | `UI Changes` | The user-visible interface changes | A concise explanation with useful screenshots or a short recording made with synthetic data. State a specific blocker if media cannot be provided. |
| 5 | `Test Cases` | Tests are added, updated, or removed | A collapsed scenario inventory grouped into Added, Updated, and Removed; omit empty groups and explain removed coverage. |
| 6 | `Privacy and Security` | Always | Concrete changes to data handling, authorization, tenant boundaries, or security. A brief statement is sufficient when there is no impact. |
| 7 | `Rollout and Rollback` | Always | Deployment order, flags or migrations when relevant, and an actionable reversal. A concise sentence can suffice for documentation or tooling. |
| 8 | `Dependencies and Blockers` | Prerequisites or material blockers exist | Required PRs, unresolved dependencies, and blockers affecting review or delivery. |

## GraphQL scope

Include `GraphQL Changes` for additions, removals, or changes to the API's schema
contract, such as fields, types, arguments, or nullability. Show only the relevant
schema changes rather than a full schema dump. Explain whether existing consumers
remain compatible and which consumers need updates.

Client query changes, generated client types, code-generation configuration, and
schema snapshot refreshes alone do not establish an API schema change. Formatting
changes alone do not qualify either. Describe those changes in `Summary`.
Resolver-only behavior changes also belong in `Summary` unless the schema contract
changes.

## UI evidence

Choose media that makes the changed behavior reviewable. Use before/after images
for visual differences and a short recording for interaction changes when useful.
Use synthetic data throughout. Exclude personal, clinical, confidential, or
operational information, private URLs, credentials, and secrets from images,
recordings, filenames, links, and prose. Review media before attaching it.

If media is unavailable, retain `UI Changes`, explain the visible behavior, and
state the concrete evidence blocker. Do not fabricate screenshots or recordings.

## Test inventory

Keep the `Test Cases` heading visible and collapse the inventory with this exact
summary label. Keep it collapsed by default; do not add the `open` attribute.
Include only populated groups:

```markdown
## Test Cases

<details>
<summary>See test cases</summary>

### Added

- Describe the new scenario and its expected behavior.

### Updated

- Describe the changed scenario and why its expectation changed.

### Removed

- Describe the removed scenario, why it was removed, and any replacement coverage.

</details>
```

Identify test files or suites when that helps reviewers locate the coverage.
Describe scenarios, not a list of test commands. If no tests changed, omit this
section; explain a material coverage gap in `Dependencies and Blockers` when one
affects review or delivery.

## Publishing checklist

- Use required headings in order and one to three Key Takeaways bullets.
- Remove irrelevant optional sections, empty test groups, placeholders, and all
  drafting comments. Every retained section must contain meaningful content.
- Keep Privacy and Security and Rollout and Rollback factual and proportional.
- Do not add `Validation` or `Verification` sections, test commands, pass/fail
  summaries, or copied CI logs. Automated evidence remains in GitHub checks.
- Link only issues, dependencies, and evidence appropriate for the repository's
  visibility. Never publish sensitive data or secrets.
- Read back the published description to confirm the headings, details block,
  links, and media render correctly and describe the final diff.

This contract guides authoring. It does not add a workflow, check, or gate and
does not modify existing pull request descriptions.
