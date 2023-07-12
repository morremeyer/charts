# charts

:warning: This repository is deprecated and will not be updated. Please migrate to https://github.com/community-tooling/charts.

Every chart available in this repository is available on community-tooling/charts in the latest version from this repository, too.

## To migrate

1. Update to the latest version available in morremeyer/charts
2. Change repository references from morremeyer/charts to community-tooling/charts

## Why?

This repository is under my ([morremeyer](https://github.com/morremeyer)) control. Although I can add collaborators, if I ever decide that I don't want to maintain it anymore, or I am unavailable for longer periods of time, it would be hard to impossible to administer the repo without me.

For that reason, I have decided to move it to a dedicated organization, https://github.com/community-tooling. This organization also hosts some OCI images that are commonly used in my (and other people's) infrastructure.

The organization enables me to give others full control, too.

As with almost every breaking change, the earlier you make it, the easier it will be to migrate. Therefore, we're doing this now instead of when the need is really there.

<details>
<summary>Old README</summary>
This repository contains all charts that I use throughout my infrastructure that weren’t already built by someone else.

Pull requests are welcome, check [CONTRIBUTING.md](CONTRIBUTING.md) for detailed information.

## Usage

```sh
helm repo add morre https://morremeyer.github.io/charts/

# Install a cronjob with the cronjob chart. Fill the my-cron-values.yaml file before running this!
helm install cronjob morre/cronjob --values my-cron-values.yaml
```

## Maintainers

The people listed here maintain this repository. At least one of them will automatically get requested as a reviewer for PRs. On issues, feel free to mention us.

| Avatar                                                                        | Name               |
| ----------------------------------------------------------------------------- | ------------------ |
| ![Avatar of morremeyer](https://avatars.githubusercontent.com/u/7683567?s=80) | Morre (morremeyer) |
| ![Avatar of ekeih](https://avatars.githubusercontent.com/u/3430656?s=80)      | Max Rosin (ekeih)  |

</details>
