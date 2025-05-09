# Changeset Permission & Workflows

This repo is testing the correct usage of `permissions` in a restrictive repository, and using a custom token for publishing and triggering actions.

At first, I'll create the base setup. This should fail because of missing permissions in the workflow.

The permissions needed is:

```yaml
permissions:
  contents: write
  pull-requests: write
```

And also check the `Allow GitHub Actions to create and approve pull requests` in Actions settings.

I'll then release v1.0.0, but this won't trigger the tag triggered workflow.

For v2.0.0, I'll use a PAT, with `commitMode: github-api`, which then will trigger the tag workflow.

## Token variations

For the next section, I'll test variations of token inputs given to the workflow. Each new version will match with a variation.

- `v3.0.0`: Built-in token
- `v4.0.0`: PAT
- `v5.0.0`: PAT + `github-api`
- `v6.0.0`: PAT + `actions/checkout` PAT

| Variation                    | `push.branches` | `push.tags` | `pull_request.created` | `pull_requests.synchronized` | `release.published` |
| :--------------------------- | :-------------: | :---------: | :--------------------: | :--------------------------: | :-----------------: |
| Built-in token               |                 |             |                        |                              |                     |
| PAT                          |                 |             |                        |                              |                     |
| PAT + `github-api`           |                 |             |                        |                              |                     |
| PAT + `actions/checkout` PAT |                 |             |                        |                              |                     |
