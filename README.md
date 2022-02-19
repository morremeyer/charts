# charts

This repository contains all charts that I use throughout my infrastructure that weren’t already built by someone else.

**Pull requests are welcome.**

## Usage

```sh
helm repo add morre https://morremeyer.github.io/charts/
```

## Development

Before you commit, please run pre-commit. This will also generate the documentation for the helm charts.

To set up pre-commit to run automatically on commit, run (example for Ubuntu)

```sh
pip3 install pre-commit

pre-commit install
```

### Commit messages

This repository uses [Conventional Commit messages](https://www.conventionalcommits.org/en/v1.0.0/). Please ensure all your commit messages follow this syntax to enable people to quickly check what a commit does.

Valid commit types are defined in [commitizen/conventional-commit-types](https://github.com/commitizen/conventional-commit-types/blob/v3.0.0/index.json).

### Versioning

Helm charts use semantic versioning. For the charts in this repository, only `[MAJOR].[MINOR].[PATCH]` syntax is used, without any pre-releases.

Please bump as follows:

* Major version for breaking changes (this includes updates of default values as users may need to manually update their values)
* Minor version when you add features
* Patch version for bug fixes and documentation updates
