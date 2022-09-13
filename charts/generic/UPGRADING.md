# Upgrading

## 3.8.0 to 4.0.0

### Kubernetes Version

If you set `ingress.enabled: true`, this chart is only compatible with Kubernetes 1.21 and newer.

### Service Ports

The port configuration for the `service` key has been deprecated with `3.6.0` and is now removed.

**If you did not change the default configuration, you do not need to do anything**

Migration example:

_Old_:

```yaml
service:
  targetPort: http
  protocol: TCP
  name: http
  port: 80
```

_New_:

```yaml
service:
  ports:
    - targetPort: http
      protocol: TCP
      name: http
      port: 80
```

### To 3.0.0

Support for CronJobs has been removed. If you used the `isCronjob: true` flag, please migrate to `morremeyer/cronjob` in version `2.0.0 <= x < 3.0.0`.

:warning: If you need open ports on your CronJob pod, this is not supported in the cronjob chart. This is a design decision as CronJobs should not have any incoming traffic.

The cronjob chart is almost fully compatible with all existing configuration you have (except for `ports`), you just have to do one migration step:

1. Remove the `isCronjob: true` value

### To 2.0.0

The format for configuration environment variables has changed and is now less verbose.

Old:

```yaml
env:
  - name: ENV_NAME
    value: test
```

New:

```yaml
env:
  ENV_NAME: test
```

If you have environment variables set from ConfigMaps or Secrets, check out `envValueFrom`, which was [added in 1.1.0](https://github.com/morremeyer/charts/commit/a2b767f91b8f921bbd81abcb37648a6724ebb1db).
