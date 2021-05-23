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
