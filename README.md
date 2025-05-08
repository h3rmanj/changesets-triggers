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
