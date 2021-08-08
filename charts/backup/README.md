# backup

Chart to back up PVCs with restic and regularly clean up the snapshots.

## Usage

If you want to regularly back up the contents of a PVC, use this minimal example for your values.yaml

```yaml
pvc: name-of-pvc
repo: s3:https://minio.example.com/name-of-pvc
backupJob:
  affinityLabels:
    app.kubernetes.io/instance: morre-paperless
    app.kubernetes.io/name: paperless
```

This will back up every day at 03:17. At 15:17, a cleanup will run and keep:

* 8 daily snapshots
* 5 weekly snapshots
* 13 monthly snapshots
* 2 yearly snapshots

For more advanced use cases, check the configuration section below or the values.yaml file.

## Configuration

The following table lists the configurable parameters of the chart and the default values.

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| backupJob.affinity | object | `{}` | to specify a full `spec.affinity` map for a pod. In most cases, `backupJob.affinityLabels` will be sufficient. |
| backupJob.affinityLabels | object | `{}` | labels of a pod that a strict affinity for scheduling will be set to. Needed for `ReadWriteOnce` PVCs. |
| backupJob.backup.args | list | `[]` | arguments for the backup. **Automatically generated, only set when necessary** |
| backupJob.backup.command | string | `nil` | command for the backup. Defaults to '/usr/bin/restic' by the upstream container. |
| backupJob.backup.image.pullPolicy | string | `"IfNotPresent"` |  |
| backupJob.backup.image.repository | string | `"restic/restic"` |  |
| backupJob.backup.image.tag | string | `"0.12.0"` |  |
| backupJob.backup.resources | object | `{}` | resources for the backup container |
| backupJob.concurrencyPolicy | string | `"Forbid"` | concurrencyPolicy for the backup Jobs |
| backupJob.init | object | `{"image":{"pullPolicy":"IfNotPresent","repository":"restic/restic","tag":"0.12.0"},"resources":{}}` | Configuration for the repository init container |
| backupJob.init.resources | object | `{}` | resources for the init container |
| backupJob.nodeSelector | object | `{}` |  |
| backupJob.restartPolicy | string | `"OnFailure"` | restartPolicy for the backup Jobs |
| backupJob.schedule | string | `"17 3 * * *"` | when to run backups |
| backupJob.securityContext | object | `{}` |  |
| backupJob.tolerations | list | `[]` |  |
| cleanupJob.affinity | object | `{}` |  |
| cleanupJob.args | list | `[]` | arguments for the cleanup. **Automatically generated, only set when necessary** |
| cleanupJob.command | string | `nil` | command for the cleanup. Defaults to '/usr/bin/restic' by the upstream container. |
| cleanupJob.concurrencyPolicy | string | `"Forbid"` | concurrencyPolicy for the cleanup Jobs |
| cleanupJob.enabled | bool | `true` | If backups shall be cleaned up after some time |
| cleanupJob.image.pullPolicy | string | `"IfNotPresent"` |  |
| cleanupJob.image.repository | string | `"restic/restic"` |  |
| cleanupJob.image.tag | string | `"0.12.0"` |  |
| cleanupJob.keepDaily | int | `8` | number of daily snapshots to keep |
| cleanupJob.keepMonthly | int | `13` | number of monthly snapshots to keep |
| cleanupJob.keepWeekly | int | `5` | number of weekly snapshots to keep |
| cleanupJob.keepYearly | int | `2` | number of yearly snapshots to keep |
| cleanupJob.nodeSelector | object | `{}` |  |
| cleanupJob.resources | object | `{}` | resources for the cleanup container |
| cleanupJob.restartPolicy | string | `"OnFailure"` | restartPolicy for the cleanup Jobs |
| cleanupJob.schedule | string | `"17 15 * * *"` | when to run the cleanup |
| cleanupJob.securityContext | object | `{}` |  |
| cleanupJob.tolerations | list | `[]` |  |
| fullnameOverride | string | `""` |  |
| imagePullSecrets | list | `[]` |  |
| nameOverride | string | `""` |  |
| pvc | string | `nil` |  |
| repo | string | `nil` | The repository location |
| secretName | string | `"backup-secret"` | The secret that all containers load their environment from. See https://restic.readthedocs.io/en/latest/040_backup.html#environment-variables for variables. |

