# Upgrading

## 2.1.1 to 3.0.0

With 3.0.0, we dropped support for Kubernetes versions < 1.21.0.

To use the chart, you will need to upgrade to at least 1.21.0.

### To 2.0.0

Support for the following has been removed:

- `livenessProbe`
- `readinessProbe`
- `ports`

This is a design decision as CronJobs should not have any incoming traffic.

The following default values have been changed:

- `command` from `["/bin/echo"]` to `[]`
- `args` from `["'{"level": "info", "message": "no arguments defined, nothing to do"}'"]` to `[]`
