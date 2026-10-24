<!--
SPDX-FileCopyrightText: 2026 [ernolf] Raphael Gradenwitz <raphael.gradenwitz@googlemail.com>
SPDX-License-Identifier: MIT
-->

<!-- Project header -->
<p>
  <h3>ncmake-workflows</h3>
  <p>GitHub Actions workflow templates for Nextcloud apps</p>
  <p>
    <a href="https://api.reuse.software/info/github.com/ernolf/ncmake-workflows"><img alt="REUSE status" src="https://api.reuse.software/badge/github.com/ernolf/ncmake-workflows"></a>
    <a href="https://github.com/ernolf/ncmake"><img alt="built with ncmake" src="https://cdn.jsdelivr.net/gh/ernolf/ncmake@main/img/ncmake-badge.svg"></a>
  </p>
</p>
<hr>
<br clear="left">

The workflow templates of [ncmake](https://github.com/ernolf/ncmake). `make workflows-install` copies a template into `.github/workflows` of an app and records it, and the workflow updater keeps it current there. Dependabot keeps the actions of the templates current in this repository.

Each template is `workflows/<name>.yml`, with its name and description in `workflows/<name>.properties.json` next to it.

> [!TIP]
> **📖 The documentation lives in the [ncmake wiki](https://github.com/ernolf/ncmake/wiki/Workflows).** This page is the short version.

## Workflows

| Template | Name | Description |
| --- | --- | --- |
| [`backport`](workflows/backport.yml) | ncmake backport | Apply a pull request's change to a maintenance branch on a "/backport to" comment and open a verified, signed-off pull request there; on an open pull request it runs at the merge |
| [`branch-cleanup`](workflows/branch-cleanup.yml) | ncmake branch cleanup | Delete a merged pull request's head branch if it still exists (a portable, workflow-shipped equivalent of the repository "Automatically delete head branches" setting) |
| [`lint-actions`](workflows/lint-actions.yml) | Lint actions | Run actionlint over every tracked GitHub Actions workflow: .github/workflows/, an app's .ncmake/workflows/ folder and templates next to a properties.json, with the repository's own configuration when it has one; a repository without workflows passes |
| [`lint-containerfiles`](workflows/lint-containerfiles.yml) | Lint Containerfiles | Run hadolint, with shellcheck on every RUN, over every tracked Containerfile and Dockerfile, with the repository's own .hadolint.yaml when it has one; a repository without Containerfiles passes |
| [`lint-markdown`](workflows/lint-markdown.yml) | Lint Markdown | Run markdownlint-cli2 over every tracked Markdown file, with the repository's own configuration or the default rules minus those GitHub Markdown breaks on purpose; a repository without Markdown files passes |
| [`lint-php-syntax`](workflows/lint-php-syntax.yml) | Lint php syntax | Run php -l over every tracked PHP file, without composer or appinfo/info.xml; the version matrix comes from the PHP_VERSIONS variable, a .php-version file or the template default |
| [`lint-shell`](workflows/lint-shell.yml) | Lint shell | Run shellcheck over every tracked shell script, found by extension or by shebang (covers extensionless commands); a repository without shell scripts passes |
| [`lint-vue-imports`](workflows/lint-vue-imports.yml) | Lint Vue imports | Fail when a tracked source file imports the @nextcloud/vue root instead of a per-component entry point, which pulls the whole library into the module graph before tree shaking; a repository without a hit passes |
| [`lint-web`](workflows/lint-web.yml) | Lint web | Run ESLint, Stylelint and html-validate over the tracked JavaScript, CSS and HTML of a repository without a Node project, with the repository's own configuration or each tool's recommended set; a repository with a package.json or without such files passes |
| [`lint-yaml`](workflows/lint-yaml.yml) | Lint YAML | Run yamllint over every tracked YAML file, with the repository's own configuration or the default set adjusted for GitHub workflows; a repository without YAML files passes |
| [`release`](workflows/release.yml) | ncmake release tarball | Build the release tarball with ncmake (make build && make dist) and attach it to the published GitHub release |
| [`workflow-updater`](workflows/workflow-updater.yml) | ncmake workflow update | Refresh the ncmake-managed CI workflows from their upstream templates on a schedule and open a pull request when anything changed (replaces Dependabot for .github/workflows/) |

## License

[MIT](LICENSE)
