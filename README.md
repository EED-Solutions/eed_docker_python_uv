# eed_package_template

## Description

 - created from this template: <https://github.com/EED-Solutions/eed_package_template/tree/f94454015a1b237a0699bf26f8edcdb3c861cc95>
   ```

## Github actions

Workflows are centrally hosted in EED_Solutions/eed_gha_workflows.
Please check for more details here.

### Docker Publish Workflow Triggering

The Docker publish workflow (`publish_docker.yml`) is triggered automatically in the following cases:

- **On any push to the `main` branch.**
- **On any tag pushed to the repository that matches semantic versioning (`v*.*.*`).**
- **When a pull request is opened, synchronized, or reopened and the source branch is named `dev` or `release`.**
  - Note: The workflow runs for all PRs, but will immediately exit unless the source branch is `dev` or `release`.

This ensures Docker images are only built and published for main releases, version tags, and changes coming from the main development branches.

## Other

Test EED85-machine
