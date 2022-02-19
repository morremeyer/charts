# charts

This repository contains all charts that I use throughout my infrastructure that weren’t already built by someone else.

Pull requests are welcome, check [CONTRIBUTING.md](CONTRIBUTING.md) for detailed information.

## Usage

```sh
helm repo add morre https://morremeyer.github.io/charts/

# Install a cronjob with the cronjob chart. Fill the my-cron-values.yaml file before running this!
helm install cronjob morre/cronjob --values my-cron-values.yaml
```
