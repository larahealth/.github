# .github

Shared, public-safe GitHub defaults for Lara Health repositories.

The root [pull request template](pull_request_template.md) and
[section rules](docs/pull-request-sections.md) define the canonical description
structure. Human authors and authoring tools should use both files from the same
revision and remove drafting comments and irrelevant optional sections before
publishing a description.

GitHub offers this template to organization repositories that have no local
template override. Tool-created descriptions should load the canonical files
explicitly because supplying a PR body can bypass the template. See
[GitHub's default community health file documentation](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file).

Changes take effect through the default branch. They do not rewrite existing PR
descriptions. This repository adds no GitHub Actions enforcement.
